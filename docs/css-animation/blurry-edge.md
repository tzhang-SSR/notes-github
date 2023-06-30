# Blurry Edge Animation
如何使用CSS模糊div的边界从而使得两个div的边缘相互交融，然后进一步通过CSS animation创造出无限融合分离的loading动画

## Refernce Link
- https://www.bilibili.com/video/BV1Wj411Q74w/?spm_id_from=333.999.0.0

## Codepen
- https://codepen.io/MourningCat/pen/gOQMVoY

## 知识点
### filter
`filter`可以将模糊（blur）或者对比（contrast）等滤镜效果应用到元素上，主要用于调整图像，背景和边框的渲染
- https://developer.mozilla.org/zh-CN/docs/Web/CSS/filter

给元素添加`filter: blur(25px)`可以模糊边框，
但是如果再在父元素中`filter:contrast(50);`, 模糊效果又会变清晰，此时相邻的两个元素就会出现边框融合的情况

### animation
```css
.box1{
  animation: r1 0.8s ease-in-out infinite alternate;
}
/*   this is equivalent to: */
/*   animation-iteration-count: infinite; */
/*   animation-direction: alternate; */
@keyframes r1{
  from{
    transform: rotate(45deg) translateX(0px);
  }
  to{
    transform: rotate(-45deg) translateX(150px);
  } 
}
```
### animation-timing-function
- `ease-in-out`: 属于`animation-timing-function`的一个值，等同于 cubic-bezier(0.42, 0, 0.58, 1.0)，表示动画属性一开始缓慢变化，随后加速变化，最后再次减速变化。
- `ease-in`: 等同于 cubic-bezier(0.42, 0, 1.0, 1.0)，表示动画一开始较慢，随着动画的进行逐渐加速.
- `ease-out`: 等同于 cubic-bezier(0, 0, 0.58, 1.0)，表示动画一开始较快，随着动画的进行逐渐减速。

### animation-iteration-count
- `infinite`: 代表动画循环的次数，infinite即无限循环

### animation-direction
- `alternate`: 设置动画在正向和反向之间交替播放
- `normal`: 动画在循环中正向播发，默认值
- `reverse`: 动画在循环中反向播发