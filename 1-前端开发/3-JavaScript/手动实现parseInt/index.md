# 手动实现parseInt

## parseInt是什么？
### 定义
把字符串转换成数值的过程。
详细一些就是：将字符串形式表示的radix进制数，转换成十进制数值。

### 用法
`parseInt(string, radix)`
1. string 要被解析的字符串，字符串前后的空白符会被忽略。如果非字符串，则将其转成字符串(toString)。
2. radix(optional) 字符串的基数，取值范围是[2, 36]。undefined、0或缺省的情况下：
    
    (1) 字符串以"0x"/"0X"开头，则基数为16；
    
    (2) 字符串以"0"开头，则基数是8/10，具体由浏览器决定。es5规定是10，但是总有浏览器要与众不同，所以最好始终给定radix的值；
    
    (3) 其他情况，默认基数都是10。
    
    如果radix的值不满足以上条件，parseInt将返回NaN。

### 注意
如果字符串无法被转换为数值，返回值为NaN。可能情况如下：
1. 字符串的第一个字符不是数值类型，比如parseInt("a123")返回值为NaN；
2. 字符串中的数值并不是radix进制数，比如parseInt("321",3)返回NaN；

## 如何实现？
```javascript
function parseInt(str, radix) {
    //检查str参数
    if (typeof str !== "string" && typeof str !== "number") {
        return NaN;
    }
    //检查radix参数
    if (radix && (typeof radix !== "number" || radix < 2 || radix > 36)) {
        return NaN;
    }
    str = String(str).trim();
    var temp = radix ? str.match(/^(-?)([0]?)(\d+)|(-?)([0]?[xX]?])([0-9a-fA-F]+)$/)
}
```


