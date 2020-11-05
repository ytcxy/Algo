## Java 入门指南

### Java 程序基础操作

#### 基本数据类型

- 整数类型： byte short，int， long
- 浮点数类型：float，double
- 字符类型：char
- 布尔类型：boolean

| 类型   | 字节数 |
| ------ | ------ |
| byte   | 1      |
| short  | 2      |
| int    | 4      |
| long   | 8      |
| float  | 4      |
| double | 8      |
| char   | 2      |

如果需要传递一个数字，没有定义变量类型

```java
100  // 默认是 int 型

100L // 默认是 long 型

10.0 // 默认是 double 型

10.0f // 默认是 float 型
```

#### 数据运算

##### 整除 

如果除数为 0 时，运行时则会报错，但编译不会。

```java
int x = 25 / 3; // -> 8
```

##### 取余

```java
int y = 25 % 3; // -> 1
```

##### 溢出

整数的范围有限制，如果计算超出了范围，就会溢出，溢出不会出现错误，但是结果不可控。
所以要调整变量的类型，让数字再类型的范围内运算就可以了。

```java
System.out.println(2147483640 + 30); // -> -2147483626
System.out.println(2147483640L + 30L); // -> 2147483670
```

##### 简写运算符  

`+=`  `-=`  `*=`  `/=`

```java
x += 100; //  相当于 x = x + 100
x -= 100; //  相当于 x = x - 100
```

##### 自增，自减

++ 写在前面或者后面是有区别的， ++ 写在前面是先加1在引用x、 否则就是先引用x再加1.

```java
x++;  // x = x + 1;
x--;  // x = x - 1;
```

##### 位移运算

在计算机中，都是二进制的表示形式，比如，int 类型的整数 5 
`00000000 00000000 00000000 00000101 `
可以对整数进行位移运算

x 向左移动 y 位  即 x = x * $2^y$

x 向右移动 y 位   即 x = x / $2^y$

```java
int n = 5;
int a = n << 1; // 00000000 00000000 00000000 00001010 = 10  
int b = n << 2; // 00000000 00000000 00000000 00010100 = 20
int c = n >> 1; // 00000000 00000000 00000000 00000010 = 2 
```

##### 位运算

位运算是按位进行与、或、非和亦或的运算

```java
0 & 1 // 0
1 & 1 // 1
    
0 | 1 // 1

~0    // 1  按位取反
    
1 ^ 0 // 1
1 ^ 1 // 0    
```

##### 三目运算符

`b ? x : y`

##### 字符和字符串

`char ` 是基本的数据类型，它占两个字节。

`String` 是引用类型，

`String` 一旦确定就不能更改了。

```java
String s = "hello";
System.out.println(s);

s = "world";
System.out.println(s);

int len = s.length();

for (int i = 0; i < len; ++i)
    System.out.println(s.charAt(i));
```

这里变的不是字符串 `s` ， 变得是 `s` 的指向。

可以使用 `+` 来实现字符串的拼接。

```java
String s = "world!";
s = "hello " + s;
System.out.println(s);
```

##### 数组

```java
int[] vis;
vis = new int[4];  // 4 个大小的数组， 

int[] a = new int[19]; // 19 个大小的数组
```

所有数组的下标都是从 0 开始的

数组在内存地址上是连续的，所以就可以使用下标来取出具体的值。

知道了下标，也知道数组的起始位置，就可以推出来值在内存地址上的位置了。

![image-20201102110621091](https://gitee.com/ytcxyt/Images/raw/master/images/20201102110621.png)

假设内存内置的起始地址是从 0 开始的（实际上并不是）

这里我们开了一个5个大小的数组，数组在内存地址上的起始位置是2，

现在我们想要取数组中 2 位置的值， 那么对应在内存地址上的位置就是 $ 2 + 2 = 4$， 所以只要在内存地址4的位置取值就可以了。

数组的优点：可以O(1) 的取数，修改数。

数组的缺点：如果删除一个数的时候，需要删除位置后面所有的数整体前移一位。



##### 字符串数组

![image-20201102150633462](https://gitee.com/ytcxyt/Images/raw/master/images/20201102150633.png)



`names` 包含3个元素，每个元素指向了一个字符串对象。

如果修改，那就是修改指向。



### 流程控制

##### 输入和输出

```java
System.out.println("Hello World!!!"); // 普通输出
int x = 10;
System.out.printf("%.2f\n",1.0* x); // 格式化输出
```

| 占位符 | 说明                             |
| ------ | -------------------------------- |
| %d     | 格式化输出整数                   |
| %x     | 格式化输出十六进制整数           |
| %f     | 格式化输出浮点数                 |
| %e     | 格式化输出科学计数法表示的浮点数 |
| %s     | 格式化字符串                     |

```java
Scanner cin = new Scanner(System.in);
x = cin.nextInt();
y = cin.nextInt();  // 还有 nextDouble, nextLong ...
System.out.println(x + " " + y);
```



##### if 判断

```java
if (true) {
    
} else {
    
};
```

##### switch多重选择

```java
int option = 1;
switch (option) {
    case 1:
        System.out.println("Selected 1");
        break;
    case 2:
        System.out.println("Selected 2");
        break;
    case 3:
        System.out.println("Selected 3");
        break;
}
```

##### while循环

```java
while(true){
    
}
```

##### for循环

```java
int[] vis = new int[3];
for (int i = 0; i < vis.length; ++i)
    vis[i] = (int) (Math.random()*100);

for (int i = 0; i < vis.length; ++i)  // 下标循环
    System.out.println(vis[i]);

for (int val : vis) // for each 循环
    System.out.println(val);
```

我们有两种for循环的方式

- 直接访问下标
- 不需要访问下标，直接要数组每个元素的值。

##### break and continue

这两个关键字都是在循环里面用的。

break 是跳出当前循环，整个循环都不执行了。

continue 是当前循环提前结束，进行下一次循环。

```java
for (int i = 0; i < 5; ++i){
    if (i == 2) break;
    System.out.println(i); // 0 1
}

for (int i = 0; i < 5; ++i){
    if (i == 2) continue;;
    System.out.println(i); // 0 1 3 4
}
```

### 数组操作

##### 遍历数组

```java
for (int i = 0; i < vis.length; ++i)  // 下标循环
    System.out.println(vis[i]);

for (int val : vis)                   // for each 循环
    System.out.println(val);
```

##### 打印数组

遍历数组的时候，就可以打印数组的内容。

如果打印数组变量，得到的是数组的JVM中的引用地址：

所以可以使用 `Arrays.toString()` 方法来输出数组的内容。

```java
System.out.println(Arrays.toString(vis)); // [41, 96, 63]
System.out.println(vis);             //[I@12b3a41
```



### 常用工具类

#### Math

基本操作

```java
// 求绝对值
Math.abs(-10); // 10
Math.abs(-1.1); // 1.1

Math.max(10, 100); // 100
Math.min(10, 100); // 10

// 计算 x 的 y 次方
Math.pow(2, 3); //  2 的 3 次方 8
// 开根号
Math.sqrt(4); // 2

// 计算 e 的 x 次方
Math.exp(2); // 7.389

// 计算以 e 为底数的对数
Math.log(4); // 1.368

// 计算以 10 为底数的对数
Math.log10(100); // 2

// 三角函数
Math.sin(3.14); // 0.00159...
Math.cos(3.14); // -0.9999...
Math.tan(3.14); // -0.0015...
Math.asin(1.0); // 1.57079...
Math.acos(1.0); // 0.0

// 常量
double pi = Math.PI; // 3.14159...
double e = Math.E; // 2.7182818...
Math.sin(Math.PI / 6); // sin(π/6) = 0.5

// 随机数 x，  0 <= x < 1

Math.random(); // 0.53907... 每次都不一样
// 如果想 rand 一个 [min,max) 的一个数
double val = Math.random()*(max-min) + min;

```

#### Random

`Random` 用来创建伪随机数，所谓伪随机数，是指只要给定一个初始的种子，产生的随机数序列是完全一样的。

如果在创建 `Random` 实例时，如果不给定种子，就使用系统当前时间戳作为种子，每次运行的时候，种子不一样，生成的就不一样。

如果在创建 `Random` 实例时，给定一个固定的种子，就会得到一个完全确定的随机数序列。

```java
Random r = new Random();
System.out.println(r.nextInt(10)); // 生成一个[0, 10) 之间的int
```

#### BigInteger

**常量**

```java
BigInteger one = BigInteger.ONE;
BigInteger ten = BigInteger.TEN;
BigInteger zero = BigInteger.ZERO;
```

**构造函数**

```java
// 直接传入一个字符串
BigInteger x = new BigInteger("11000"); 

// 前面时字符串， 后面是基数
BigInteger y = new BigInteger("110",2); // 6 
```

**常用方法**

```java
BigInteger x = new BigInteger("11000");
BigInteger y = new BigInteger("110",2); // 6
BigInteger z = new BigInteger("10");

System.out.println(x.intValue());
System.out.println(y.intValue());

x = x.add(y);
x = x.subtract(y);
x = x.multiply(y);
x = x.divide(y);

x = x.mod(y);
x = x.pow(y.intValue());
x = x.modPow(y,z); // x ^ y % z
x = x.negate();    // 取反
x = x.abs();       // 绝对值
x = x.gcd(y);
x = x.and(y);
x.compareTo(y); // x < y : -1, x == y : 0   x > y : 1
x.equals(y);   //
x = x.max(y);  // 返回 max(x,y)
x = x.min(y);  // 返回 min(x,y)
```

### Java集合

- `Queue`
- `Deque`
- `LinkedList`
- `ArrayList`
- `Stack`
- `Map`
- `Set`



##### `ArrayList` 的常用方法

`LinkedList` 方法也一样。只不过效率不一样

```java
// ArrayList
// List<String> list = new LinkedList<>();
List<String> list = new LinkedList<>();

list.add("ytc"); // 添加
list.add("sxy");
list.add("me");
list.add("yu");
list.add("ttt");
System.out.println("list[0] = " + list.get(0)); // 查询
System.out.println("size is " + list.size());   // 元素个数
System.out.println("is empty? " + list.isEmpty()); // 是否为空
System.out.println("is contains yy? " + list.contains("yy")); // 查询是否存在
System.out.println("index of ytc? " + list.indexOf("ytc")); // 查询元素位置
list.set(0, "tao");  // 元素覆盖
list.remove("me");  // 元素删除
list.remove(2);  // 指定位置元素删除

for (String val : list)
    System.out.println(val);
list.clear();  // 清空
```

##### `Queue` 的常用方法

LinkedList 类实现了 Queue 接口，因此我们可以把 LinkedList 当作Queue来使用

 add， remove，element 方法会抛异常。（添加，查看并删除，查看）

offer，poll，peek    方法不会抛异常。      （添加，查看并删除，查看）

```java
// Queue
Queue<String> queue = new LinkedList<>();
queue.offer("f");
queue.offer("g");
queue.offer("a");
queue.offer("b");
queue.offer("c");

for (String val : queue)
    System.out.println(val);

System.out.println("poll " + queue.poll()); // 返回第一个元素，并弹出
System.out.println(queue.peek());  // 返回队首
System.out.println(queue.element()); // 返回队首
System.out.println(queue.size());   // 队列的大小
System.out.println(queue.isEmpty()); //  队列是否为空
 
queue.clear();
```

##### `Deque` 的常用方法

Deque 时 Queue 的子接口，所以可以使用 Queue 的方法。

- 插入  add / offer

  - 异常不安全

    void add() | addFirst() | addLast() 

  - 异常安全

    boolean offer()  |offerFirst() |offerLast() 

- 查看并删除

  - 异常不安全

    E remove | removeFirst | removeLast()

  - 异常安全

    E poll() | pollFirst() | pollLast();

- 查看

  - 异常不安全

    E element() | getFirst() | getLast()

  - 异常安全

    E peek() | peekFirst() | peekLast()





也可以使用 `Deque` 来实现 `Stack` 的操作。

- void push();   // void addFirst()
- E pop() ;      // E removeFirst

```java
// Stack
Deque<String> deque = new ArrayDeque<>();
deque.push("yyy");
deque.push("aaa");
deque.push("bbb");
System.out.println(deque.pop());
deque.clear();
System.out.println(deque.isEmpty());
```



##### `Map` 的常用方法

```java
// Map
Map<String, String> map = new HashMap<>();
map.put("1", "ytc");
map.put("2", "sxy");
map.put("3", "yu");
map.put("4", "tc");
System.out.println(map.get("3"));
map.remove("1"); // 删除一个键值对

for (String key : map.keySet()) // 遍历
    System.out.println(key + " " + map.get(key));

for (Map.Entry<String, String> entry : map.entrySet()) // 遍历
    System.out.println(entry.getKey() + " " + entry.getValue());


System.out.println(map.size());
map.clear();
System.out.println(map.isEmpty());
```

##### `Set` 的常用方法

```java
// Set
Set<String> set  =new HashSet<>();
set.add("1");
set.add("2");
set.add("3");
set.add("4");
System.out.println("size of set : " + set.size());
for (String val: set)
    System.out.println(val + " ");
System.out.println("contains 4 ? " + set.contains("4"));

set.remove("2");

set.clear();

System.out.println(set.isEmpty());
```

