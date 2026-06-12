---
title: "C++/gcc not working properly"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by excalibur787 on 2011-01-13
Hello World. 
I'm new to linux and I'm trying to get gcc to compile the obligatory Hello World program for my C++ class so that I don't have to install Visual Studio on my other computer. I made the program as follows:

#include <iostream>
int main(){
    cout << "Hello World" << endl;
    return 0;
}

When I run this program ($ gcc HelloWorld.cpp) I get a long list of errors saying things like "undefined reference to ..."

I'm not sure if this is actually a real error or if I installed something incorrectly. If it is only an error, is there a program I can download to make these error messages less archaic? I read that splint only works for C and not C++.
If it would help to see the entirety of the error message, I can post it.

---

### Post by vivek.pandey on 2011-01-13
> **excalibur787 said:**
> Hello World. 
I'm new to linux and I'm trying to get gcc to compile the obligatory Hello World program for my C++ class so that I don't have to install Visual Studio on my other computer. I made the program as follows:

#include <iostream>
int main(){
    cout << "Hello World" << endl;
    return 0;
}

When I run this program ($ gcc HelloWorld.cpp) I get a long list of errors saying things like "undefined reference to ..."

I'm not sure if this is actually a real error or if I installed something incorrectly. If it is only an error, is there a program I can download to make these error messages less archaic? I read that splint only works for C and not C++.



If it would help to see the entirety of the error message, I can post it.

dude there are few things you need to know
1)gcc-compiler for c only
2)g++ compiler for c++
3)your program s in c++ so use g++ get it installed by sudo apt-get install g++
4)your program code should be like this

#include <iostream>
using namespace std;
int main(){
    cout << "Hello World" << endl;
    return 0;
}
here using namespace is used for cout and cin
5)compile as g++ filename  (if it is in home folder)
else
g++ path_to_the_file

enjoy your stay in ubuntu

---

### Post by excalibur787 on 2011-01-13
Hehe I guess that would explain it. Thanks a lot

---

### Post by vivek.pandey on 2011-01-13
i would rather suggest you to mark this thread as solved if your doubts are cleared:)

---

