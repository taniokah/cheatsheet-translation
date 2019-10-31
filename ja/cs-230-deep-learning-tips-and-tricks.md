**Deep Learning Tips and Tricks translation**

<br>

**1. Deep Learning Tips and Tricks cheatsheet**

&#10230;深層学習（ディープラーニング）のアドバイスやコツのチートシート

<br> 


**2. CS 230 - Deep Learning**

&#10230;CS 230 - 深層学習

<br>


**3. Tips and tricks**

&#10230;アドバイスやコツ

<br>


**4. [Data processing, Data augmentation, Batch normalization]**

&#10230;[データ処理、Data augmentation (データ拡張)、Batch normalization (バッチ正規化)]

<br>


**5. [Training a neural network, Epoch, Mini-batch, Cross-entropy loss, Backpropagation, Gradient descent, Updating weights, Gradient checking]**

&#10230;[ニューラルネットワークの学習、エポック、ミニバッチ、交差エントロピー誤差、誤差逆伝播法、勾配降下法、重み更新、勾配チェック]

<br>


**6. [Parameter tuning, Xavier initialization, Transfer learning, Learning rate, Adaptive learning rates]**

&#10230;[パラメータチューニング、Xavier初期化、転移学習、学習率、適応学習率]

<br>


**7. [Regularization, Dropout, Weight regularization, Early stopping]**

&#10230;[正規化、Dropout (ドロップアウト)、重みの正規化、Early stopping (学習の早期終了)]

<br>


**8. [Good practices, Overfitting small batch, Gradient checking]**

&#10230;[おすすめの技法、小さいバッチの過学習、勾配チェック]

<br>


**9. View PDF version on GitHub**

&#10230;GitHubでPDF版を見る

<br>


**10. Data processing**

&#10230;データ処理

<br>


**11. Data augmentation ― Deep learning models usually need a lot of data to be properly trained. It is often useful to get more data from the existing ones using data augmentation techniques. The main ones are summed up in the table below. More precisely, given the following input image, here are the techniques that we can apply:**

&#10230;Data augmentation (データ拡張) - 大抵の場合は、深層学習のモデルを適切に訓練するには大量のデータが必要です。Data augmentation という技術を用いて既存のデータから、データを増やすことがよく役立ちます。Data augmentation の主な手法は以下にまとまっています。より正確には、以下の入力画像に対して、下記の技術が適用できます。

<br>


**12. [Original, Flip, Rotation, Random crop]**

&#10230;[元の画像、反転、回転、ランダムな切り抜き]

<br>


**13. [Image without any modification, Flipped with respect to an axis for which the meaning of the image is preserved, Rotation with a slight angle, Simulates incorrect horizon calibration, Random focus on one part of the image, Several random crops can be done in a row]**

&#10230;[何も変更されていない画像、画像の意味が変わらない軸における反転、わずかな角度の回転、不正確な水平線の校正（calibration）をシミュレートする、画像の一部へのランダムなフォーカス、連続して数回のランダムな切り抜きが可能]

<br>


**14. [Color shift, Noise addition, Information loss, Contrast change]**

&#10230;[カラーシフト、ノイズの付加、情報損失、コントラスト（鮮やかさ）の修正]

<br>


**15. [Nuances of RGB is slightly changed, Captures noise that can occur with light exposure, Addition of noise, More tolerance to quality variation of inputs, Parts of image ignored, Mimics potential loss of parts of image, Luminosity changes, Controls difference in exposition due to time of day]**

&#10230;[RGBのわずかな修正、照らされ方によるノイズの捕捉、ノイズの付加、入力画像の品質のばらつきへの耐性の強化、画像の一部の無視、画像の一部が欠ける可能性の再現、明るさの変化、時刻による露出の違いのコントロール]

<br>


**16. Remark: data is usually augmented on the fly during training.**

&#10230;備考：データ拡張は基本的には学習時に臨機応変に行われる。

<br>


**17. Batch normalization ― It is a step of hyperparameter γ,β that normalizes the batch {xi}. By noting μB,σ2B the mean and variance of that we want to correct to the batch, it is done as follows:**

&#10230;batch normalization - ハイパーパラメータ γ,β によってバッチ {xi} を正規化するステップです。修正を加えたいバッチの平均と分散をμB,σ2Bと表記すると、以下のように行えます。

<br>


**18. It is usually done after a fully connected/convolutional layer and before a non-linearity layer and aims at allowing higher learning rates and reducing the strong dependence on initialization.**

&#10230;より高い学習率を利用可能にし初期化への強い依存を減らすことを目的として、基本的には全結合層・畳み込み層のあとで非線形層の前に行います。

<br>


**19. Training a neural network**

&#10230;ニューラルネットワークの学習

<br>


**20. Definitions**

&#10230;定義

<br>


**21. Epoch ― In the context of training a model, epoch is a term used to refer to one iteration where the model sees the whole training set to update its weights.**

&#10230;エポック - モデル学習においてエポックとは学習の繰り返しの中の1回を指す用語で、1エポックの間にモデルは全学習データからその重みを更新します。

<br>


**22. Mini-batch gradient descent ― During the training phase, updating weights is usually not based on the whole training set at once due to computation complexities or one data point due to noise issues. Instead, the update step is done on mini-batches, where the number of data points in a batch is a hyperparameter that we can tune.**

&#10230;ミニバッチ勾配降下法 - 学習段階では、計算が複雑になりすぎるため通常は全データを一度に使って重みを更新することはありません。またノイズが問題になるため1つのデータポイントだけを使って重みを更新することもありません。代わりに、更新はミニバッチごとに行われます。各バッチに含まれるデータポイントの数は調整可能なハイパーパラメータです。

<br>


**23. Loss function ― In order to quantify how a given model performs, the loss function L is usually used to evaluate to what extent the actual outputs y are correctly predicted by the model outputs z.**

&#10230;損失関数 - 得られたモデルの性能を数値化するために、モデルの出力zが実際の出力yをどの程度正確に予測できているかを評価する損失関数Lが通常使われます。

<br>


**24. Cross-entropy loss ― In the context of binary classification in neural networks, the cross-entropy loss L(z,y) is commonly used and is defined as follows:**

&#10230;交差エントロピー誤差 - ニューラルネットワークにおける二項分類では、交差エントロピー誤差L(z,y)が一般的に使用されており、以下のように定義されています。

<br>


**25. Finding optimal weights**

&#10230;最適な重みの探索

<br>


**26. Backpropagation ― Backpropagation is a method to update the weights in the neural network by taking into account the actual output and the desired output. The derivative with respect to each weight w is computed using the chain rule.**

&#10230;誤差逆伝播法 - 実際の出力と期待される出力の差に基づいてニューラルネットワークの重みを更新する手法です。各重みwに関する微分は連鎖律を用いて計算されます。

<br>


**27. Using this method, each weight is updated with the rule:**

&#10230;この方法を使用することで、それぞれの重みはそのルールにしたがって更新されます。

<br>


**28. Updating weights ― In a neural network, weights are updated as follows:**

&#10230;重みの更新 - ニューラルネットワークでは、以下の方法にしたがって重みが更新されます。

<br>


**29. [Step 1: Take a batch of training data and perform forward propagation to compute the loss, Step 2: Backpropagate the loss to get the gradient of the loss with respect to each weight, Step 3: Use the gradients to update the weights of the network.]**

&#10230;[ステップ１：訓練データのバッチを用いて順伝播で損失を計算し、ステップ２：損失を逆伝播させて各重みに関する損失の勾配を求め、ステップ３：求めた勾配を用いてネットワークの重みを更新します。]

<br>


**30. [Forward propagation, Backpropagation, Weights update]**

&#10230;[順伝播、逆伝播、重みの更新]

<br>


**31. Parameter tuning**

&#10230;パラメータチューニング

<br>


**32. Weights initialization**

&#10230;重みの初期化

<br>


**33. Xavier initialization ― Instead of initializing the weights in a purely random manner, Xavier initialization enables to have initial weights that take into account characteristics that are unique to the architecture.**

&#10230;Xavier初期化 - 完全にランダムな方法で重みを初期化するのではなく、そのアーキテクチャのユニークな特徴を考慮に入れて重みを初期化する方法です。

<br>


**34. Transfer learning ― Training a deep learning model requires a lot of data and more importantly a lot of time. It is often useful to take advantage of pre-trained weights on huge datasets that took days/weeks to train, and leverage it towards our use case. Depending on how much data we have at hand, here are the different ways to leverage this:**

&#10230;転移学習 - 深層学習のモデルを学習させるには大量のデータと何よりも時間が必要です。膨大なデータセットから数日・数週間をかけて構築した学習済みモデルを利用し、自身のユースケースに活かすことは有益であることが多いです。手元にあるデータ量次第ではありますが、これを利用する以下の方法があります。

<br>


**35. [Training size, Illustration, Explanation]**

&#10230;[学習サイズ、図、解説]

<br>


**36. [Small, Medium, Large]**

&#10230;[小、中、大]

<br>


**37. [Freezes all layers, trains weights on softmax, Freezes most layers, trains weights on last layers and softmax, Trains weights on layers and softmax by initializing weights on pre-trained ones]**

&#10230;[全層の凍結、softmaxの重みの学習、大半の層の凍結、最終層とsoftmaxの重みの学習、学習済みの重みで初期化した各層とsoftmaxの重みの学習]

<br>


**38. Optimizing convergence**

&#10230;収束の最適化

<br>


**39. Learning rate ― The learning rate, often noted α or sometimes η, indicates at which pace the weights get updated. It can be fixed or adaptively changed. The current most popular method is called Adam, which is a method that adapts the learning rate.
**

&#10230;学習率 - 多くの場合αや時々ηと表記される学習率とは、重みの更新速度を表しています。学習率は固定することもできる上に、適応的に変更することもできます。現在もっとも使用される手法は、学習率を適切に調整するAdamと呼ばれる手法です。

<br>


**40. Adaptive learning rates ― Letting the learning rate vary when training a model can reduce the training time and improve the numerical optimal solution. While Adam optimizer is the most commonly used technique, others can also be useful. They are summed up in the table below:**

&#10230;適応学習率法 - モデルを学習させる際に学習率を変動させると、学習時間の短縮や精度の向上につながります。Adamがもっとも一般的に使用されている手法ですが、他の手法も役立つことがあります。それらの手法を下記の表にまとめました。

<br>


**41. [Method, Explanation, Update of w, Update of b]**

&#10230;[手法、解説、wの更新、bの更新]

<br>


**42. [Momentum, Dampens oscillations, Improvement to SGD, 2 parameters to tune]**

&#10230;[Momentum（運動量）、振動の抑制、SGDの改良、チューニングする2つのパラメータ]

<br>


**43. [RMSprop, Root Mean Square propagation, Speeds up learning algorithm by controlling oscillations]**

&#10230;[RMSprop、二乗平均平方根のプロパゲーション、振動をコントロールすることによる学習アルゴリズムの高速化]

<br>


**44. [Adam, Adaptive Moment estimation, Most popular method, 4 parameters to tune]**

&#10230;[Adam、Adaptive Moment estimation、もっとも人気のある手法、チューニングする4つのパラメータ]

<br>


**45. Remark: other methods include Adadelta, Adagrad and SGD.**

&#10230;備考：他にAdadelta、Adagrad、SGDなどの手法があります。

<br>


**46. Regularization**

&#10230;正則化

<br>


**47. Dropout ― Dropout is a technique used in neural networks to prevent overfitting the training data by dropping out neurons with probability p>0. It forces the model to avoid relying too much on particular sets of features.**

&#10230;ドロップアウト - ドロップアウトとは、ニューラルネットワークで過学習を避けるためにp>0の確率でノードをドロップアウト（無効化）する手法です。モデルが特定の特徴量に依存しすぎることを避けるよう強制します。

<br>


**48. Remark: most deep learning frameworks parametrize dropout through the 'keep' parameter 1−p.**

&#10230;備考：ほとんどの深層学習のフレームワークでは、ドロップアウトを'keep'というパラメータ（1-p)でパラメータ化します。

<br>


**49. Weight regularization ― In order to make sure that the weights are not too large and that the model is not overfitting the training set, regularization techniques are usually performed on the model weights. The main ones are summed up in the table below:**

&#10230;重みの正則化 - 重みが大きくなりすぎず、モデルが過学習しないようにするため、モデルの重みに対して正則化を行います。主な正則化手法は以下の表にまとめられています。

<br>


**50. [LASSO, Ridge, Elastic Net]**

&#10230;[LASSO、Ridge、Elastic Net]

<br>

**50 bis. Shrinks coefficients to 0, Good for variable selection, Makes coefficients smaller, Tradeoff between variable selection and small coefficients]**

&#10230;bis. 係数を0へ小さくする、変数選択に適している、係数を小さくする、変数選択と小さい係数のトレードオフ

<br>

**51. Early stopping ― This regularization technique stops the training process as soon as the validation loss reaches a plateau or starts to increase.**

&#10230;Early stopping - バリデーションの損失が変化しなくなるか、あるいは増加し始めたときに学習を早々に止める正則化方法

<br>


**52. [Error, Validation, Training, early stopping, Epochs]**

&#10230;[損失、評価、学習、early stopping、エポック]

<br>


**53. Good practices**

&#10230;おすすめの技法

<br>


**54. Overfitting small batch ― When debugging a model, it is often useful to make quick tests to see if there is any major issue with the architecture of the model itself. In particular, in order to make sure that the model can be properly trained, a mini-batch is passed inside the network to see if it can overfit on it. If it cannot, it means that the model is either too complex or not complex enough to even overfit on a small batch, let alone a normal-sized training set.**

&#10230;小さいバッチの過学習 - モデルをデバッグするとき、モデル自体の構造に大きな問題がないか確認するため簡易的なテストが役に立つことが多いです。特に、モデルを正しく学習できることを確認するため、ミニバッチをネットワークに渡してそれを過学習できるかを見ます。もしできなければ、モデルは複雑すぎるか単純すぎるかのいずれかであることを意味し、普通サイズの学習データセットでは言うまでもなく、小さいバッチでは過学習できないのです。

<br>


**55. Gradient checking ― Gradient checking is a method used during the implementation of the backward pass of a neural network. It compares the value of the analytical gradient to the numerical gradient at given points and plays the role of a sanity-check for correctness.**

&#10230;Gradient checking (勾配チェック) - Gradient checking とは、ニューラルネットワークの逆伝播を実装する際に用いられる手法です。特定の点で解析的勾配と数値的勾配とを比較する手法で、逆伝播の実装が正しいことを確認できます。

<br>


**56. [Type, Numerical gradient, Analytical gradient]**

&#10230;[種類、数値的勾配、解析的勾配]

<br>


**57. [Formula, Comments]**

&#10230;[公式、コメント]

<br>


**58. [Expensive; loss has to be computed two times per dimension, Used to verify correctness of analytical implementation, Trade-off in choosing h not too small (numerical instability) nor too large (poor gradient approximation)]**

&#10230;[計算コストが高い；損失を次元ごとに２回計算する必要がある、解析的実装が正しいかのチェックに用いられる、hを選ぶ時に小さすぎると数値不安定になり、大きすぎると勾配近似が不正確になるというトレードオフがある]

<br>


**59. ['Exact' result, Direct computation, Used in the final implementation]**

&#10230;[「正しい」結果、直接的な計算、最終的な実装での使用]

<br>


**60. The Deep Learning cheatsheets are now available in [target language].

&#10230;深層学習のチートシートは[対象言語]で利用可能になりました。


**61. Original authors**

&#10230;原著者

<br>

**62.Translated by X, Y and Z**

&#10230;X・Y・Z 訳

<br>

**63.Reviewed by X, Y and Z**

&#10230;X・Y・Z 校正

<br>

**64.View PDF version on GitHub**

&#10230;GitHubでPDF版を見る

<br>

**65.By X and Y**

&#10230;X・Y 著

<br>
