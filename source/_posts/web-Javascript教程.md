---
    title: Javascript
    date: 2023-04-02 10:00:07
    description: JS核心教程
    cover: ./img/first_cover.jpg
    toc_number: true
---

# Web APIs 简介

## 目标

- Web APIs 阶段与 JavaScript 语法阶段的关联性
- 什么是 API
- 什么是 Web API

## Web APIs 和  JS 基础关联性

### JS的组成

![image-20230421142532166](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421142532166.19bkceesm0n4.webp)



### JS 基础阶段以及 Web APIs 阶段 

![image-20230421142752089](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421142752089.p2qfzugdvlc.png)

JS 基础学习 ECMAScript 基础语法为后面作铺垫， Web APIs 是 JS 的应用，大量使用 JS 基础语法做交互效果

## API 和 Web API

### API 
<font color=#ff0000>API（Application Programming Interface,应用程序编程接口）</font>是一些预先定义的函数，目的是提供应用程序与开发人员基于某软件或硬件得以访问一组例程的能力，而又无需访问源码，或理解内部工作机制的细节。

简单理解： <font color=#ff0000>API 是给程序员提供的一种工具，以便能更轻松的实现想要完成的功能。</font>

> 比如手机充电的接口：
> 我们要实现充电这个功能：
> - 我们不关心手机内部变压器，内部怎么存储电等
> - 我们不关心这个充电线怎么制作的
> - 我们只知道，我们拿着充电线插进充电接口就可以充电
> - 这个充电接口就是一个 API 

### Web API 

Web API 是浏览器提供的一套操作浏览器功能和页面元素的 API ( BOM 和 DOM )。
现阶段我们主要针对于浏览器讲解常用的 API , 主要针对浏览器做交互效果。
比如我们想要浏览器弹出一个警示框， 直接使用 alert(‘弹出’)
MDN 详细 API : https://developer.mozilla.org/zh-CN/docs/Web/API
因为 Web API 很多，所以我们将这个阶段称为 Web APIs

## API 和 Web API 总结

1. API 是为我们程序员提供的一个接口，帮助我们实现某种功能，我们会使用就可以了，不必纠结内部如何实现
2. Web API 主要是针对于浏览器提供的接口，主要针对于浏览器做交互效果。
3. Web API 一般都有输入和输出（函数的传参和返回值），Web API 很多都是方法（函数） 
4. 学习 Web API 可以结合前面学习内置对象方法的思路学习

# DOM

## 目标

- 能够说出什么是 DOM  
- 能够获取页面元素  
- 能够给元素注册事件  
- 能够操作 DOM 元素的属性 
- 能够创建元素 
- 能够操作 DOM 节点

## DOM简介

### 什么是DOM

文档对象模型（Document Object Model，简称 DOM），是 W3C 组织推荐的处理可扩展标记语言（HTML或者XML）的标准编程接口。W3C 已经定义了一系列的 DOM 接口，通过这些 DOM 接口可以改变网页的内容、结构和样式

### DOM树

![image-20230421145432307](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421145432307.562bqaxyqpc0.png)

- 文档：一个页面就是一个文档，DOM 中使用 document 表示 元素
- 页面中的所有标签都是元素，DOM 中使用 element 表示 节点
- 网页中的所有内容都是节点（标签、属性、文本、注释等），DOM 中使用 node 表示

<font color=#ff0000>DOM 把以上内容都看做是对象</font>

### 获取元素

#### 如何获取页面元素

DOM在我们实际开发中主要用来操作元素。我们如何来获取页面中的元素呢?

获取页面中的元素可以使用以下几种方式:

- 根据 ID 获取
- 根据标签名获取
- 通过 HTML5 新增的方法获取
- 特殊元素获取

#### 根据 ID 获取

使用 <font color=#ff0000>getElementById()</font> 方法可以获取带有 ID 的元素对象。

```javascript
document.getElementById('id');
```

使用 console.dir() 可以打印我们获取的元素对象，更好的查看对象里面的属性和方法。

#### 根据标签名获取

使用 <font color=#ff0000>getElementsByTagName()</font> 方法可以返回带有指定标签名的对象的集合。

```javascript
document.getElementsByTagName('标签名');
```

<font color=#ff0000>注意：</font>
<font color=#ff0000>1. 因为得到的是一个对象的集合，所以我们想要操作里面的元素就需要遍历。</font>
<font color=#ff0000>2. 得到元素对象是动态的</font>
<font color=#ff0000>3. 如果获取不到元素,则返回为空的伪数组(因为获取不到对象)</font>

还可以获取某个元素(父元素)内部所有指定标签名的子元素。

```javascript
element.getElementsByTagName('标签名');
```

注意：父元素必须是<font color='#ff0000'>单个对象(必须指明是哪一个元素对象)</font>. 获取的时候不包括父元素自己。

#### 通过 HTML5 新增的方法获取

```javascript
document.getElementsByClassName(‘类名’)；// 根据类名返回元素对象集合
document.querySelector('选择器');        // 根据指定选择器返回第一个元素对象
document.querySelectorAll('选择器');     // 根据指定选择器返回
```

<font color=#ff0000>注意：</font>
querySelector 和 querySelectorAll里面的选择器需要加<font color=#ff0000>符号</font>,比如:document.querySelector('<font color=#ff0000>#</font>nav'); 

### 获取特殊元素（body，html）

#### 获取body元素

```javascript
doucumnet.body  // 返回body元素对象
```

#### 获取html元素


```javascript
document.documentElement  // 返回html元素对象
```

### 事件基础

#### 事件概述

JavaScript 使我们有能力创建动态页面，而事件是可以被 JavaScript 侦测到的行为。简单理解：<font color=#ff0000> 触发--- 响应机制</font>。网页中的每个元素都可以产生某些可以触发 JavaScript 的事件

> 例如，我们可以在用户点击某按钮时产生一个 事件，然后去执行某些操作。

#### 事件三要素

1. 事件源 （谁）
2. 事件类型 （什么事件）
3. 事件处理程序 （做啥）

#### 执行事件的步骤

1. 获取事件源
2. 注册事件（绑定事件） 
3. 添加事件处理程序（采取函数赋值形式）

#### 常见的鼠标事件

![image-20230421153845046](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421153845046.1iljzbag6egw.png)

#### 分析事件三要素

- 下拉菜单三要素
- 关闭广告三要素

### 操作元素

JavaScript 的 DOM 操作可以改变网页内容、结构和样式，我们可以利用 DOM 操作元素来改变元素里面的内容 、属性等。注意以下都是属性

#### 改变元素内容

```javascript
element.innerText
```

从起始位置到终止位置的内容, 但它去除 html 标签， 同时空格和换行也会去掉

```javascript
element.innerHTML
```

起始位置到终止位置的全部内容，包括 html 标签，同时保留空格和换行

#### 常用元素的属性操作

1. innerText、innerHTML 改变元素内容
2. src、href
3. id、alt、title

#### 案例： 分时显示不同图片,显示不同问候语

- 根据不同时间，页面显示不同图片，同时显示不同的问候语。
- 如果上午时间打开页面，显示上午好，显示上午的图片。
- 如果下午时间打开页面，显示下午好，显示下午的图片。
- 如果晚上时间打开页面，显示晚上好，显示晚上的图片。

案例分析：

- 根据系统不同时间来判断，所以需要用到日期内置对象
- 利用多分支语句来设置不同的图片
- 需要一个图片，并且根据时间修改图片，就需要用到操作元素src属性
- 需要一个div元素，显示不同问候语，修改元素内容即可

实现代码：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        img {
            width: 300px;
        }
    </style>
</head>

<body>
    <img src="images/s.gif" alt="">
    <div>上午好</div>
    <script>
        // 根据系统不同时间来判断，所以需要用到日期内置对象
        // 利用多分支语句来设置不同的图片
        // 需要一个图片，并且根据时间修改图片，就需要用到操作元素src属性
        // 需要一个div元素，显示不同问候语，修改元素内容即可
        // 1.获取元素
        var img = document.querySelector('img');
        var div = document.querySelector('div');
        // 2. 得到当前的小时数
        var date = new Date();
        var h = date.getHours();
        // 3. 判断小时数改变图片和文字信息
        if (h < 12) {
            img.src = 'images/s.gif';
            div.innerHTML = '亲，上午好，好好写代码';
        } else if (h < 18) {
            img.src = 'images/x.gif';
            div.innerHTML = '亲，下午好，好好写代码';
        } else {
            img.src = 'images/w.gif';
            div.innerHTML = '亲，晚上好，好好写代码';

        }
    </script>
</body>

</html>
```

#### 表单元素的属性操作

利用 DOM 可以操作如下表单元素的属性：

type、value、checked、selected、disabled

#### 案例：仿京东显示密码

点击按钮将密码框切换为文本框，并可以查看密码明文。

![image-20230421154553749](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421154553749.3o6dywg0efg0.webp)

核心思路：  

- 点击眼睛按钮，把密码框类型改为文本框就可以看见里面的密码
- 一个按钮两个状态，点击一次，切换为文本框，继续点击一次切换为密码框
- 算法：利用一个flag变量，来判断flag的值，如果是1 就切换为文本框，flag 设置为0，如果是0 就切换为密码框，flag设置为1

实现代码：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box {
            position: relative;
            width: 400px;
            border-bottom: 1px solid #ccc;
            margin: 100px auto;
        }
        
        .box input {
            width: 370px;
            height: 30px;
            border: 0;
            outline: none;
        }
        
        .box img {
            position: absolute;
            top: 2px;
            right: 2px;
            width: 24px;
        }
    </style>
</head>

<body>
    <div class="box">
        <label for="">
            <img src="images/close.png" alt="" id="eye">
        </label>
        <input type="password" name="" id="pwd">
    </div>
    <script>
        // 1. 获取元素
        var eye = document.getElementById('eye');
        var pwd = document.getElementById('pwd');
        // 2. 注册事件 处理程序
        var flag = 0;
        eye.onclick = function() {
            // 点击一次之后， flag 一定要变化
            if (flag == 0) {
                pwd.type = 'text';
                eye.src = 'images/open.png';
                flag = 1; // 赋值操作
            } else {
                pwd.type = 'password';
                eye.src = 'images/close.png';
                flag = 0;
            }

        }
    </script>
</body>

</html>
```

#### 样式属性操作

我们可以通过 JS 修改元素的大小、颜色、位置等样式。

1. element.style     行内样式操作
2. element.className 类名样式操作

<font color='#ff0000'>注意：</font>

<font color='#ff0000'>1.JS 里面的样式采取驼峰命名法 比如 fontSize、 backgroundColor</font>

<font color='#ff0000'>2.JS 修改 style 样式操作，产生的是行内样式，CSS 权重比较高</font>

#### 案例：淘宝点击关闭二维码

当鼠标点击二维码关闭按钮的时候，则关闭整个二维码。

![image-20230421160639039](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421160639039.3k7biildvyo0.webp)

核心思路：  

- 利用样式的显示和隐藏完成， display:none 隐藏元素 display:block 显示元素 
-  点击按钮，就让这个二维码盒子隐藏起来即可

实现代码：

```html
<body>
    <div class="box">
        淘宝二维码
        <img src="images/tao.png" alt="">
        <i class="close-btn">×</i>
    </div>
    <script>
        // 1. 获取元素 
        var btn = document.querySelector('.close-btn');
        var box = document.querySelector('.box');
        // 2.注册事件 程序处理
        btn.onclick = function() {
            box.style.display = 'none';
        }
    </script>
</body>
```

#### 案例： 循环精灵图背景

可以利用 for 循环设置一组元素的精灵图背景

![image-20230421161002371](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421161002371.63jtjkhptro0.webp)

案例分析：

- 首先精灵图图片排列有规律的
- 核心思路： 利用for循环  修改精灵图片的 背景位置 background-position
- 剩下的就是考验你的数学功底了
- 让循环里面的 i 索引号 * 44 就是每个图片的y坐标

实现代码：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        li {
            list-style-type: none;
        }
        
        .box {
            width: 250px;
            margin: 100px auto;
        }
        
        .box li {
            float: left;
            width: 24px;
            height: 24px;
            background-color: pink;
            margin: 15px;
            background: url(images/sprite.png) no-repeat;
        }
    </style>
</head>

<body>
    <div class="box">
        <ul>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </div>
    <script>
        // 1. 获取元素 所有的小li 
        var lis = document.querySelectorAll('li');
        for (var i = 0; i < lis.length; i++) {
            // 让索引号 乘以 44 就是每个li 的背景y坐标  index就是我们的y坐标
            var index = i * 44;
            lis[i].style.backgroundPosition = '0 -' + index + 'px';
        }
    </script>
</body>

</html>
```

#### 案例：显示隐藏文本框内容

当鼠标点击文本框时，里面的默认文字隐藏，当鼠标离开文本框时，里面的文字显示。

![image-20230421161352852](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421161352852.sgc5jisuljk.webp)

案例分析：

- 首先表单需要2个新事件，获得焦点 onfocus  失去焦点 onblur   
- 如果获得焦点， 判断表单里面内容是否为默认文字，如果是默认文字，就清空表单内容
- 如果失去焦点， 判断表单内容是否为空，如果为空，则表单内容改为默认文字

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        input {
            color: #999;
        }
    </style>
</head>

<body>
    <input type="text" value="手机">
    <script>
        // 1.获取元素
        var text = document.querySelector('input');
        // 2.注册事件 获得焦点事件 onfocus 
        text.onfocus = function() {
                // console.log('得到了焦点');
                if (this.value === '手机') {
                    this.value = '';
                }
                // 获得焦点需要把文本框里面的文字颜色变黑
                this.style.color = '#333';
            }
            // 3. 注册事件 失去焦点事件 onblur
        text.onblur = function() {
            // console.log('失去了焦点');
            if (this.value === '') {
                this.value = '手机';
            }
            // 失去焦点需要把文本框里面的文字颜色变浅色
            this.style.color = '#999';
        }
    </script>

</body>

</html>
```

#### 样式属性操作

我们可以通过 JS 修改元素的大小、颜色、位置等样式。

1. element.style     行内样式操作
2. element.className 类名样式操作

<font color='#ff0000'>注意：</font>
<font color='#ff0000'>1. 如果样式修改较多，可以采取操作类名方式更改元素样式。</font>
<font color='#ff0000'> 2. class因为是个保留字，因此使用className来操作元素类名属性</font>
<font color='#ff0000'>3. className 会直接更改元素的类名，会覆盖原先的类名。</font>

#### 案例： 密码框格式提示错误信息

用户如果离开密码框，里面输入个数不是6~16，则提示错误信息，否则提示输入正确信息

![image-20230421162526203](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421162526203.3kcxk8z8xi40.webp)

案例分析：

- 首先判断的事件是表单失去焦点 onblur
- 如果输入正确则提示正确的信息颜色为绿色小图标变化
- 如果输入不是6到16位，则提示错误信息颜色为红色 小图标变化
- 因为里面变化样式较多，我们采取className修改样式

实现代码：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        div {
            width: 600px;
            margin: 100px auto;
        }
        
        .message {
            display: inline-block;
            font-size: 12px;
            color: #999;
            background: url(images/mess.png) no-repeat left center;
            padding-left: 20px;
        }
        
        .wrong {
            color: red;
            background-image: url(images/wrong.png);
        }
        
        .right {
            color: green;
            background-image: url(images/right.png);
        }
    </style>
</head>

<body>
    <div class="register">
        <input type="password" class="ipt">
        <p class="message">请输入6~16位密码</p>
    </div>
    <script>
        // 首先判断的事件是表单失去焦点 onblur
        // 如果输入正确则提示正确的信息颜色为绿色小图标变化
        // 如果输入不是6到16位，则提示错误信息颜色为红色 小图标变化
        // 因为里面变化样式较多，我们采取className修改样式
        // 1.获取元素
        var ipt = document.querySelector('.ipt');
        var message = document.querySelector('.message');
        //2. 注册事件 失去焦点
        ipt.onblur = function() {
            // 根据表单里面值的长度 ipt.value.length
            if (this.value.length < 6 || this.value.length > 16) {
                // console.log('错误');
                message.className = 'message wrong';
                message.innerHTML = '您输入的位数不对要求6~16位';
            } else {
                message.className = 'message right';
                message.innerHTML = '您输入的正确';
            }
        }
    </script>
</body>

</html>
```

操作元素是 DOM 核心内容

![image-20230421162951991](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421162951991.3a0cegyks2i0.png)

#### 案例进阶

1. 世纪佳缘 用户名 显示隐藏内容 
2. 京东关闭广告（直接隐藏即可） 
3. 新浪下拉菜单（微博即可） 
4. 开关灯案例（见素材）

#### 排他思想（案例）

![image-20230421163326279](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421163326279.5kwhr0w19os0.webp)

如果有同一组元素，我们想要某一个元素实现某种样式， 需要用到循环的排他思想算法：

1. 所有元素全部清除样式（干掉其他人）
2. 给当前元素设置样式 （留下我自己）
3. 注意顺序不能颠倒，首先干掉其他人，再设置自己

实现代码：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>

<body>
    <button>按钮1</button>
    <button>按钮2</button>
    <button>按钮3</button>
    <button>按钮4</button>
    <button>按钮5</button>
    <script>
        // 1. 获取所有按钮元素
        var btns = document.getElementsByTagName('button');
        // btns得到的是伪数组  里面的每一个元素 btns[i]
        for (var i = 0; i < btns.length; i++) {
            btns[i].onclick = function() {
                // (1) 我们先把所有的按钮背景颜色去掉  干掉所有人
                for (var i = 0; i < btns.length; i++) {
                    btns[i].style.backgroundColor = '';
                }
                // (2) 然后才让当前的元素背景颜色为pink 留下我自己
                this.style.backgroundColor = 'pink';

            }
        }
        //2. 首先先排除其他人，然后才设置自己的样式 这种排除其他人的思想我们成为排他思想
    </script>
</body>

</html>
```

#### 案例：百度换肤

案例分析：

- 这个案例练习的是给一组元素注册事件
- 给4个小图片利用循环注册点击事件
- 当我们点击了这个图片，让我们页面背景改为当前的图片
- 核心算法： 把当前图片的src 路径取过来，给 body 做为背景即可

实现代码：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        body {
            background: url(images/1.jpg) no-repeat center top;
        }

        li {
            list-style: none;
        }

        .baidu {
            overflow: hidden;
            margin: 100px auto;
            background-color: #fff;
            width: 410px;
            padding-top: 3px;
        }

        .baidu li {
            float: left;
            margin: 0 1px;
            cursor: pointer;
        }

        .baidu img {
            width: 100px;
        }
    </style>
</head>

<body>
    <ul class="baidu">
        <li><img src="images/1.jpg"></li>
        <li><img src="images/2.jpg"></li>
        <li><img src="images/3.jpg"></li>
        <li><img src="images/4.jpg"></li>
    </ul>
    <script>
        // 1. 获取元素 
        var imgs = document.querySelector('.baidu').querySelectorAll('img');
        //console.log(imgs);
        // 2. 循环注册事件 
        for (var i = 0; i < imgs.length; i++) {
            imgs[i].onclick = function () {
                // this.src 就是我们点击图片的路径   images/2.jpg
                // console.log(this.src);
                // 把这个路径 this.src 给body 就可以了
                document.body.style.backgroundImage = 'url(' + this.src + ')';
            }
        }
    </script>
</body>

</html>
```

#### 案例：表格隔行变色

![image-20230421170136853](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421170136853.7f9btg98p5o0.png)

案例分析：

- 用到新的鼠标事件 鼠标经过 onmouseover   鼠标离开 onmouseout
- 核心思路：鼠标经过 tr 行，当前的行变背景颜色， 鼠标离开去掉当前的背景颜色
- 注意： 第一行（thead里面的行）不需要变换颜色，因此我们获取的是 tbody 里面的行

实现代码：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        table {
            width: 800px;
            margin: 100px auto;
            text-align: center;
            border-collapse: collapse;
            font-size: 14px;
        }
        
        thead tr {
            height: 30px;
            background-color: skyblue;
        }
        
        tbody tr {
            height: 30px;
        }
        
        tbody td {
            border-bottom: 1px solid #d7d7d7;
            font-size: 12px;
            color: blue;
        }
        
        .bg {
            background-color: pink;
        }
    </style>
</head>

<body>
    <table>
        <thead>
            <tr>
                <th>代码</th>
                <th>名称</th>
                <th>最新公布净值</th>
                <th>累计净值</th>
                <th>前单位净值</th>
                <th>净值增长率</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
            <tr>
                <td>003526</td>
                <td>农银金穗3个月定期开放债券</td>
                <td>1.075</td>
                <td>1.079</td>
                <td>1.074</td>
                <td>+0.047%</td>
            </tr>
        </tbody>
    </table>
    <script>
        // 1.获取元素 获取的是 tbody 里面所有的行
        var trs = document.querySelector('tbody').querySelectorAll('tr');
        // 2. 利用循环绑定注册事件
        for (var i = 0; i < trs.length; i++) {
            // 3. 鼠标经过事件 onmouseover
            trs[i].onmouseover = function() {
                    // console.log(11);
                    this.className = 'bg';
                }
                // 4. 鼠标离开事件 onmouseout
            trs[i].onmouseout = function() {
                this.className = '';
            }
        }
    </script>
</body>

</html>
```

#### 案例：表单全选取消全选案例

![image-20230421170534501](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421170534501.404rvd8hnvk0.webp)

业务需求：

1. 点击上面全选复选框，下面所有的复选框都选中（全选）
2. 再次点击全选复选框，下面所有的复选框都不中选（取消全选）
3. 如果下面复选框全部选中，上面全选按钮就自动选中
4. 如果下面复选框有一个没有选中，上面全选按钮就不选中
5. 所有复选框一开始默认都没选中状态

案例分析：

- 全选和取消全选做法：  让下面所有复选框的checked属性（选中状态） 跟随 全选按钮即可
- 下面复选框需要全部选中， 上面全选才能选中做法： 给下面所有复选框绑定点击事件，每次点击，都要循环查看下面所有的复选框是否有没选中的，如果有一个没选中的， 上面全选就不选中。
- 可以设置一个变量，来控制全选是否选中

实现代码：

```html
<!DOCTYPE html>
<html>

<head lang="en">
    <meta charset="UTF-8">
    <title></title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }
        
        .wrap {
            width: 300px;
            margin: 100px auto 0;
        }
        
        table {
            border-collapse: collapse;
            border-spacing: 0;
            border: 1px solid #c0c0c0;
            width: 300px;
        }
        
        th,
        td {
            border: 1px solid #d0d0d0;
            color: #404060;
            padding: 10px;
        }
        
        th {
            background-color: #09c;
            font: bold 16px "微软雅黑";
            color: #fff;
        }
        
        td {
            font: 14px "微软雅黑";
        }
        
        tbody tr {
            background-color: #f0f0f0;
        }
        
        tbody tr:hover {
            cursor: pointer;
            background-color: #fafafa;
        }
    </style>

</head>

<body>
    <div class="wrap">
        <table>
            <thead>
                <tr>
                    <th>
                        <input type="checkbox" id="j_cbAll" />
                    </th>
                    <th>商品</th>
                    <th>价钱</th>
                </tr>
            </thead>
            <tbody id="j_tb">
                <tr>
                    <td>
                        <input type="checkbox" />
                    </td>
                    <td>iPhone8</td>
                    <td>8000</td>
                </tr>
                <tr>
                    <td>
                        <input type="checkbox" />
                    </td>
                    <td>iPad Pro</td>
                    <td>5000</td>
                </tr>
                <tr>
                    <td>
                        <input type="checkbox" />
                    </td>
                    <td>iPad Air</td>
                    <td>2000</td>
                </tr>
                <tr>
                    <td>
                        <input type="checkbox" />
                    </td>
                    <td>Apple Watch</td>
                    <td>2000</td>
                </tr>

            </tbody>
        </table>
    </div>
    <script>
        // 1. 全选和取消全选做法：  让下面所有复选框的checked属性（选中状态） 跟随 全选按钮即可
        // 获取元素
        var j_cbAll = document.getElementById('j_cbAll'); // 全选按钮
        var j_tbs = document.getElementById('j_tb').getElementsByTagName('input'); // 下面所有的复选框
        // 注册事件
        j_cbAll.onclick = function() {
                // this.checked 它可以得到当前复选框的选中状态如果是true 就是选中，如果是false 就是未选中
                console.log(this.checked);
                for (var i = 0; i < j_tbs.length; i++) {
                    j_tbs[i].checked = this.checked;
                }
            }
            // 2. 下面复选框需要全部选中， 上面全选才能选中做法： 给下面所有复选框绑定点击事件，每次点击，都要循环查看下面所有的复选框是否有没选中的，如果有一个没选中的， 上面全选就不选中。
        for (var i = 0; i < j_tbs.length; i++) {
            j_tbs[i].onclick = function() {
                // flag 控制全选按钮是否选中
                var flag = true;
                // 每次点击下面的复选框都要循环检查者4个小按钮是否全被选中
                for (var i = 0; i < j_tbs.length; i++) {
                    if (!j_tbs[i].checked) {
                        flag = false;
                        break; // 退出for循环 这样可以提高执行效率 因为只要有一个没有选中，剩下的就无需循环判断了
                    }
                }
                j_cbAll.checked = flag;
            }
        }
    </script>
</body>

</html>
```

#### 自定义属性的操作

##### 1. 获取属性值

- element.属性  获取属性值。
- element.getAttribute('属性');

区别：

- element.属性  获取内置属性值（元素本身自带的属性）
- element.getAttribute(‘属性’);  主要获得自定义的属性 （标准） 我们程序员自定义的属性

##### 2. 设置属性值

- element.属性 = ‘值’  设置内置属性值。
- element.setAttribute('属性', '值'); 

区别：

- element.属性  设置内置属性值
- element.setAttribute(‘属性’);  主要设置自定义的属性 （标准）

##### 3. 移除属性

- element.removeAttribute('属性');

#### 案例：tab 栏切换（重点案例）

当鼠标点击上面相应的选项卡（tab），下面内容跟随变化

![image-20230421171537784](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421171537784.3et5cvnp7ro0.png)

案例分析：

1. Tab栏切换有2个大的模块
2. 上的模块选项卡，点击某一个，当前这一个底色会是红色，其余不变（排他思想） 修改类名的方式
3. 下面的模块内容，会跟随上面的选项卡变化。所以下面模块变化写到点击事件里面。
4. 规律：下面的模块显示内容和上面的选项卡一一对应，相匹配。
5. 核心思路： 给上面的tab_list 里面的所有小li 添加自定义属性，属性值从0开始编号。 
6. 当我们点击tab_list 里面的某个小li，让tab_con 里面对应序号的 内容显示，其余隐藏（排他思想）

实现代码：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        li {
            list-style-type: none;
        }
        
        .tab {
            width: 978px;
            margin: 100px auto;
        }
        
        .tab_list {
            height: 39px;
            border: 1px solid #ccc;
            background-color: #f1f1f1;
        }
        
        .tab_list li {
            float: left;
            height: 39px;
            line-height: 39px;
            padding: 0 20px;
            text-align: center;
            cursor: pointer;
        }
        
        .tab_list .current {
            background-color: #c81623;
            color: #fff;
        }
        
        .item_info {
            padding: 20px 0 0 20px;
        }
        
        .item {
            display: none;
        }
    </style>
</head>

<body>
    <div class="tab">
        <div class="tab_list">
            <ul>
                <li class="current">商品介绍</li>
                <li>规格与包装</li>
                <li>售后保障</li>
                <li>商品评价（50000）</li>
                <li>手机社区</li>
            </ul>
        </div>
        <div class="tab_con">
            <div class="item" style="display: block;">
                商品介绍模块内容
            </div>
            <div class="item">
                规格与包装模块内容
            </div>
            <div class="item">
                售后保障模块内容
            </div>
            <div class="item">
                商品评价（50000）模块内容
            </div>
            <div class="item">
                手机社区模块内容
            </div>

        </div>
    </div>
    <script>
        // 获取元素
        var tab_list = document.querySelector('.tab_list');
        var lis = tab_list.querySelectorAll('li');
        var items = document.querySelectorAll('.item');
        // for循环绑定点击事件
        for (var i = 0; i < lis.length; i++) {
            // 开始给5个小li 设置索引号 
            lis[i].setAttribute('index', i);
            lis[i].onclick = function() {
                // 1. 上的模块选项卡，点击某一个，当前这一个底色会是红色，其余不变（排他思想） 修改类名的方式

                // 干掉所有人 其余的li清除 class 这个类
                for (var i = 0; i < lis.length; i++) {
                    lis[i].className = '';
                }
                // 留下我自己 
                this.className = 'current';
                // 2. 下面的显示内容模块
                var index = this.getAttribute('index');
                console.log(index);
                // 干掉所有人 让其余的item 这些div 隐藏
                for (var i = 0; i < items.length; i++) {
                    items[i].style.display = 'none';
                }
                // 留下我自己 让对应的item 显示出来
                items[index].style.display = 'block';
            }
        }
    </script>
</body>

</html>
```

#### H5自定义属性

<font color='#ff000'>自定义属性目的：是为了保存并使用数据。有些数据可以保存到页面中而不用保存到数据库中。</font>

自定义属性获取是通过getAttribute(‘属性’) 获取。但是有些自定义属性很容易引起歧义，不容易判断是元素的内置属性还是自定义属性。H5给我们新增了自定义属性：

##### 1. 设置H5自定义属性

H5规定自定义属性data-开头做为属性名并且赋值。

比如 <div data-index="1"></div>或者使用 JS 设置  element.setAttribute(‘data-index’, 2)

##### 2. 获取H5自定义属性

1. 兼容性获取   element.getAttribute(‘data-index’);
2. H5新增 element.dataset.index  或者 element.dataset[‘index’]   ie 11才开始支持

### 节点操作

#### 为什么学节点操作

获取元素通常使用两种方式：

![image-20230421172501533](https://cdn.staticaly.com/gh/ruayun/picgo@main/img-js/image-20230421172501533.4tku5mgeu9i0.png)

这两种方式都可以获取元素节点，我们后面都会使用，但是节点操作更简单



