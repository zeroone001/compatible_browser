### 计算数组的极值
``` javascript
function smallest(array){                         
  return Math.min.apply(Math, array);             
}                                                 

function largest(array){                          
  return Math.max.apply(Math, array);             
}  

smallest([0, 1, 2.2, 3.3]); // 0

largest([0, 1, 2.2, 3.3]); // 3.3
``` 
### 迭代arguments
```javascript
function useCall() {
    [].forEach.call(arguments, function(val, key) {
        console.log(key, val)
    });
}

useCall('Bob Dylan', 'Bob Marley', 'Steve Vai');

//0 "Bob Dylan"
//1 "Bob Marley"
//2 "Steve Vai"

```
### 将arguments转为数组
```javascript
function transformToArray(arg){
  return Array.prototype.slice.call(arg);
}
```
###使用IIFE解决循环问题
```javascript
var funcs = [];

for (var i = 0; i < 10; i++) {
    funcs.push((function(value) {
        return function() {
            console.log(value);
        }
    }(i)));
}

funcs.forEach(function(func) {
    func();     // 从 0 到 9 依次输出
});
```
### 使用let解决循环问题
```javascript
var funcs = [];

for (let i = 0; i < 10; i++) {
    funcs.push(function() {
        console.log(i);
    });
}

funcs.forEach(function(func) {
    func();     // 从 0 到 9 依次输出
})
```
###理解map和parseInt
```javascript   
['1','2','3'].map(parseInt);
//[1, NaN, NaN]

['1','2','3'].map(function(x){return parseInt(x,10)});
//[1, 2, 3]
```
###微信内部修改document.title
```javascript   
function setTitle(title) {
  document.title = title;
  if (/ip(hone|od|ad)/i.test(navigator.userAgent)) {
    var i = document.createElement('iframe');
    i.src = '/favicon.ico';
    i.style.display = 'none';
    i.onload = function() {
      setTimeout(function(){
        i.remove();
      }, 9)
    }
    document.body.appendChild(i);
  }
}

setTitle("要修改的标题");
```
###判断一个值是否是对象
```javascript
function isObject(value){
  return value === Object(value);
}

isObject({}); // true
isObject(123);  // false
```

















