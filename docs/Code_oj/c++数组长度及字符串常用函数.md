[TOC]

# 获取静态数组和动态数组的长度

总结:
**$\textcolor{blue}{获取char类型字符串数组长度：可以用strlen( )函数}$**

**$\textcolor{blue}{获得string类型的字符串长度：可用string.size()函数}$**

**$\textcolor{blue}{获取数组长度: 使用sizeof(array) / sizeof(array[0])，注意在C/C++中并没有提供直接获取}$**

**$\textcolor{blue}{数组长度的函数vector可以直接由a.size()获得动态数组长度}$**

## 1. 字符串数组

获取字节型的字符串数组长度：可以用strlen( )函数

获得string类型的字符串长度：可用string.size()函数

```cpp
#include <iostream>
#include <string>
using namespace std;
int main(){
	char str1[] = "hello world!"; // 长度为12
    int len_str1 = strlen(str1);
    cout << "str1:" << str1 << endl;
    cout << "str1_len:" << len_str1 << endl;

    string str2 = "hello world"; // 长度为11
    cout << "str2:" << str2 << endl;
    cout << "str2_len:" << str2.size() << endl;
}
```

```markdown
输出：

str1:hello world!
str1_len:12
str2:hello world
str2_len:11
```

## 2. 静态数组

获取数组长度: 使用sizeof(array) / sizeof(array[0])，注意在C/C++中并没有提供直接获取数组长度的函数

```cpp
#include <iostream>
#include <string>
using namespace std;
int main(){
	int b1[] = { 0, 2, 4, 5, 1, 3, 8, 6 };
	cout << "len_b1: " << sizeof(b1)/sizeof(b1[0]) << endl;
}
```

```
输出：
len_b1: 8
```

## 3. 动态数组

数组长度的函数vector可以直接由a.size()获得动态数组长度

```cpp
#include <iostream>
#include <string>
using namespace std;
int main(){
	vector<int> a1 = { 0, 2, 4, 5, 1, 3, 8, 6 };
    cout << "len_a1: " << a1.size() << endl;
}
```

```
输出：
len_a1: 8
```



# C++常用字符串函数使用整理[^1]

## strlen（字符数组）

- 功能：求字符串长度。
- 说明：该函数的实参可以是字符数组名，也可以是字符串。
- 使用样例：

```cpp
char s1[80] = "China";
cout<<strlen(s1)<<'\n';　　　　　　//输出结果为5
cout<<strlen("大学生"）<<'\n';　　  //输出结果为6　
```

- 结果说明：一个汉字有两个字节，所以strlen("大学生")的结果为6。

## strcpy（字符数组1，字符数组2）

- 功能：将字符数组2中的字符串复制到字符数组1中
- 说明：
  （1）字符数组1的长度必须大于等于字符数组2的长度。
  （2）复制时连同字符串后面的'\0'一起复制到字符数组1中。
  （3）不能用赋值语句将一个字符串常量或字符数组直接赋给一个字符数组。
  （4）字符数组的复制只能用strcpy函数处理。用一个赋值语句只能将一个字符赋给一个字符型变量或字符型数组元素。但可以在定义的时候初始化。

如以下形式：

```cpp
str1 ={''Good"};　　　　//不合法
str1 = str2;　　　　　　//不合法
char a[5],c1,c2;
c1 = 'A'; c2 = 'B';　　　 //合法
c[0] = 'C';　　　　　　 //合法
char g[20] = "aaaa'' 　  //合法
```

- 使用样例：

```cpp
char a[20]="aaaaaa",b[20]="bbb";
strcpy(a,b);
cout<<a; 
return 0;
```

- 结果说明：数组b的值将会覆盖数组a的值，所以结果为"bbb"。

## strcat（字符数组1，字符数组2）

- 功能：将字符数组2中的字符串连接到字符数组1中的字符串的后面，对字符数组2中的内容没有影响。
- 说明：该函数中的第二个参数也可以是一个字符串常量。
- 使用样例：

```cpp
char s1[20] = "one", s2 = "two", s3[20] = "three";

strcat(s1,s2);

strcat(s1,s3);
```

- 结果说明：运行样例后，则数组s1中的字符串为”onetwothree",数组s2和s3中的字符串没变。

## strcmp（字符数组1，字符数组2）

- 功能：比较两个字符串是否相等。
- 说明：
  （1）如果两个字符串中的字符均相同，则两个字符串相等，函数返回值为0；
  （2）当两个字符串不同时，则以自左至右出现的第一个不同字符的比较结果作为两个字符串的比较结果。
  　　 如果第一个字符串大于第二个字符串，则返回值为1。
  　　 如果第一个字符串小于第二个字符串，则返回值为-1。
  （3）这种比较是按字符的ASCII码值的大小比较的。
- 使用样例：

```cpp
strcmp("Student","Student");　　　　　　//比较结果为0
strcmp("student","Student");　　　　　　//比较结果为1
strcmp("Student","student");　　　　　　//比较结果为-1
int a=strcmp("stude","student");
```

- 结果说明：当第一个字符串比较完后，第二个字符串还有字符，则当第一个字符串小于第二个字符串，所以a的值为-1。

## strlwr（字符数组）

- 功能：将字符数组中存放的所有大写字母变成小写字母，其它字母不变。
- 使用样例：

```cpp
char s1[ ] = "Student1";
strlwr (s1);
```

- 结果说明：将s1数组中的字符串全部变成小写字母，即“student1"。

## strupr（字符数组）

- 功能：将字符数组中存放的所有小写字母变成大写字母，其它字母不变。
- 使用样例：

```cpp
char s1[ ] = "Student2";
strupr (s1);
```

- 结果说明：将s1数组中的字符串全部变成小写字母，即“STUDENT2"。

## strncpy(字符数组1，字符数组2，len)

- 功能：将字符数组2 前len个字符复制到字符数组1的前len个字符空间中。
- 说明：
  （1）第二个参数可以是数组名，也可以是字符串，第三个参数为正整数。
  （2）当字符数组2中表示的字符串的长度小于len时，则将该字符串全部复制到第一个参数所指定的数组中。
- 使用样例：

```cpp
char s1[ 80] = "aaaaaa", s2[80];
strncpy(s1,"student", 4);
strncpy(s2,"teacher",10);
```

- 结果说明：
  运行该样例后，s1为"studaa"；字符串"teacher"的长度小于10，则将其全部字符复制到s2中，s2的内容为"teacher"。

## strncmp(字符数组1，字符数组2，len)

- 功能：比较两个字符数组中表示的字符串的前len个字符。
- 说明：
  （1）前两个参数均可以为字符数组或字符串，第3个参数为正整数。
  （2）若第一个字符串或第二个字符串的长度小于len时，该功能与strcmp()相同。
  （3）当两个字符串的长度均大于len时，len为最多要比较的字符个数。
- 使用样例：
  `cout<<strncmp("English","England",4)<<endl;`
- 结果说明：因为比较的两个字符串的前4个字符相同，所以输出的值为0。

参考资料：

[^1]: https://www.cnblogs.com/gzx6688/p/10741507.html