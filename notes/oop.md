# JS OOP (Prototype-based)

[TOC]

----


> ES6 後支援 class 語法
> 以下 JS OO 概念不涉及 ES6 新語法



## OOP 懶人包

* 物件導向程式設計 (Object-oriented programming, OOP)
* 本質：
  * 是一種使用 abstraction 概念表達現實世界的程式設計方式
  * OOP 運用數個先前所建立的技術所組成，包含模組化 (modularity)、多型 (polymorphism) 以及封裝 (encapsulation) 
* 優點：
  * OOP 提出了一個更有彈性且易於維護的設計方法
  * 由於 OOP 強調模組化，因為物件導向的程式碼變的較為容易開發且易於理解
  * 廣泛被許多大型軟體工程所採用


----

## JS OOP (Prototype-based)

* JavaScript 是一個 **以雛型為基礎 (Prototype-based)** 的程式設計語言 (或更準確的說是以雛型為基礎的腳本語言)
  * 是一種不使用類別的物件導向程式設計模式
  * 使用了函數來當做類別 (Class) 的建構子 (Constructor)
  * 它採用了複製的模式而非繼承
  * 又稱作無類別 (Classless)、雛型導向 (Prototype-oriented) 或以實例為基的程式語言 (Instance-based programming)


----

## Examples

### Example 1: new Function 寫法


````js
function Car(_color){
  this.color = _color;
}
var c1 = new Car("Green");
console.log(c1);			// Car {color: "Green"}
console.log(c1.color);		// Green

// 以下寫法類似 new Car() 效果
var c2 = (function(){
  var _new = { constructor: Car, __proto__: Car.prototype };
  _new.constructor("Red");
  return _new;
})();
console.log(c2);			// Car {constructor: ƒ, color: "Red"}
````





### Example 2: function.prototype 寫法

Ref: https://www.zhihu.com/question/20289071



````js
function cat(){}
cat.prototype = {
	food:"fish",
	say: function(){
    	console.log("I love "+this.food);     
    }
}

var blackCat = new cat;
blackCat.say(); // I love fish
````





### Example 3: 利用閉包模擬 OO 效果

Refer to: Closures (閉包) - 利用閉包模擬 OO 效果



----

## FP (Functional Programming)

ref: http://www.codedata.com.tw/social-coding/paradigm-shift-to-functional-programming/

### 什麼是 Functional Programming

* 一種開發典範，只需要給我處理後的結果，不需要過問結果如何而來
* 例如：數學函式的 abs() ，回傳絕對值
* 以前是處理數學函數計算，又以 λ演算 (λ calculus) 為基礎
* 如果之前沒接觸過 FP 不需太在意，有時候已經默默在用 FP 帶來的一些功能



### Why Functional Programming

* 平行化與非同步不論在任何開發上面，都是比較難處理的部分，複雜度高的邏輯，若加上 FP 的特性來處理這類複雜的問題，可以把邏輯表達的較為易懂。
* OOP (Object-oriented programming) 教我們基本的單位就是 Class（類別），使用 Real World（真實世界）的角度去思考對應物件與方法，與 FP 所描述的方式大不相同。
* 如果轉換到 FP，OOP 上面許多的 Design Patterns 雖然不是特別的重要，重點放在於處理資料流上面，使得開發者更能專注問題所在。



### FP Basic Functions

* FP 有些特性我們必須熟悉，以及有一些好用的基礎函式，例如高階排序函式 (Higher-Order Functions)，底下我們舉三個基本常用的函式：
  * map: 尋訪每個元素，加以處理，並且回傳處理後的元素。
  * filter: 回傳 布林值，以決定是否處理該元素。
  * reduce: 尋訪每個元素，依序組合元素，轉換成結果，丟給下個元素運算組合，然後產生最終組合的結果。



## References

* [JavaScript 物件導向介紹](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript)
* [深入了解物件模型](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Guide/Details_of_the_Object_Model)