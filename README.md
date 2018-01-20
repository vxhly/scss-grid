# scss-grid

[![NPM version](https://img.shields.io/npm/v/scss-grid.svg?style=flat-square)](https://vxhly.github.io/2016/08/flexbox-layout/) [![GitHub forks](https://img.shields.io/github/forks/vxhly/scss-grid.svg)](https://github.com/vxhly/scss-grid/network) [![GitHub stars](https://img.shields.io/github/stars/vxhly/scss-grid.svg)](https://github.com/vxhly/scss-grid/stargazers) [![NPM download](https://img.shields.io/npm/dm/scss-grid.svg?style=flat-square)](https://npmjs.org/package/scss-grid) [![GitHub license](https://img.shields.io/github/license/vxhly/scss-grid.svg)](https://github.com/vxhly/scss-grid/blob/master/LICENSE)

> Grid Layout 是一种基于二维网格的布局系统，旨在完全改变我们设计基于网格的用户界面的方式，弥补网页开发在二维布局能力上的缺陷，可以通过 bower 和 npm 下载

## 参考

> 使用 SASS 语法编写，使用 gulp 前端打包工具进行打包

> 针对 Grid Layout 布局方式的详细介绍：[Grid 栅格布局](https://www.cnblogs.com/xiaohuochai/p/7083153.html#anchor1) 或者 [Grid 栅格布局](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout)

## download

```bash
git clone https://github.com/vxhly/scss-grid.git
```

### npm

```bash
npm install scss-grid --save
```

### bower

```bash
bower install scss-grid --save
```

### use

```bash
<link href="./scss-grid.min.css">

# or

import 'scss-grid/src/scss-grid.scss'
```

## 为什么需要 Grid Layout

```
grid 栅格布局，二维布局模块，具有强大的内容尺寸和定位能力，适合需要在两个维度上对齐内容的布局
像表格一样，网格布局使作者能够将元素对齐到列和行中。但是，使用CSS网格的布局要比使用表格要多得多。
例如，一个网格容器的子元素可以自己定位，因此它们实际上是重叠的，并且与CSS定位的元素类似。
CSS Grid Layout擅长将页面划分为主要区域，或根据HTML基元构建的控件的部分之间的大小，位置和层次来定义关系。
```

## support

2017年3月，Chrome、Firefox将开启默认支持。

当然对于很多人等不及浏览器默认支持，想提前体验一把，这里提供一些打开方式

![support](https://github.com/vxhly/scss-grid/blob/master/img/caniuse.png)

### Chrome

在浏览器中输入：`chrome://flags/#enable-experimental-web-platform-features`

然后，找到 `Experimental Web Platform features`，点击`启用`。

然后重启浏览器，然后便能体验到了。

### Opera

在浏览器中输入：`opera://flags/#enable-experimental-web-platform-features`

然后，找到 `Enable experimental Web Platform features`，点击 `启用`

同样，重启浏览器

### Safari

在 safari TP 版本以及 WebKit Nightly 中可以使用。不过比较麻烦，需要 `IOS10.12` 以上。

启用方式：Develop > Expermiental Features > CSS Grid

### Firefox

在浏览器中输入：`about:config`

然后，输入 `layout.css.grid`，双击即可激活。

同样，重启浏览器

## menuTree

```
  |- src
    |- _base.scss       => 清除浏览器默认样式，更完整的清除浏览器样式可引入  [normalize.css](https://github.com/necolas/normalize.css)
    |- _grid-name.scss  => 定义区域布局
    |- _grid.scss       => 开启 Grid Layout 布局，等分区域布局（通过 grid="col-* row-* 设置 * 取值为 number，范围 1~12"）
    |- _param.scss      => 全局变量（如需自定义，修改本文件即可）
    |- scss-grid.scss   => 主文件
```

## use

```html
<link rel="stylesheet" href="./dist/css/scss-grid.css">

<!-- 经典布局（header aside main footer）,从左至右，从上至下 -->
<div grid grid-name="header (aside main) footer" class="info">
  <div grid-header>header</div>
  <div grid-main>Main</div>
  <div grid-aside>Aside</div>
  <div grid-footer>Footer</div>
</div>
```

- `grid` => 开启 Grid Layout 布局
- `grid-name` => 指定布局方式（header、footer 默认高 60px，aside 默认高 150px, main 自动适配，区域与区域之间的间距默认为 1.5rem，值的写法应该遵循从上至下，从左至右原则，从上至下使用 `[]` 将区域名字括起来，区域名字使用空格相隔，从左至右使用 `()` 将区域名字括起来，区域名字使用空格相隔），以下为 `grid-name` 的可选值

  - `[header main]`

    ```
    ----------
    | header |
    ----------
    | main   |
    ----------
    ```

  - `[header main footer]`

    ```
    ----------
    | header |
    ----------
    | main   |
    ----------
    | footer |
    ----------
    ```

  - `(aside main)`

    ```
    ----------------
    | aside | main |
    ----------------
    ```

  - `[header (aside main)]`

    ```
    ----------------
    | header       |
    ----------------
    | aside | main |
    ----------------
    ```

  - `[header (aside [main footer])]`

    ```
    ------------------
    | header         |
    ------------------
    |       | main   |
    | aside |--------|
    |       | footer |
    ------------------
    ```

  - `(aside [header main])`

    ```
    ------------------
    |       | header |
    | aside |--------|
    |       | main   |
    ------------------
    ```

  - `(aside [header main footer])`

    ```
    ------------------
    |       | header |
    |       |--------|
    | asdie | main   |
    |       |--------|
    |       | footer |
    ------------------
    ```

  - `[header (aside main) footer]`

    ```
    ----------------
    | header       |
    |--------------|
    | asdie | main |
    |--------------|
    | footer       |
    ----------------
    ```

  - `[(aside [header main]) footer]`

    ```
    ------------------
    |       | header |
    | asdie |--------|
    |       | main   |
    |----------------|
    | footer         |
    ------------------
    ```

  - `[(asdie main) footer]`

    ```
    ----------------
    | asdie | main |
    |--------------|
    | footer       |
    ----------------
    ```