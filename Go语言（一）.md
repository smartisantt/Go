## Go语言





![img](https://www.runoob.com/wp-content/uploads/2015/06/go128.png)

#### 简介

Go属于编译型语言，其相对于Python解释型语言而言，编译型语言的首先将源代码编译生成机器语言，再由机器运行[机器码](https://baike.baidu.com/item/机器码/86125)（[二进制](https://baike.baidu.com/item/二进制/361457)）。

Go 语言被设计成一门应用于搭载 Web 服务器，存储集群或类似用途的巨型中央服务器的系统编程语言。

对于高性能分布式系统领域而言，Go 语言无疑比大多数其它语言有着更高的开发效率。它提供了海量并行的支持，这对于游戏服务端的开发而言是再好不过了。



第一个Go程序 hello.go文件

```go
package main

import "fmt"

func main() {
  fmt.Println("Hello, World!")
}
```

***注意：`{`不能单独放在一行。*******



```go
package main

import "fmt"

func main() 
{ // !!这会报错
  fmt.Println("Hello, World!")
}
```



要执行Go语言代码可以使用`go run hello.go`命令。

此外我们还可以使用`go build hello.go`命令生成二进制文件。



程序解读：

1. 第一行代码`package main`定义了包名。你必须在源文件非注释的第一行指明这个文件属于哪个包。如：`package main`表示一个可独立了执行的程序，每个Go应用程序都包含一个名为main的包。
2. 下一行`import "fmt"`告诉Go编译器这个程序需要使用fmt包（的函数，或其他元素），fmt包实现了IO的函数。
3. 下一行`func main()`是程序开始执行的函数。main函数是每一个可执行程序所必须包含的，一般来说都是在启动后第一个执行的函数（如果有init()函数则会先执行该函数）
4. 下一行`fmt.Println(...)`可以将字符串输出到控制台，并在最后自动增加换行符合\n。
5. 当标识符（包括常量、变量、类型、函数名、结构字段等等）以一个**大写字母开头**，如：Group1，那么使用这种形式的标识的对象就可以被外部包的代码所使用（客户端程序需要先导入这个包），这被称为导出（像面向对象的public）；标志符如果是以小写字母开头，则对包外是不可见的，但是他们在整个包的内部是可见并且可以用的（像面向对象语言中的protected）。





#### 注释

```go
// 这是一个注释
/*   

这是一个多行注视
这是一个多行注视

*/
```





#### 标识符

标识符用来命名变量、类型等程序实体。一个标识符实际上就是一个或是多个字母(A~Z和a~z)数字(0~9)、下划线_组成的序列，但是第一个字符必须是字母或下划线而不能是数字。

go语言关键字25个
| 关键字   | 关键字      | 关键字 | 关键字    | 关键字 |
| -------- | ----------- | ------ | --------- | ------ |
| break    | default     | func   | interface | select |
| case     | defer       | go     | map       | struct |
| chan     | else        | goto   | package   | switch |
| const    | fallthrough | if     | range     | type   |
| continue | for         | import | return    | var    |





golang 的fmt 包实现了格式化I/O函数，类似于C的 printf 和 scanf。

| 占位符 | 说明             |
| ------ | ---------------- |
| `%v`   | 相应值得默认格式 |
| `%t`   | 占位符           |
| `%d`   | 十进制           |
| `%f`   | 有小数点而无指数 |
| `%s`   | 输出字符串       |
| `%p`   | 指针             |
| `%e`   | 科学计数法       |



#### 数据类型

- 布尔型（true, false)
- 数字类型（Go 语言支持整型和浮点型数字，并且支持复数，其中位的运算采用补码。）
- 字符串类型
- 派生类型



##### 数字类型

| 代码     | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| `uint8`  | 无符号 8 位整型 (0 到 255)                                   |
| `uint16` | 无符号 16 位整型 (0 到 65535)                                |
| `uint32` | 无符号 32 位整型 (0 到 4294967295)                           |
| `uint64` | 无符号 64 位整型 (0 到 18446744073709551615)                 |
| `int8`   | 有符号 8 位整型 (-128 到 127)                                |
| `int16`  | 有符号 16 位整型 (-32768 到 32767)                           |
| `int32`  | 有符号 32 位整型 (-2147483648 到 2147483647)                 |
| `int64`  | 有符号 64 位整型 (-9223372036854775808 到 9223372036854775807) |



##### 浮点类型

| 代码         | 说明           |
| ------------ | -------------- |
| `float32`    | 32位浮点数     |
| `float64`    | 64位浮点数     |
| `complex64`  | 32位实数和虚数 |
| `complex128` | 64位实数和虚数 |



Go语言类型转换

语法格式：

```go
type_name(expression)
```







#### go语言变量

Go 语言变量名由字母、数字、下划线组成，其中首个字符不能为数字。**不能是关键字或者预定义字符。**



#### 变量声明

##### 1、第一种

```go
var 变量名 变量类型
var 变量名1,变量名2 变量类型
```

如果没有初始化，则变量如果是`int`类型，则默认为0，如果是`bool`类型，则默认是`false`



##### 2、第二种

根据值自行判定变量类型

```go
var 变量 = 值
```



##### 3、第三种

省略 var, 注意` :=` 左侧是没有声明新的变量格式：

```go
新变量 := 值
```

`=`和`:=`的区别

`=` 使用必须使用先var声明例如。

`:=`是声明并赋值，并且系统自动推断类型，不需要var关键字。只能被用在函数体内，而不可以用于全局变量的声明与赋值。

如果在相同的代码块中，我们不可以再次对于相同名称的变量使用初始化声明。

如果你声明了一个**局部变量**却没有在相同的代码块中使用它，会得到编译错误。



#### go语言常量



```go
// 显示定义
const b string = "abc"
// 隐式定义
const b = "abc"
// 多个相同类型
const c_name1, c_name2 = valueq, value2
// 枚举
const (
	Unkonw = 0
	Female = 1
	Male = 2
)
```



#### go语言运算符

| 运算符 | 描述 |
| ------ | ---- |
| `+`    | 相加 |
| `-`    | 相减 |
| `*`    | 相乘 |
| `/`    | 相除 |
| `%`    | 求余     |
| `++`   | 自增 |
| `--`   | 自减 |



#### 关系运算符

`==` ,`!=` ,`>=`,`<=`,`<`,`>`



#### 逻辑运算符

`&&`,`||`,`!`



#### 位运算符

`&`,`|`,`^`,`<<`,`>>`



#### 赋值运算符

`=`,`+=`,`-=`,`*=`,`/=`,`%=`,`<<=`,`>>=`,`&=`,`^=`,`|=`



#### 其他运算符

`&` 返回变量存储地址 ，`&a`给出变量的实际地址

`*` 指针变量，`*a`是一个指针变量，指针变量保存的是一个地址值，会分配独立的内存来存储一个整型数字。当变量前面有 ***** 标识时，才等同于 **&** 的用法，否则会直接输出一个整型数字。

```go
func main() {
	var a int = 4
	var ptr *int
	ptr = &a

	println("a的值为", a);	// a的值为 4
	println("*ptr的值为", *ptr) // *ptr的值为 4
	println("ptr的值为", ptr)  // ptr的值为 0xc00002ff78
}
```





#### 条件语句

| 语句        | 描述                                                         |
| ----------- | ------------------------------------------------------------ |
| if语句      | **if 语句** 由一个布尔表达式后紧跟一个或多个语句组成。       |
| if else     | **if 语句** 后可以使用可选的 **else 语句**, else 语句中的表达式在布尔表达式为 false 时执行。 |
| if 嵌套语句 | **if** 或 **else if** 语句中嵌入一个或多个 **if** 或 **else if** 语句。 |
| switch 语句 | **switch** 语句用于基于不同条件执行不同动作。                |
| select 语句 | **select** 语句类似于 **switch** 语句，但是select会随机执行一个可运行的case。如果没有case可运行，它将阻塞，直到有case可运行。 |

*注意：Go 没有三目运算符，所以不支持* **?:** *形式的条件判断。*



#### 循环语句



for循环有3种格式：

`for init; condition; post {}`

`for condition {}`

`for {}` 

- init： 一般为赋值表达式，给控制变量赋初值；
- condition： 关系表达式或逻辑表达式，循环控制条件；
- post： 一般为赋值表达式，给控制变量增量或减量。



```go
func main() {
	var b int = 15
	var a int

	numbers := [6]int{1, 2, 3, 5}

	for a := 0; a < 10; a++ {
		fmt.Printf("a的值为：%d\n", a)
	}

	for a < b {
		a++
		fmt.Printf("a的值为：%d\n", a)
	}

    // for 循环的 range 格式可以对 slice、map、数组、字符串等进行迭代循环。
	for i, x := range numbers {
		fmt.Printf("第 %d位 x的值 = %d\n", i,x)
	}
}
```



##### 无限循环

```go
for true  {
        fmt.Printf("这是无限循环。\n");
    }

// 或者
for {
  fmt.Printf("这是无限循环。\n")
}
```





#### 循环控制语句	

| 控制语句   | 描述                                             |
| ---------- | ------------------------------------------------ |
| `break`    | 经常用于中断当前 for 循环或跳出 switch 语句      |
| `continue` | 跳过当前循环的剩余语句，然后继续进行下一轮循环。 |
| `goto`     | 将控制转移到被标记的语句。                       |





### 函数

函数格式定义如下：

```go
func function_name( [parameter list] ) [return_types] {
   函数体
}
```



例：求两个数最大的数

```go
package main

import (
	"fmt"
)


func main() {
	var a int = 22
	var b int = 10
	var ret int

	ret = max(a, b)
	fmt.Printf("最大的是:%d\n", ret)
}


func max(num1, num2 int) int {
	var result int

	if(num1 > num2) {
		result = num1
	} else {
		result = num2
	}
	return result
}
```



#### 函数的参数

调用函数，可以通过两种方式来传递参数：

值传递：值传递是指在调用函数时将实际参数复制一份传递到函数中，这样在函数中如果对参数进行修改，将不会影响到实际参数。

引用传递：引用传递是指在调用函数时将实际参数的地址传递到函数中，那么在函数中对参数所进行的修改，将影响到实际参数。



默认情况下，Go 语言使用的是**值传递**，即在调用过程中不会影响到实际参数。



**值传递**

```go
package main

import (
	"fmt"
)


func main() {
	var a int = 22
	var b int = 10


	swap(a, b)

	fmt.Printf("a:%d\n", a)
	fmt.Printf("b:%d\n", b)
}


func swap(x, y int)  {
	x, y = y, x
}
```





**引用传递**

```go
package main

import (
	"fmt"
)


func main() {
	var a int = 22
	var b int = 10

	/* 调用 swap() 函数
	 * &a 指向 a 指针，a 变量的地址
	 * &b 指向 b 指针，b 变量的地址
	 */
	swap(&a, &b)

	fmt.Printf("a:%d\n", a)
	fmt.Printf("b:%d\n", b)
}


func swap(x, y *int)  {
	*x, *y = *y, *x
}
```



#### 变量的作用域

Go 语言中变量可以在三个地方声明：

- 函数内定义的变量称为局部变量
- 函数外定义的变量称为全局变量
- 函数定义中的变量称为形式参数





#### 数组

Go 语言数组声明需要指定元素类型及元素个数，语法格式如下：

```go
var variable_name [SIZE] variable_type
```

```go
// 初始化语法一：
var balance = [5] float32 {2.2, 2.3, 2.2}
fmt.Printf("%v", balance)

// 初始化语法二：
var a = [...] float32 {1.2, 23.23, 323.2}
fmt.Printf("%v", a[1])
```



#### 二维数组

```go
var arrayName [ x ][ y ] variable_type
```





#### 结构体

结构体定义需要使用 type 和 struct 语句。struct 语句定义一个新的数据类型，结构体有中有一个或多个成员。type 语句设定了结构体的名称。结构体的格式如下：

```go
type struct_variable_type struct {
   member definition;
   member definition;
   ...
   member definition;
}
```



#### 结构体指针

定义指向结构体的指针类似于其他指针变量，格式如下：

```go
var struct_pointer *Books
```





#### 切片

Go 语言切片是对数组的抽象。**Go 数组的长度不可改变**，在特定场景中这样的集合就不太适用，Go中提供了一种灵活，功能强悍的内置类型切片("动态数组"),与数组相比切片的长度是不固定的，可以追加元素，在追加时可能使切片的容量增大。



定义切片：

```go
var identifier []type
```

或使用make()函数来创建切片:

```go
var slice1 []type = make([]type, len)
```



切片初始化：

```go
s :=[] int {1,2,3 }
```



#### Range

Go 语言中 range 关键字用于 for 循环中迭代数组(array)、切片(slice)、通道(channel)或集合(map)的元素。在数组和切片中它返回元素的索引和索引对应的值。

```go
package main
  
import "fmt"

func main() {
        nums := []int{2, 3, 4}
        sum := 0

        for _, num := range nums {
                sum += num
        }
        fmt.Println("sum:", sum)

        for i, num := range nums {
                if num == 3 {
                        fmt.Println("index:", i)
                }
        }
}
```



#### Go语言Map（集合）

##### 定义Map

```go
// 声明变量，默认map是nil
var map_variable map[key_data_type] value_data_type

// 使用make函数
map_variable := make(map[key_data_type]value_data_type)
```

如果不初始化 map，那么就会创建一个 nil map。nil map 不能用来存放键值对



##### delete()函数

delete() 函数用于删除集合的元素, 参数为 map 和其对应的 key。





#### Go语言递归函数

递归函数就是自己调用自己的过程



例：函数递归实现阶乘

```go
package main

import "fmt"

func Factorial (n uint64) (result uint64) {
    if (n > 0) {
        result = n * Factorial(n - 1)
        return result
    }
    return 1
}

func main() {
    var i int = 15
    fmt.Printf("%d 的阶乘是 %d\n", i, Factorial(uint64(i)))
}
```



#### 接口（interface）

nterface(接口)是golang最重要的特性之一，Interface类型可以定义一组方法，但是这些不需要实现。并且interface不能包含任何变量。

简单的说：

- interface是方法的集合
- interface是一种类型，并且是指针类型
- interface的更重要的作用在于**多态实现**



定义：

```go
/* 定义接口 */
type interface_name interface {
   method_name1 [return_type]
   method_name2 [return_type]
   method_name3 [return_type]
   ...
   method_namen [return_type]
}

```



例：

```go
package main

import "fmt"

type Skills interface {
    Running()
    Getname() string
}

type Student struct {
    Name string
    Age int
}

func (p Student) Getname() string {
    fmt.Println(p.Name)
    return p.Name
}


func (p Student) Running() {
    fmt.Printf("%s running", p.Name)
}

func main() {
    var skill Skills
    var stu1 Student
    stu1.Name = "allen"
    stu1.Age = 22
    skill = stu1
    skill.Running()
}
```





#### 接口嵌套

go语言中的接口可以嵌套，可以理解我继承，子接口拥有父接口的所有方法，并且想要使用该子接口的话，必须将父接口和子接口的所有方法都实现。

```go
type Skills interface {
    Running()
    Getname() string

}

type Test interface {
    sleeping()
    Skills   //继承Skills
}
```



#### 错误处理

Go 语言通过内置的错误接口提供了非常简单的错误处理机制。

```go
type error interface {
    Error() string
}
```



#### 并发

Go 语言支持并发，我们只需要通过 go 关键字来开启 goroutine 即可。

语法格式：

```go
go 函数名( 参数列表 )
```



例子：

```go
package main
  
import (
    "fmt"
    "time"
)

func say(s string) {
    for i := 0; i < 5; i++ {
        time.Sleep(100 * time.Millisecond)
        fmt.Println(s)
    }
}

func main() {
    go say("world")
    say("!!!!!")
}
```



#### 通道（channel）

通道（channel）是用来传递数据的一个数据结构。通道可用于两个 goroutine 之间通过传递一个指定类型的值来同步运行和通讯。

声明一个通道：

```go
ch := make(chan int)
```



#### 通道缓冲区

通道可以设置缓冲区，通过make的第二个参数指定缓冲区的大小。

```go
ch := make(chan int, 100)
```

