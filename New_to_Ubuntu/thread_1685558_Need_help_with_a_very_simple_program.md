---
title: "Need help with a very simple program"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by techningeer on 2011-02-10
I am using the CodeLite IDE. I compiled the following program using CodeLite (It is a C++ program):

#include <iostream.h>
int main()
{
	cout << "Hello World\n";
	return (0);
}

It returns this message:

g++ -c  "/home/keagan/.coding-work/Hello/printamessage.cc" -g  -o ./Debug/printamessage.o "-I." "-I." 
/home/keagan/.coding-work/Hello/printamessage.cc:1:23: error: iostream.h: No such file or directory
/home/keagan/.coding-work/Hello/printamessage.cc: In function ‘int main()’:
/home/keagan/.coding-work/Hello/printamessage.cc:4: error: ‘cout’ was not declared in this scope
make[1]: *** [Debug/printamessage.o] Error 1
make: *** [All] Error 2

Anybody have any idea how to fix this? It seems to be a library issue...

--thanks, techningeer

---

### Post by robsoles on 2011-02-12
Drop the .h off iostream and give it another whirl.

You may need a 'namespace', take a look at [http://www.cplusplus.com/doc/tutorial/program_structure/](http://www.cplusplus.com/doc/tutorial/program_structure/)

(This is far from 'strictly an Ubuntu issue' and better help for programming in a specific language is much more likely to be in a dedicated forum elsewhere than ubuntuforums.org)

---

### Post by Vaphell on 2011-02-12
```
#include <iostream>

// using namespace std;

int main(int argc, char **argv)
{
	std::cout << "Hello world" << std::endl;
	return 0;
}
```

cout and endl belong to the std namespace, so you need to use std:: prefix to indicate that or put following line above your main()
```
using namespace std;
```

btw it's iostream not iostream.h - standard c++ header files have no extension

---

