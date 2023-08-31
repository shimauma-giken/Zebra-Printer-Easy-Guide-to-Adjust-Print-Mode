---
marp: true
paginate: true
header:   Zebra Technologies Tech Seminar Oct 2023 
footer: Visit www.zebra.com for details!
style: |
    @import 'default';
    @import url('https://fonts.googleapis.com/css?family=Noto Sans JP&display=swap');

    section{
        font-family: 'Noto Sans JP', serif;
        background-color: white;
        justify-content: start;
        font-size: 150%
    }

    section.main-title *, h3, h4{
        justify-content: center;
        text-align: center;
    }

    section.main-distitle *, h3, h4{
        justify-content: start;
        text-align: left;
    }


    section.sub-title {
        justify-content: center;
        text-align: center;
    }

    section.author {
        text-align: right;
        justify-content: end;
    }

    section.smallfontsize{
        font-size: 100%
    }

        section.defaultfontsize{
        font-size: 100%
    }


---
<!-- 全体設定ですよ -->
<!-- これはコメント -->





<!-- 
参考リンク：

https://qiita.com/e99h2121/items/79db6b7375ccbf3d3977#marp-%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%82%B7%E3%83%B3%E3%82%BF%E3%83%83%E3%82%AF%E3%82%B9

[marpで使える 画像の記法をマスターしよう](https://zenn.dev/cota_hu/books/marp-beginner-advanced/viewer/create-2)

[Marpでスライドを左右に分割する方法](https://qiita.com/ShibuKazu/items/8c35f8b6ebe24af03cdc)

[marp nextで中央寄せをする](https://qiita.com/isobe_mochi/items/4c60f54bba8133e4a8ab)

-->



</br>

<!-- _class: main-title -->
### なぜRFIDプリンタにカッターが利用できないという迷信が広まるのか
#### ～ 実機で用紙オプションの基本をしっかり理解する ～

</br>
</br>
</br>

<!-- _class: author -->
Zebra Technologies Japan
Senior Sales Engineer
Yu Sasaki / 佐々木有
22 Sep 2023
[www.zebra.com](https://www.zebra.com)




---

## 用紙オプションに苦手意識を持っている人は意外に多い
</br>

- 見たことない
- 触ったことがない
- 調べ方がわからない
- オプション組み合わせがわからない
</br>

→ 実はお客様視点でも同じ。だから、しっかり理解する必要がある。

<!-- 
お客様視点でも同じなので、意外と質問が多い。
プロフェッショナルとして恥をかかないよう、正確な受け答えができるようにしておくことが肝要。
結論：顧客サポートにおいては非常に重要。（特にRFIDオプション利用時）
-->

--- 


## 用紙オプションとはなにか？

用紙に対して、特定の操作を加えるもの  

</br>

1. カッター
1. 剥離
1. フルリワインダー
1. ハーフリワインダー
1. RFIDオプション
   </br>


        ハーフとフルリワインダーは間違えないようにしよう



---


## 利用可能なオプションは機種によって異なる

</br>
</br>

| 機種 | カッター | 剥離 | ハーフR | フルR | RFID | 
|-|:-:|:-:|:-:|:-:|:-:|
| モバイル         | × | △ | × | × | △ | 
| デスクトップ     | 〇 | 〇 | × | × | △ | 
| テーブルトップ    | 〇 | 〇 | 〇 | 〇 | 〇 | 
| リストバンド      | × | × | × | × | × | 

</br>


△ --- 一部モデルのみ対応



---


## キッティングの手順
</br>

1. 用紙オプションの取付
   
        同梱のマニュアルに沿って、オプションを取り付ける。

    </br>

2. 用紙のセッティング
   
        用紙スペック、用紙オプションに従い適切な設定を行う。

</br>

わからない場合はzebra.com > 製品サポートページの動画を見よう。



---


<!-- _class: sub-title -->


# 用紙オプションを理解しよう

---
<!-- _class: sub-distitle -->

## カッターとキャッチトレイ
    用紙をカットする

#### ハード構成  
1. カッター
2. キャッチトレイ (ZT Only)

#### 用紙設定
- Cutter 
- Delay Cut

![bg right:40% 80%](./picture/ZT411-Cutter-01.png)

---

## Cutter とDelay Cut モードの違い

カットするタイミングやカット方法によって使い分ける

#### Cutter モード
    - バッチ（^XA^XZ)終了時のタイミングで自動カットしたい方向け。
    - 3枚印刷→カットのように特定のパターンでカットする場合に多用される。
    - ^XB発行のバッチはカットを抑制できる。

#### Delay Cut モード
    - 任意のタイミングでカットしたい方向け。
    - カットタイミングがランダムに発生する現場で用いられることが多い。
    - カットコマンド*実行タイミングでカットされる。
        * ZPL: ~JK / SGD: media.cut_now


---
## 剥離と台紙巻き取り
    - 台紙とラベルを分離する
    - 処理済み台紙を巻き取る
  
#### ハード構成  
1. ピーラー
2. ハーフリワインダー(ZT Only)

![bg right:40% 80%](./picture/ZT411-Peel_half-rewind-01.png)

#### 用紙設定
- Rewind 

---
## 用紙巻き取り
    - 印刷済みラベルを巻き取る
  
#### ハード構成  
1. フルリワインダー(ZT Only)

★ フィールドインストール不可。
![bg right:40% 80%](./picture/ZT411-Full-Rewind-01.png)

#### 用紙設定
- Rewind 


---

## よくある勘違いとミス

1. RFID + Cutter は非サポート
    
        サポート可。適切な対応をすることで利用できることが多い。
        調整・設定者はプリンタ・RFラベルへの知見が必須。
2. フルリワインダーは後付けできる
   
        後付けできない。ハーフRとフルRの違いがわからないための発注ミスや
        後付けできると顧客に説明し、後々のトラブルとなることが多い。
3. Silverlineでピーラーが利用できる
   
        利用不可。Silverlineラベルはその物理的特性により、カッター・ピーラー・フルリワインダーなどの
        用紙オプションの利用は非サポート。

---
### オプション利用時は用紙要件が異なる

![bg right 80%](./picture/Tech-Specs-ZT411-media.png)

</br>

機種・用紙オプションの種類によって、利用できる用紙スペックが異なる。詳細はTech Specsを参照すること。

- Media Width
- Minimum Label Length
  
  </br>

    カッター利用時は特に長いラベル長が求められることを理解しよう。



---

## 付録：印刷モードのアルゴリズム

</br>

|||
|-|-|
| Tear-off  | [F0] > Print > [Tear Bar] > Tear ... > **[F0]**
| Peel-Off  | [F0] > Print > [Peel Position] > Peel .. > **[F0]**.
| Cutter    | [F0] > Print > [Cut Position] > Cut ... > **[F0]**
| RFID + Tear-off   | [F0] > **[Encode Position]** > RF Encode > [F0] > Print > [Tear Bar] > Tear... > **[F0]**
| RFID + Cutter     | [F0] > **[Encode Position]** > RF Encode > [F0] > Print > [Cut Position] > Cut ... > **[F0]** 

---

<!-- _class: sub-title -->


# Let's Play

---

## 知っておくべき重要な設定値

- ラベル停止位置

        カット、剥離、切り取り位置の微調整。
- RFID エンコードポジション

        RFIDタグのエンコード位置。ラベルピッチ 25mm 以下は特に重要。

</br>

特に用紙オプション+ RFID利用時はバックフィード量のコントロールが鍵

---

## 実習1 (基本)

1. 用紙オプションのモードを設定しよう。
   
        「用紙オプションモードの変更」をみながら、適切なモードに設定してみよう。

2. 印刷後のラベル停止位置を調整してみよう。
   
        「ラベル停止位置の調整」をみながら、ラベル停止位置を調整してみよう。

---
## 用紙オプションモードの変更
カット、剥離、切取り時の停止位置を設定。
</br>

|||
|-|-|
| 有効値| Tear Off, Peel Off, Rewind, Cutter, Delayed Cut, Linerless Peel, Linerless Rewind, Linerless Tear, Applicator, Linerless Cut, Linerless Delayed Cut
| ZPL コマンド| ^MM
| SGD コマンド| media.printmode
| フロントパネル | [印刷] > [イメージ調整] > [用紙処理]


![bg right:30% 60%](./picture/panel-media-handleing.png)


---
## ラベル停止位置の調整
カット、剥離、切取り時の停止位置を設定。
</br>

|||
|-|-|
| 有効値| -120 ～ +120
| ZPL コマンド| ~TA###
| SGD コマンド| ezpl.tear_off
| フロントパネル | [印刷] > [イメージ調整] > [切り取線オフセット]


![bg right:30% 60%](./picture/ZT411-Meia-tof-01.png)


---

## 実習2 (基本)

1. ラベル停止位置の微調整をしてみよう。

         - カットの場合、ラベル間のど真ん中でカットしてみよう。
         - 剥離の場合、適切に剥離できる位置に微調整をしよう。
  
1. ラベル停止位置を大きく変えてラベルドロップ現象を再現してみよう

        どのあたり設定値でラベルドロップが発生するのか確認してみよう。

---

## 実習3 (応用)

1. RFID のマニュアルキャリブレーションを実行し、エンコードスポットを確認してみよう。

         - ^XA^HR^XZを実行し、返り値を確認しよう。
         - 返り値から最適なエンコードスポットと設定値を割り出そう。
  
2. オートキャリブレーションより浅いエンコードポジションを設定し、印刷してみよう。
   
        ラベルドロップが発生せず、エンコードができていることを確認しよう。

---
## RFID プログラミング位置
RFIDのエンコードポイントの設定。カッター利用時はできるだけ、Backfeedが浅めの設定にすると良いことが多い。

![bg right:30% 60%](./picture/ZT611-RFID-Position.png)

|||
|-|-|
| 有効値| Bxxx ～ F0 ～ Fxxx
| ZPL コマンド| ^RS
| SGD コマンド| rfid.position.program
| フロントパネル | [RFID] > [RFID] > [RFIDプログラミング位置]


---

### マニュアルで適切なRFIDプログラミング位置を知る方法
</br>
RFIDオートキャリブレーションは確実にエンコードができるポイントを設定する傾向があるため、プログラミング位置が深めのbackfeed に設定されることが多い。その結果、RFID + カッター利用時にラベルのドロップの遠因となることがある。回避するにはドロップしないエンコードポイントをマニュアルをZPL/SGDコマンドで確認する必要がある。コマンド詳細は下記Articleを参照すること。

    ZT411 & ZT421 RFID Calibration
    Article ID:000018011  •  November 18, 2019
</br>
カッター、切り取り時は並行して、バックフィード量を最大化できるように「ラベル停止位置の調整」を実施した方が良い。

![bg right:30% 85%](./picture/Zpl_Hr_Result.png)

---

# Expamples： Result of ^HR

<!-- _class: smallfontsize -->

RFID calibration=passed
position=B9 MM,A1,21,22
tid information=E280.6890:NXP
leading edge
    Tag 1   ,
EPC,9CD5    ,
(略)
B11,A1,14,15,
B10,A1,13,15,
B09,A1,13,14,<---****A1
B08,A1,13,15,
B07,A1,16,17,
B06,A1,18,20, ★
B05,A1,24,26, 
B04,A1,  ,  ,
B03,A1,26,  ,
B02,A1,25,26,
B01,A1,26,27,
F00,A1,  ,  ,
(略)
trailing edge

---



## まとめ

用紙オプション利用時に絶対に押さえておくポイント。

1. 用紙/RFIDキャリブレーションを適切に行う
        
        印字起点(F0)をきちんと設定することが基本。

2. ラベルの停止位置を適切にコントロールする
   
        カット・剥離に適した停止位置を設定する。
3. バックフィード量をコントロールする ★

        バックフィード時にラベルがプラテンローラから滑落しないバックフィード量設定にする。
        RFID、カッターを利用時はバックフィード量が大きくなりがちなので要注意。
---

<!-- class: sub-title -->


# Any Questions? 

---


# テスト

---


# 結果発表

---


# セミナーアンケート
---

# End 
---



Adjusting Cut Position for ZPL Printers When Using ZDesigner Driver
Article ID:000015824  •  February 16, 2021


混乱の元

~TAxxx
ezpl.tear_off : 99 , Choices: -120-120

media.tof

! U1 setvar "media.tof" "0"
! U1 setvar "ezpl.tear_off" "0"


---
Zebra support community : Article ID:000016155

バックフィードが発生する理由

Front Feed > ラベルの印刷・搬送
Back Feed > 切り取り位置・カット位置・ピール位置・から印刷/エンコード位置への移動

To avoid a dead band at this leading edge, a backfeed is required to properly place the label under the printhead for the next print cycle.

Tear Off Mode– The inter-label gap is moved forward to the Tear Bar so a user can tear the printed labels cleanly at the gap. 

Peel Off Mode – After printing the label is fed forward to allow the edge of the printed label to hang from the peel bar until taken,

Cutter Mode – The label is fed forward to the cut line where the cutter cuts the printed label.

Rewind Mode – There is no backfeed associated with Rewind Mode  


---
|||
|-|-|
|^XB| 記述された^XA..^XZにて、Tear-off/Cutter/Peel postionへのラベルフィードをしない。バッチ処理のスループット向上やカット不要な場合に利用する。
|~JS| media.backfeed : N | 

^XB in Tear-off Mode
Normal Operation: backfeed, print, and feed to rest
^XB Operation: print (Rewind Mode)
^XB in Peel-off Mode
Normal Operation: backfeed, print, and feed to rest
^XB Operation: print (Rewind Mode)
NOTE: To prevent jamming in cutter mode, ^XB suppresses backfeed and cutting
 
^XA^FO50,50,^A0,32,32^FDAAAAAAAAAAAAAAAAA^FS^XZ



Any questions? 

--
付録
### Silverline 2 +

<!--

-->


## 適切なオプションを選択する方法

---
## オプション付きSKUと後付けの違い

---
<!-- _class: default -->
はじめに1

<style>
    .split {
        display: table;
        width: 100%;
    }
    .split-item {
        display: table-cell;
        padding: 0px;
        width: 50%;
    }
    .split-left {
        position: relative;
    }
    .split-left__inner {
        height: 100%;
        position: fixed;
        width: 40%;
    }
        .split-right {
        position: relative;
    }
    .split-right__inner {
        height: 100%;
        position: fixed;
        width: 40%;
    }
</style>

<div class="split">
  <div class="split-item split-left">
    <div class="split-left__inner">

    Sub title 1

- 以下のQUBO形式のベイズ線形回帰モデルを獲得関数としたBBO手法
  $$ \tilde{f}(\vec{\bm{x}}\mid\vec{\bm{\alpha}}) = a_0 + \Sigma_{i}a_i x_i + \Sigma_{i < j} a_{ij} x_i x_j$$

- 離散変数を含むBBOに対するベイズ最適化手法として提案されている

    </div>
  </div>
  <div class="split-item split-right">
    <div class="split-right__inner">

        Sub title 2

- 以下のQUBO形式のベイズ線形回帰モデルを獲得関数としたBBO手法
  $$ \tilde{f}(\vec{\bm{x}}\mid\vec{\bm{\alpha}}) = a_0 + \Sigma_{i}a_i x_i + \Sigma_{i < j} a_{ij} x_i x_j$$
- 離散変数を含むBBOに対するベイズ最適化手法として提案されている

    </div>
  </div>
</div>



