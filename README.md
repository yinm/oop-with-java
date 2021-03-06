[なぜ，あなたはJavaでオブジェクト指向開発ができないのか：書籍案内｜技術評論社](http://gihyo.jp/book/2005/4-7741-2222-X)をやってます。

---

# memo

## Lesson1
- プログラミングの手順は3つのステップ
  1. コンピュータに行わせたいことを理解する
  2. 理解したことを説明できるレベルまで整理する
  3. コンピュータがわかる言葉に翻訳する
- オブジェクト指向は、ソフトウェアを効率的かつ楽に開発するために生まれた技術

## Lesson2
- 非オブジェクト指向で開発した場合の問題点
  - 簡単な仕様変更でも、複数箇所のプログラム修正が必要になる

## Lesson3
- オブジェクト指向は、人間の理解をできるだけそのままコンピュータへ伝えるための方法
  - 2.理解したことを説明できるレベルまで整理する に対応する
- 役割分担を明確にすることがオブジェクト指向の考え方の第一歩
  - 役割を、クラスと呼ぶ
  - 実際の登場人物(実体)を、インスタンスと呼ぶ  
    - クラスの種類に関係なくインスタンス全般を、オブジェクト(実体が存在するもの)と呼ぶ (これがオブジェクト指向の由来)
- それぞれの登場人物は、互いの動作をきっかけに自分の役割を果たす
  - きっかけを、メッセージと呼ぶ
  - オブジェクト同士がメッセージをやりとりすることを、メッセージパッシングと呼ぶ 
  - 手続き型のフローチャートに比べて、より現実世界の考え方が近い形にできる
- 操作 (メソッド)
  - メッセージをきっかけとした、オブジェクトの振る舞いのこと 
- オブジェクトの状態を管理するための方法
  - 属性(フィールド): オブジェクト固有の状態
    - 同じインスタンスでも、全てが同じではない場合がある(e.g. 名前、じゃんけんに勝った回数)
    - 自分に関する情報は自分で管理させる
  - カプセル化
    - オブジェクトの内部の状態を隠し、他のオブジェクトからは直接知ることができないようにすること
- メソッド名は、「そのオブジェクトに対してどのような操作をするか」という観点で名前をつける
  - cf getter/setter 
  
## Lesson4
- ソースコードのコピーによる拡張の問題点
  1. 共通部分の機能追加やバグ修正の際に、複数箇所の同じ変更が必要になる
  2. クラスの拡張をコピーで行ってしまうと、本来関係のない箇所の修正が必要になる (e.g. 呼び出し元の引数の型が合わなくなる)
- 継承
  - スーパークラスの性質(属性・操作)を受け継ぐ
  - サブクラスは、スーパークラスに対する追加や変更部分のみ記述(オーバーライド)すればいい点が、クラスをコピーするのと異なる
    - 1.共通部分の機能追加やバグ修正の際に、複数箇所の同じ変更が必要になる を解決する
  - 継承した時点で、サブクラスはスーパークラスの一種であると表現できる
    - 2.クラスの拡張をコピーで行ってしまうと、本来関係のない箇所の修正が必要になる (e.g. 呼び出し元の引数の型が合わなくなる) を解決する
- 継承の階層
  - 深すぎる(5階層以上)になると、保守性が下がる
    - e.g. どこで定義されているメソッドかわかりづらくなる
- 多重継承
  - 複数のスーパークラスを継承したサブクラスを作ることができる
  - クラス関係が複雑になりすぎてわかりづらいという考えが現在の主流のため、Javaなどの言語では禁止されている
    - 代わりにインターフェースを使って表現する
- 継承のコンストラクタ 
  - Javaの言語仕様では、スーパークラスでコンストラクタを作成していた場合は、サブクラスでも作成しなければならない
- superの使い方 (2種類)
  - サブクラス上でオーバーライドした場合でも、スーパークラスのメソッドを使うことを表現する場合に使う (e.g. `super.showHand()`)
  - スーパークラスのコンストラクタを呼び出す (e.g. `super()`)
- this
  - 自分自身のオブジェクトを表すことができる
  - 省略しても問題ないが、継承関係が深く、メソッドをオーバーライドしている場合に明示的につけておくことで混乱を防げる
  
## Lesson5
- インタフェース(interface)
  - 「オブジェエクトへの操作方法とそれに対応する振る舞いの組み合わせ」を規定したもの
- 委譲
  - 実質的な処理を他のクラスにお願いしてしまうこと
    - 利用する側にとっては、呼び出すクラスもメソッドも同じで良い
    - 実際の処理が呼び出す側からは隠蔽されているので、処理の切り替えを簡単に行える
- インターフェースクラスの利用
  - 型の指定は、インターフェースクラス型として扱う (実装クラスではない)
  - 汎用性を高めるため？
  
## Lesson6
- モデリング
  - 物事の本質をできるだけシンプルに表現すること 
    - 統一して説明できる理論(モデル)として表現できることで、拡張や変更が容易にできる
  - 2.理解したことを説明できるレベルまで整理する を行うこと
  - モデリングに正解はなく、多くのことを統一して説明できるモデルを作るのは難しいので、関心を向けている一面が適切にモデリングできればいい
- モデリングの手順
  1. 仕様を決める
  2. クラスを抽出する
  3. オブジェクト間のメッセージを考える
  4. 各クラスの操作を洗い出す
  5. 各クラスの属性を洗い出す
- 仕様の決め方
  - ユースケースを使う  
    - システムがどうあるべきかを考える (どのように作るかを考えるだけではいけない)
- クラスを抽出する
  - 名詞抽出法 
    - 仕様に出てくる名詞を抽出してクラスの候補にし、その中から明確な役割が存在するものをクラスにする
    - 主語や目的語になるものは役割になりやすい
- クラス間の関連を洗い出す
  - 関連
    - クラスの間に何らかの意味上の繋がりがあること
    - 関連があるということは、それらのクラス間でメッセージをやりとりする可能性がある
  - クラス間の関連を図に描き出す
- 各クラスの属性を洗い出す
  - 操作に関連して必要になる属性を挙げていく
    - 他のクラスからの操作によって影響を受けるオブジェクト固有の状態
    - 他のクラスから必要とされるオブジェクト固有の情報
  - ただし、外部に影響しない属性は不要
- シーケンス図 
  - プログラムの流れ(操作の呼び出し関係の順番)を理解するために使える図
  
## Lesson7
- 継承関係を見極める
  - is-a関係になっていないものは継承してはいけない
    - ◯ 七並べの手札は、手札である 
    - ◯ ばば抜きの手札は、手札である
    - X 七並べの手札は、ばば抜きの手札である
  - 似ているが違いのあるクラスは、汎化を使って継承する
- 汎化 (generalization)
  - 複数のクラスの共通部分のみを切り出したクラスを作成して、それを継承すること
    - e.g. クラスAとBの共通部分をクラスCとして作成し、クラスAとBはクラスCのサブクラスとして作り直す
- フレームワーク
  - 似た問題を一段抽象化してあらかじめモデリングしておき、それを元に様々なソフトウェアで利用できるようにしたもの 
  
## Lesson8
- フレームワークを作る
  - 共通する要素を抽出する
    - 具体的な事柄を一段階抽象化して、共通する要素を上げてみる (e.g. トランプゲームのフレームワークなら、ばば抜き・七並べの共通要素)
  - インターフェースを使って、フレームワークの境界を明確にする
    - フレームワークが提供する範囲と、利用者が作らなければならない機能を分ける
- フレームワーク化するメリットとして、問題領域のモデリングそのものも再利用できる (再利用できるのは、プログラムだけではない)
- インターフェースと抽象クラスの違い
  - インターフェース: すべてのメソッドが抽象メソッドでなければならない
  - 抽象クラス: 抽象メソッドでないメソッドが存在してもいい
  
## Lesson9
- 

