###1、屏幕尺寸

屏幕大小，指屏幕对角线长度，而不是屏幕的高度或宽度，单位为英寸。

![image.png](https://upload-images.jianshu.io/upload_images/6828981-6c9a607e9b8afdaa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###2、显示/物理分辨率

屏幕拥有像素的总数以及屏幕宽和高方向的像素数量，单位为像素。像素/px是组成屏幕图像的最小点。同样大小的屏幕，像素越高越清晰。

![image.png](https://upload-images.jianshu.io/upload_images/6828981-dfc9b17dfca922f5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###3、屏幕像素密度PPI

ppi是指每英寸所拥有的像素数/每英寸像素。像素密越高，代表屏幕图像显示越清晰。

![image.png](https://upload-images.jianshu.io/upload_images/6828981-e14d4358f3f9022c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###4、视网膜屏幕

![image.png](https://upload-images.jianshu.io/upload_images/6828981-e6b8d1f1732ad9d4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
*ppi与dpi
![image.png](https://upload-images.jianshu.io/upload_images/6828981-a0c4bd40a3582253.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###5、设备像素(device pixel)与逻辑像素(css像素)

####设备像素
 是物理概念，指的是设备中使用的物理像素,也就是屏幕中的发光的点数(屏幕由很多个发光点组成，每个发光点可以显示不同的颜色，这些发光的点组成了屏幕)。
比如iPhone 5的分辨率640 x 1136px。横向有640个发光的点，纵向有1136个发光的点。所以我们说iPhone5 的设备水平像素是640像素，指的是640个发光点。
####CSS像素
是Web编程的概念，CSS样式代码中使用的逻辑像素。1个逻辑像素可能对应多个物理像素（发光点）。

在CSS规范中，长度单位可以分为两类，绝对(absolute)单位以及相对(relative)单位。px是一个相对单位，相对的是设备像素(device pixel)。
>假设电脑的物理分辨率是1024* 768。 如果我故意设置操作系统分辨率为512*384（水平和垂直各缩小1倍），那么此时css定义的1px像素的盒子在屏幕中的显示的宽度比原来高分辨率的宽度增加一倍，所以CSS中的像素只是相对，不是绝对的。当对1px像素进行缩小时不会有效果，因为CSS像素至少要占有一个设备像素。

>iPhone 5使用的是Retina视网膜屏幕，横向逻辑css的像素是320px，但是实际物理像素是640的点，所以水平方向就会有2个点对应css的1个像素，垂直也是两倍的关系，也就是1个css的逻辑像素：由水平2个物理像素点和垂直2个像素点也就是（2乘2=4）4个物理像素点  显示1px宽1px高的一个逻辑的css像素。

####设备独立像素（DIP）
设备独立像素（DIP，device-independent pixel，density-independent pixel），简单地来说设备独立像素就是：独立于设备的用于逻辑上衡量像素的单位。在移动Web开发中就是指的CSS的逻辑像素。

###6、设备像素比(devicePixelRatio)

设备像素比(dpr) 与 ppi有一定的相关性，即ppi越大，dpr也相应的较大，1dpr 对应160ppi ，其对照表如下：
![image.png](https://upload-images.jianshu.io/upload_images/6828981-a347525eacd43c6d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
设备像素比DPR(devicePixelRatio)是默认缩放为100%的情况下，设备像素（也称物理像素）和CSS像素的比值(设备独立像素)。

####DPR = 设备像素 / CSS像素
>仅仅计算横向或者纵向。比如：iphone5为例：水平物理像素640  页面缩放100%时，横向320px，则dpr = 640 / 320 = 2

DPR也有对应的javascript属性`window.devicePixelRatio `（ie11+,edge,chrome49+, Safari9.1+）
DPR不一定都是整数，尤其是android设备十分的碎片化！

###7、视口
问题：PC端设计的网页一般都是大于960px 尺寸，移动端上的浏览器为了能够将那些为PC端设计的网站正常显示，一般都给一个默认的整屏的宽度为980px（css像素），虽然能这样让移动端浏览器兼容大部分PC端页面，但是页面缩放后文字会变得非常小，用户需要手动放大缩小才能看清楚，体验非常差。

![image.png](https://upload-images.jianshu.io/upload_images/6828981-2d28fcaffe48d2b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

苹果首先在浏览器上引入了视口的功能，随后各大浏览器都跟随实现。

视口（viewport）是用户网页的可视区域，也可称之为视区。

####PC端视口
PC端视口的大小跟浏览器的可视区的宽高保持1：1固定比例对应。也就是说浏览器改变宽高，视口跟着改变。
####移动端视口
在移动端视口与移动端浏览器屏幕宽度不再相关联，可以比浏览器的可视区域更大或者更小，还可以对页面进行缩放（放大、缩小）。
由于移动端的视口可以进行放大、缩小、改变宽高，所以造成了视口的大小跟屏幕能显示的内容的宽度和布局的宽度不一致，这就出现两个概念：布局视口和视觉视口。

####视图视口（visual viewport）
视图视口是手持设备物理屏幕的可视区域。
![image.png](https://upload-images.jianshu.io/upload_images/6828981-97989b73fdaf31c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
视觉视口是用户正在看到的网站的区域，对于的javascript属性是`window.innerWidth/Height`
####布局视口（layout viewport）
布局视口：在移动端视口与移动端浏览器屏幕宽度不再相关联，可以单独设置它的宽高（主要是宽），这个视口就是HTML页面布局的区域，并且可以通过viewport meta标签控制。

![image.png](https://upload-images.jianshu.io/upload_images/6828981-5533df687a6659f8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

>布局视口不会受到缩放的影响，缩放不会导致页面重排渲染，对于移动端宝贵的性能来说非常重要。

layout viewport布局视口的宽度可以通过js的`document.documentElement.clientWidth`获取。

各个浏览器默认的布局视口宽度：
![image.png](https://upload-images.jianshu.io/upload_images/6828981-136b41c1f100684c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
####meta标签控制布局视口的宽度
meta标签设置布局视口的语法：
`<meta name="viewport" content="name1=value1,name2=value2">`
![image.png](https://upload-images.jianshu.io/upload_images/6828981-0e27e171a8692b96.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
width是设置布局视口的宽度。如果设置iphone5s具体的width值为：320。

`<meta name="viewport" content="width=320">`
![image.png](https://upload-images.jianshu.io/upload_images/6828981-213c3d493b334c80.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如果只是设置viewport的width属性时，iphone的浏览器自动将页面进行缩放到恰好放下页面而不出现滚动条，所以此时：visual viewport == layourt viewport。
上例中：就像把屏幕分成320份。如果设置一个元素为100px*100px，看起来就是屏幕的100/320
如果布局视口的宽度=device-width(设备宽度，也就是:物理像素/dpr)时，此时页面100%的宽度正好能在视觉视口中完全显示，不需要缩放查看页面了,而且在不同尺寸下都能基本表现一致，此时的布局视口的状态我们就称为理想视口（ideal viewport）。
测试代码：

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>理想视口</title>
  <style>
    html, body, div {
      padding: 0;
      margin: 0;
    }
    .box {
      width: 100%;
      height: 100px;
      background-color: #ccc;
      box-sizing: border-box;
    }
  </style>
</head>
<body>
  <div class="box">
  </div>
</body>
</html>
```
####理想视口(ideal viewport)
所谓的理想视口是：
第一，不需要用户缩放和横向滚动条就能正常的查看网站的所有内容；
第二，显示的文字的大小是合适，比如一段14px大小的文字，不会因为在一个高密度像素的屏幕里显示得太小而无法看清，理想的情况是这段14px的文字无论是在何种密度屏幕，何种分辨率下，显示出来的大小都是差不多的。当然，不只是文字，其他元素像图片什么的也是这个道理。
理想视口的宽度一般可以通过以下公式计算：
理想视口的宽度 = 设备像素 / dpr
也就是当布局视口的宽度 等于 设备独立像素的宽度时就是理想视口。
简单的指定的方法：
```
<!--这一行代码告诉浏览器，布局视口的宽度应该与理想视口的宽度一致--> 
<meta name="viewport" content="width=device-width">
或者
 <meta name="viewport" content="initial-scale=1">
```
####meta标签控制布局视口的缩放
` <meta name="viewport" content="initial-scale=1">`

为什么我们指定了meta标签的viewport缩放比例1也可以实现理想视口呢？
这个比值到底是谁呢？这个值是确定整体网页缩放的比例。
缩放比 = 理想视口的宽度 / 视觉视口的宽度
也就是说当视觉视口的宽度 和  理想视口的宽度相等时，则就是1。因为手机端的浏览器会自动设置布局视口的宽度为视觉视口的宽度，所以此时：设备的布局视口==视觉视口==理想视口。
看一图就明了：

![image.png](https://upload-images.jianshu.io/upload_images/6828981-738955eeacc058f7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![image.png](https://upload-images.jianshu.io/upload_images/4393631-822d06f750903bf4.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/594/format/webp)

视觉视口：当页面手动放大的时候，用户可以看到的网页内容减少，视觉视口的尺寸变小。反之，同理不赘述。
默认的缩放（initial-scale）值设置后，浏览器会根据理想视口计算出视觉视口，并设置布局视口==视觉视口。
但是如果width和initial-scale都设置的时候，浏览器会取两个值较大的，所以可以通过width设置一个最小的布局视口宽度

####viewport的其他设置

maximum-scale
在移动端，你可能会考虑用户浏览不便，然后给予用户放大页面的权利，但同时又希望是在一定范围内的放大，这时就可以使用maximum-scale来进行约束。
maximum-scale用于指定用户能够放大的比例。

举个例子来讲：
`<meta name="viewport" content="initial-scale=1,maximum-scale=5" />`
假设页面的默认缩放值initial-scale是1，那么用户最终能够将页面放大到这个初始页面大小的5倍。

minimum-scale
类似maximum-scale的描述，不过minimum-scale是用来指定页面缩小比例的。

通常情况下，为了有更好地体验，不会定义该属性的值比1更小，因为那样页面将变得难以阅读。

user-scalable
如果你不想页面被放大或者缩小，通过定义user-scalable来约束用户是否可以通过手势对页面进行缩放即可。

该属性的默认值为yes，即可被缩放（如果使用默认值，该属性可以不定义）；当然，如果你的应用不打算让用户拥有缩放权限，可以将该值设置为no。
使用方法如下：
`<meta name="viewport" content="user-scalable=no" />`

>本文参考：[https://www.jianshu.com/p/4c029b6d433a](https://www.jianshu.com/p/4c029b6d433a)




