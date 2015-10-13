# Sosuu
素数の列挙
public class PrimeNumber {
	public static void main(String[] args) {
		final int range=1000; // 検査対象の最大数
		int counter = 0; // 乗除算回数を係数するためのカウンタ
		int ptr = 0; // 素数の個数
		int[] prime = new int[500]; // 素数を格納する配列
		
		prime[ptr++] = 2; // 素数２を配列に格納
		prime[ptr++] = 3; // 素数３を配列に格納
		
		for (int n=5;n<=range;n+=2) {
			// 素数５から走査，対象は奇数のみ，1000まで
			boolean flag = false; // 素数か否かの判定フラグ
			for (int i=1;prime[i]*prime[i]<=n;i++) {
				// nの平方根以下のいずれの素数でも割り切れないかを検査
				counter += 2; // for文の乗算とif文の除算をカウント
				if (n%prime[i] == 0) { // 割り切れると素数ではない
					flag = true;
					break; // 繰返しの中断
				}
			}
			if (!flag) { // 最後まで割り切れなかったら素数
				prime[ptr++] = n; // 素数を配列に登録
				counter++; // for文の条件がクリアできなかった時の判定分
			}
		}
		
		for (int i = 0; i < ptr; i++) // 素数表示
			System.out.println(prime[i]);
			
		System.out.println("乗除算回数：" + counter);
	}
}
