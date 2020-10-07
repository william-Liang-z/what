### 基础

#### 定位

1. 默认情况: 盒子模型.top/bottom/left/right不生效.

2. relative. top/left/right/bottom表示远离这个方向的距离. 如top: 50px表示相对原来的位置是向下偏移50px. relative会保留原来的物理空间.

3. absolute. 绝对定位. 基于上一个已经定位的父元素(即要设置position属性的父元素, 一直找到body为止). top/left/right/bottom表示相应方向与上一个已定位的父元素的距离. top: 50px表示距离上方50px;

4. fix. 脱离文档流. 定位只窗窗口有关.

5. float. float不是position的值, 方式为float: left/ float: right. 脱离文档流, 会向左或者向右浮动, 直到遇到边界或者另一个浮动元素边框. 

   



#### 颜色

1. 颜色表示方式: 
   * 英文(如green, blue)
   * 十六进制, 如#FFF, #FFFFFF(只能是3位或者6位)
   * rgb, 三原色, 每个颜色用0-255表示. 如rgb(255, 0, 0). 更高级有个rgba, a表示透明度. 范围为0-1, 为0时透明.
   * hsl, 类似rab, 要设置三个值. 第一个指定颜色, 0(360)为红色, 120为绿色, 240为蓝色. 第二个值为百分比形式, 表示饱和度, 0表示灰色,100显示原来颜色; 第三个也是百分比形式, 表示亮度. 0为黑色, 100为白色. 显示正常颜色为50. hsl也对应有个hsla.
2. 线性渐变. linear-gradient. 第一个值变化方向, 0deg表示自底向上渐变, 90deg为从左到右渐变.(相当顺时针时针转动). **默认值为180deg**, 即自顶向下渐变. 之后的任意个参数表示渐变的起止颜色. (linear是background的值, 不是属性.) 颜色参数可以以空格+位置的形式指定颜色持续区间, 例如: (0deg, blue 100px 120px, yellow 80%).
3. 重复线性渐变. repeat-linear-gradient. 类似于linear-gradient, 第一个参数为角度. 但后面的参数比较复杂, 以颜色+空格+位置的形式, 如blue 0px. 参数表示开始渐变的颜色和渐变开始/结束的位置. 



#### 形状大小

##### transform

1. scale: 放缩. 传入放缩倍数. 如transform: scale(1.1)表示放大1.1倍.
2. skewX/skewY: 绕X轴/Y轴旋转一定角度, 产生三维的视觉效果. 对X来说, 从左视图看, 是顺时针方向旋转. 对Y来说是俯视图为顺时针方向旋转.
3. rotate(). 顺时针转过一定角度, 如transform: rotate(45deg)

##### opacity

设置透明度

##### display

1. block. 行内元素作为块级元素显示.

2. inline-block: 块级元素作为行内元素显示.

3. flex. 弹性布局. 设置这个属性的元素会成为弹性容器. 

   * 设置弹性容器的flex-direction属性, 可以轻易改变子元素的排列方向和顺序. 可选值有: row/column/row-reverse/column-reverse. (默认值为row)

   * justify-content. 有五个可选值. center: 子元素居中显示; flex-start/flex-end: 紧贴最前/最后的位置(由flex-diraction确定); space-between: 第一个和最后一个紧贴边界, 中间的元素均匀分布; space-around: 均匀分布, 但是第一个/最后一个元素到边界的距离为间隔的一半.

   * align-items. 有点类似justify-content, 不过后者是顺着flex-direction方向的调整, 前者是在与之垂直的方向进行调整. 例如当前flex-direction的方向是row, align-items调整的是竖直方向.

     可选值有五个. center在对应方向上子元素居中显示. flex-start/flex-end: 在对应方向子元素在开始/结束处显示. stretch: 对应方向上填满容器. baseline: 对应方向上与基线对齐.

   * flex-wrap. 默认情况下, 如果子元素没有内容, 但是显示的大小超出父容器的大小, 父容器会将其压缩到一定大小(如果有内容则不会压缩, 会撑大父容器). 使用flex-wrap可进行换行. 可选值有三个: nowrap, 默认不换行. wrap, 多余的部分进行换行; wrap-reverse, 换行, 但是是从下网上填充. 

   * flex-shrink: 当多个子容器被压缩时使用, 数值表示被压缩的倍数. 3表示原来的1/3. 但是如果另一个元素也被压缩了. 还是会自动填充留空的部分. 

   * flex-grow. 与flex-shrink相对, 便是放大倍数. 可以理解成全部的flex-grow数值加起来作为分母, 单个元素的这个值作为分子, 表示这个元素占用长度.

   * flex-basis. 设置flex-shrink和flex-grow调整前的初始大小.

   * flex. 作为一个属性, 可以简略表示flex-grow, flex-shrink, flex-basis. 默认值为flex: 0 1 auto;

   * order: 在子元素中设置, 表示子元素的顺序. 数值越大越靠后. 

   * align-self. 在子元素中设置, 设置子元素的对齐方式. 可选值与align-items一样, 而且设置align-self会清除当前子元素的align-items;
   
4. grid. 网格元素. 设置元素这display为这个值的时候, 该元素也会添加一些相应的网格特性. 添加后可以设置以下一些属性. 

   * grid-template-columns: 设置列的宽度. 有多少个宽度表示有多少列. 例如, grid-template-columns: 50px 50px表示有两列, 每列宽度为50px; 单位也可以设置为`fr`, 所有带fr单位的列共享父元素剩下 的宽度空间. 用repeat函数可以减少代码手写量. 第一个参数为重复次数, 之后的参数为重复的内容, 例如`repeat(2,10px,20px) 30px`相当于`10px 20px 10px 20px 30px`. 另外还有一个函数`minmax` , 表示最小和最大的长度. 这个函数和其他列宽值设置方法相同, 设置一个列并且可以作为repeat的参数. 

     有了minmax就方便了使用repeat创建弹性布局. repeat第一个参数传入auto-fill, 网格元素就会在之后的参数的限制范围内自由拉伸/换行. auto-fit类似于auto-fill, 不过后者会创建空网格补全, auto-fit不会. auto-fit会选择合适的大小填充.

   * grid-template-rows: 设置行高. 值和上面设置列宽类似, 不过如果行数大于设置的行数, 则只会设置前几个行的高度(就是说不会换行), 后几个保留原样式.

   * grid-column-gap/grid-row-gap: 设置每一列/每一行之间的间隔(开始和结束还是紧贴边界). 有个简便写法, grid-gap. 传入两个参数, 分别表示间隙行高和列宽. 例如grid-gap: 10px 20px. 如果只有一个参数, 则行间隙和列间隙大小相等. 

   * grid-column. 这个属性是应用到子元素的, 表示某个子元素的占用的列宽. 以分数的形式, 如1/3表示从第一条竖线到第三条竖线之间的列宽(也就是占用前两列). grid-row也是类似的作用. (对grid-template-columns和grid-template-rows创建的空行也会有相应的line).

   * justify-self.应用到子元素. 默认情况下, 这个属性的值为stretch, 每个子网格充满整个网格. 也就是说如果网格比元素大, 子元素会充满整个表格. 可以设置start/center/end恢复原来的大小, 并选择元素在网格中的位置. justify-self只能设置水平方向的位置, 垂直位置有个对应的align-self.

   * justify-items/align-items. 在父元素中设置, 对左右子元素应用justify-self/align-self.

   * grid-template-area. 父元素设置. 定义表格区域. 用字符串的形式表示, 每一行用一个字符串, 字符串里面的每个单元格用空格分开, 使用自己定义的命名, 例如`"a a a" "b b b"`, 空单元格用`.`表示. 直接应用这个的表格并没有什么变化, 之后还有设置一些属性.

   * grid-area. 在子元素中设置, 而且一般要事先设置好grid-template-area, 对应的自定义的变量名应该是在同一行或同一列(可以占多行多列, 但必须形成一个矩形, 不能多余或空缺). 设置形式如: `child1{grid-area: my-var;}`, 属性值为在父类grid-template-area中自定义的名称, 例如上面的a和b. **grid-area**也可以不设置grid-template-area直接选取占用的区域. 值可以用四个数值三个斜杠表示, 分别表示开始水平线/开始垂直线/结束水平线/结束垂直线, 类似grid-column/grid-row. 

#### 阴影

box-shadow. 设置的属性值依次为

1. offset-x: x方向偏移量, 正数为向右偏移
2. offset-y: y方向偏移量, 正数向下偏移.
3. blur-radius: 表示模糊程度, 数值越大越模糊. 模糊半径增大背景图像也会相应增大.
4. spread-radius: 扩大的半径. 为0时大小与原图像大小一致.

#### 盒子模型

CSS的盒子模型由内到外是content, padding, border, margin. 但有些不同的场合需要改变盒子的范围, 使得我们需要的盒子只用到content或者padding. 常见值为: content-box, padding-box, border-box. 

1. background-clip. 默认值为border-box, 背景会延申到边框下面(边框设置为虚线或者半透明可以看到效果). 只能设置
2. background-position. 使用背景图片时用到, 定位图片的位置在top,left,right, bottom中的基准位置. 默认是padding-box, 即图片对应到padding盒子的边界.





#### 伪类

##### 常见伪类

1. `:hover`. 鼠标放上去后的样式.
2. `:before/:after`. 在选中的元素之前/之后加入一个**行内元素**, 并设置相应样式. 设置的属性里面的content可以是空字符串, 但是不能省略content不写, 否则不会显示任何内容. 可以插入图片等内容.



#### 动画

##### animation

在对应的元素中设置相应的animation属性, 来定义动画的持续时间等效果. 在@keyframes中添加动画转换的起止样式.@keyframes后接变量名, 再设置相应样式, 例如: 

```css
@keyframes var-name{
    0%{
        color: blue;
    }
    50%{
        color: yellow;
    }
    100%{
        color: red;
    }
}
```

这段可以在持续时间内先由蓝色变成黄色, 之后再变成红色. (0%还是不要设置的好, 从一开始的样式到0%的样式还是有个跳变)



animation共有八个属性: 

1. `animation-frame`, 值为自定义的变量名. 

2. `animation-duration`值为动画持续时间.

3. `animation-fill-mode`. 值为forword时, 表示动画结束后保持最终样式.

4. `animation-iteration-count`. 表示循环次数, infinite为一直循环下去. 

5. `animation-timing-function`. 运动形式, 一共有四个可取值, 默认为ease, 开始和结束时速度较慢, 运动中间速度较快. linear为匀速变换; ease-in低速开始高速结束; ease-out高速开始低速结束. 

   这个属性的值可以设置成Bezier曲线的形式, cubic-bezier(x1,y1,x2,y2). 原理: 贝塞尔曲线是一个位移-时间图, 不过x轴表示位移, y轴表示时间. 贝塞尔的曲线通过样条插值获得, 两个固定点(0,0)和(1,1). 对应斜率为p0-p1和p2-p3连线的斜率. x1,x2取值范围为0-1, y任意.







### 设备兼容

#### 响应式web

响应式web是一种自适应不同尺寸设备的设计方式.

* 根据屏幕宽度/高度返回内容. 使用media设置最大/最小宽度/高度:

  ```css
  /*当屏幕高度小于600px是应用里面的样式*/
  @media(max-height: 600px){
      p{
          font-size:12px;
      }
  }
  ```

* 图片自适应: 设置高度为auto, 最大宽度为100%适应父容器(不能超出父容器). 设置为块级元素. 

* 图片适应高分辨率设备: 大小应为原图的一半.

* 根据视口大小确定单位: vh/vw/vmin分别表示当前视口的宽度百分比/视口高度百分比/视口宽度与高度的较小值. 