---
title: "g++ compiler"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by pUnT3r on 2009-12-25
I want to install g++ compiler on ubuntu 9.10.I installed it using command
sudo apt-get install build-essential
But still compiling a simple C++ program displays error.However C program is running well.
PLEASE HELP ME!!!!

---

### Post by falconindy on 2009-12-25
Would be helpful to post your code and/or error message on compile.

---

### Post by pUnT3r on 2009-12-25
I created the file f2.cpp as below
///////
#include<iostream.h>
int main()
{
cout<<"WoW";
return 0;
}
///////
The errors displayed after compiling with "g++ f2.cpp -o f2" were-----
f2.cpp:1:21: error: iostream.h: No such file or directory
f2.cpp: In function ‘int main()’:
f2.cpp:4: error: ‘cout’ was not declared in this scope

---

### Post by lloyd_b on 2009-12-25
> **pUnT3r said:**
> I created the file f2.cpp as below
///////
#include<iostream.h>
int main()
{
cout<<"WoW";
return 0;
}
///////
The errors displayed after compiling with "g++ f2.cpp -o f2" were-----
f2.cpp:1:21: error: iostream.h: No such file or directory
f2.cpp: In function ‘int main()’:
f2.cpp:4: error: ‘cout’ was not declared in this scope

Try "#include <iostream>" rather than "#include <iostream.h>" - the ".h" version is deprecated, and was never really standard to being with.

You will also need to either add a "using namespace std;" line, or reference "cout" as "std::cout".

Lloyd B.

---

### Post by pUnT3r on 2009-12-27
Thnx a lot i did make a mistake!!!!Now the code is running well.

---

