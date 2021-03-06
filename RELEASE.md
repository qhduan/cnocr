# Release Notes

### Update 2020.05.29: 发布 cnocr V1.2.2

主要变更：

* `CnOcr`加入类函数 `CnOcr.set_cand_alphabet(cand_alphabet) `。可通过此类函数设置`cand_alphabet`。这样同一个实例也可以指定不同的`cand_alphabet`进行识别。
* bugfix:
  * 修复同时初始化多个实例时会报错的问题。



### Update 2020.05.25: 发布 cnocr V1.2.1

主要变更：

* bugfix:
  * 修复了zip文件名的typo。



### Update 2020.05.25: 发布 cnocr V1.2.0

主要变更：

* 优化了对数字识别的准确度。
* 优化了模型结构，进一步降低了模型的大小，提升了预测速度；最小模型从原来的`6.8M`降为`4.7M`。
* 使用了[爱因互动 Ein+](https://einplus.cn)自己的CDN存储模型文件，下载速度超快。
* 提供了预测速度更快的 `shorter (-s)`版预训练模型：`densenet-lite-s-gru`和`densenet-lite-s-fc`。
* 默认模型由之前的`conv-lite-fc`改为`densenet-lite-fc`。
* 预测支持使用GPU。
* bugfixs:
  * Web 调用时的内存泄露。感谢 [@myuanz](https://github.com/myuanz)；
  * 输入图片宽度很小时导致异常；
  * 去掉  `f-print`。



### Update 2020.04.21: 发布 cnocr V1.1.0

V1.1.0对代码做了很大改动，重写了大部分训练的代码，也生成了更多更难的训练和测试数据。训练好的模型相较于之前版本的模型精度有显著提升，尤其是针对英文单词的识别。



以下列出了主要的变更：

* 更新了训练代码，使用mxnet的`recordio`首先把数据转换成二进制格式，提升后续的训练效率。训练时支持对图片做实时数据增强。也加入了更多可传入的参数。

* **允许训练集中的文字数量不同，目前是中文10个字，英文20个字母。**

* 提供了更多的模型选择，允许大家按需训练多种不同大小的识别模型。

* 内置了各种训练好的模型，最小的模型只有之前模型的`1/5`大小。所有模型都可免费使用。

* 相较于之前版本的模型，新的模型精度有显著提升，尤其是针对英文单词的识别。**新模型已经可以识别英文单词间的空格。**

* **支持文字识别只在给定字符集中进行。** 对于一些纯数字或者纯英文字母的应用场景可以带来识别率提升。

* 优化了对黑底白字多行文字图片的支持。

* mxnet依赖升级到更新的版本了。很多人反馈mxnet `1.4.1`经常找不到没法装，现在升级到`>=1.5.0,<1.7.0`。

  

### Update 2019.07.25: 发布 cnocr V1.0.0

`cnocr`发布了预测效率更高的新版本v1.0.0。**新版本的模型跟以前版本的模型不兼容**。所以如果大家是升级的话，需要重新下载最新的模型文件。具体说明见下面（流程和原来相同）。



主要改动如下：

-  **crnn模型支持可变长预测，提升预测效率**
-  支持利用特定数据对现有模型进行精调（继续训练）
-  修复bugs，如训练时`accuracy`一直为`0`
-  依赖的 `mxnet` 版本从`1.3.1`更新至 `1.4.1`
