vue学习笔记，比较基础。
# mvc 和mvvc的区别
  - mvc是后端概念：model、view、controller
  - mvvc是前端概念： Model、View、ViewModel
# 最简单的vue代码段
  ```
    <div id="welcome">
        <p>{{ msg }}</p>
    </div>
    <script>
        var vm = new Vue({
            el: '#welcome',
            data: {
                msg: '欢迎来到我的世界'
            },
            methods:{}
        });
    </script>
  ```
# vue对象属性
  - el：指定vue对象要控制的区域。
  - data：data对象定义了控制区域中要用到的数据。
  - methods: 自定义方法。

# vue指令
## v-clock
  - 用于解决屏幕闪动的问题。
  - 如果网络较慢，网页还在加载vue.js，导致vue来不及渲染，这时页面展示的就是源代码。
  ```
  <!-- 元素上加 v-cloak属性 -->
  <p v-cloak>
      {{ msg }}
  </p>
  
  <!-- 样式 -->
  <style>
      [v-cloak] {
        display: none
      }
  </style>
  ```
## v-text 和 v-html
  - v-text用vue对象中的值覆盖元素内容
  - v-html区别于v-text的是：v-html绑会将内容解析为html，而v-text仅解析为普通文本。
  ```
  <div id="app">
        <p v-text="msg">========</p>
  </div>
  
  var vm = new Vue({
            el: "#app",
            data: {
                msg: 'i have a gift'
  }});
  ```
## v-bind
  - 元素属性可用v-bind绑定vue对象的属性
  - v-bind:arrtribute  可以缩写为  :attribute
```
    <div id="app">
        <input type="button" :value="msg">
    </div>
    
    var vm = new Vue({
            el: "#app",
            data: {
                msg: 'i have a gift'
            }
    });
```
## style属性绑定
  可以把样式定义在vue对象中,用v-bind:style引用
```
    <!-- 内联样式绑定 -->
    <!-- v-bind <h1 :style="{color:'red', 'font-weight':400}"> -->
    <!-- v-bind 中使用vue中的data 对象-->
    <!-- 数组-->
    <div id="app">
        <h1 :style="[h1style1, h1style2]">
            我很帅！！
        </h1>
    </div>
```
## class属性绑定
  类似style属性绑定
  ```
    <!-- 原生 <h1 class="red italic thin"> -->
    <!-- v-bind 直接传数组 <h1 :class="['red','italic','thin','active']"> -->
    <!-- v-bind 中使用三元表达式 <h1 :class="['red','italic','thin',flag ? 'active' : '']"> -->
    <!-- v-bind 中使用对象 <h1 :class="{red:true,italic:true,thin:true,active:true}"> -->
    <!-- v-bind 中使用对象 对象定义到vue的data属性中 -->
  ```

## v-on
    - v-on 提供事件绑定
    - v-on:event 可以缩写为 @event
```
    <div id="app">
        <input type="button" value="这个一个button" @click="alert">
    </div>
    var vm = new Vue({
            el: "#app",
            methods: {
                alert: function () {
                    alert("哈哈哈哈哈");
                }
            }
    });
```

## v-model
   双向数据绑定
   ```
    <div id="app">
        <input type="text" v-model="msg">
        <br/>
        <input type="text" :value="msg">
    </div>
    
    var vm = new Vue({
            el:"#app",
            data:{
                msg:"我好帅哦"
            }
    });
   ```
## v-for
   - 遍历原生类型数组
   - 遍历对象数组
   - 遍历对象的属性和值
```
    <div id="app">
        <p v-for="(item, i) in list">索引{{i}}, 值{{item}}</p>
        <p v-for="(user, i) in users"> 第{{i}}个user的id是{{user.id}},name是{{user.name}}</p>
        <p v-for="(val, key) in user"> user对象的属性{{key}}的值是{{val}}</p>
        <p v-for="count in 10">这是第{{count}}个数字</p> <!-- 从1开始 -->
    </div>
```
## v-if 和 v-show
    - v-if： 用删除和创建dom元素的方法实现
    - v-show： 用 display:none 属性实现
```
    <div id="app">
        <input type="button" value="reverse" @click="reverse">
        <!-- 用删除和创建元素实现 -->
        <h3 v-if="flag">天空很蓝</h3>
        <!-- 用display:none style属性实现 -->
        <h3 v-show="flag">天空很蓝蓝蓝</h3>
    </div>
```
# 事件修饰符
   默认行为冒泡,可以有下面选项
   - .stop 阻止冒泡
   - .prevent 阻止元素的默认行为
   - .capature 事件捕获,不是太清楚。
   - .self 仅当事件发生在元素自身时有效
   - .once 绑定的事件只执行一次

# 写在最后
  - 后端开发一枚，学前端是为了能够做更好玩的事情。
  - 前端的学习笔记都放在这个仓库：https://github.com/pepper-0611/qianduan
  - 在找工作的同学可以找我内推(看个人介绍)