## Perl

* 标量$a = 1;

* 数组

  > @b = {1,2,3};  
  >
  > $b[1]表索引数组
  >
  > @b = qw/1 2 3/; 数组；另一种表示
  >
  > push：数组末尾添加
  >
  > unshift：数组开头添加
  >
  > pop：数组末尾删除
  >
  > shift：数组开头删除
  >
  > Perl 中数组元素替换使用 splice() 函数，语法格式如下，以下实例从第6个元素开始替换数组中的5个元素: splice(@nums, 5, 5, 21..25);
  >
  > Perl 中将字符串转换为数组使用 split() 函数，语法格式如下：@string = split('-', $var_string);
  >
  > Perl 中将数组转换为字符串使用 join() 函数，语法格式如下：$string1 = join( '-', @string );
  >
  > Perl 中数组排序使用 sort() 函数，语法格式如下：@sites = qw(google taobao runoob facebook);     @sites = sort(@sites);
  >
  > *注意：数组排序是根据 ASCII 数字值来排序。所以我们在对数组进行排序时最好先将每个元素转换为小写后再排序。*

* 哈希：哈希是 **key/value** 对的集合。Perl中哈希变量以百分号 (%) 标记开始。访问哈希元素格式：**${key}**。

  > * 列表中第一个元素为 key，第二个为 value。
  >
  > ```perl
  > %data = ('google', 'google.com', 'runoob', 'runoob.com', 'taobao', 'taobao.com');
  > ```
  >
  > * 也可以使用 **=>** 符号来设置 key/value:
  >
  > ```perl
  > %data = ('google'=>'google.com', 'runoob'=>'runoob.com', 'taobao'=>'taobao.com');
  > ```
  
  > * 读取所有的键key：keys %HASH
  >
  > @names = keys %data;
  >
  > * 使用 **values** 函数来读取哈希所有的值,语法格式如下：values %HASH
  >
  > @urls = values %data;
  >
  > * 可以使用 **exists** 函数来判断key是否存在，存在的时候读取：
  >
  > ```perl
  > if( exists($data{'facebook'} ) ){   print "facebook 的网址为 $data{'facebook'} \n"; }
  > ```
  >
  > * 添加 key/value 对可以通过简单的赋值来完成。但是删除哈希元素你需要使用 **delete** 函数：delete $data{'taobao'};
  > * 可以使用 foreach 和 while 来迭代哈希：
  >
  > ```perl
  > foreach $key (keys %data){    
  > 	print "$data{$key}\n"; }
  > ```
  >
  > ```perl
  > while(($key, $value) = each(%data)){
  > 	print "$data{$key}\n"; }
  > ```
  
* 条件判断：

  > unless：如果不，与if not类似
  >
  > unless......else

* 循环判断：

  >  do...while 循环会确保至少执行一次循环

* 循环控制：

  > next语句：Perl next 语句用于停止执行从next语句的下一语句开始到循环体结束标识符之间的语句，转去执行continue语句块，然后再返回到循环体的起始处开始执行下一次循环。next [ LABEL ];其中 LABEL 是可选的，如果没有指定 LABEL，next 语句将返回到循环体的起始处开始执行下一次循环。
  >
  > last语句：
  >
  > continue语句：Perl continue 块通常在条件语句再次判断前执行。
  >
  > redo语句：redo 语句直接转到循环体的第一行开始重复执行本次循环，redo语句之后的语句不再执行，continue语句块也不再执行；
  >
  > goto语句：Perl 有三种 goto 形式：got LABLE，goto EXPR，和 goto &NAME。

* 运算操作符：

  > 比较运算操作：<=>或cmp : 检查两个操作数的值是否相等, 如果左边的数小于右边的数返回 -1，如果相等返回 0, 如果左边的数大于右边的数返回 1 。
  >
  > 引号运算：
  >
  > * q{}：为字符串添加单引号，q{abcd} 结果为 'abcd'
  > * qq{}：为字符串添加双引号，qq{abcd} 结果为 "abcd"
  > * qx{ }：为字符串添加反引号，qx{abcd} 结果为 \`abcd\`

* 其他运算符：

  > 点号. ：点号 (.) 用于连接两个字符串。
  >
  > x：x 运算符返回字符串重复的次数。('-' x 3) 输出为 ---。
  >
  > .. ：.. 为范围运算符。(2..5) 输出结果为 (2, 3, 4, 5)
  >
  > -> ：箭号用于指定一个类的方法，$obj->$a 表示对象 $obj 的 $a 方法。

* 子程序：

  * 子程序私有变量：默认情况下，Perl 中所有的变量都是全局变量，这就是说变量在程序的任何地方都可以调用。如果我们需要设置私有变量，可以使用 **my** 操作符来设置。**my** 操作符用于创建词法作用域变量，通过 **my** 创建的变量，存活于声明开始的地方，直到闭合作用域的结尾。闭合作用域指的可以是一对花括号中的区域，可以是一个文件，也可以是一个 if, while, for, foreach, eval字符串。
  
* 变量的临时赋值：使用 local 为全局变量提供临时的值，在退出作用域后将原来的值还回去。local 定义的变量不存在于主程序中，但存在于该子程序和该子程序调用的子程序中。
  
  * 静态变量：state操作符功能类似于C里面的static修饰符，state关键字将局部变量变得持久。state也是词法变量，所以只在定义该变量的词法作用域中有效，举个例子：use feature 'state';
  
* 引用：

  * 创建引用：定义变量的时候，在变量名前面加个\，就得到了这个变量的一个引用，比如:

  ```perl
  $scalarref = \$foo;     # 标量变量引用
  $arrayref  = \@ARGV;    # 列表的引用
  $hashref   = \%ENV;     # 哈希的引用
  $coderef   = \&handler; # 子过程引用
  $globref   = \*foo;     # GLOB句柄引用
  ```

  * 取消引用：取消引用可以根据不同的类型使用 $, @ 或 % 来取消
* 引用函数：
  
  ```perl
  #!/usr/bin/perl
   
  # 函数定义
  sub PrintHash{
     my (%hash) = @_;
     
     foreach $item (%hash){
        print "元素 : $item\n";
     }
  }
  %hash = ('name' => 'runoob', 'age' => 3);
   
  # 创建函数的引用
  $cref = \&PrintHash;
   
  # 使用引用调用函数
  &$cref(%hash);
  ```
  
  