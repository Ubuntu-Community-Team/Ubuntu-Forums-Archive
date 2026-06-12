---
title: "c++ &quot;hello world&quot; error"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by minsf on 2009-08-06
when running a simple c++ hello-world program i get the error
> hello: 1: Syntax error: word unexpected (expecting ")")
any idea why?

**_more details:_**
i decided to jump in and compile my first c++ file.
the simple hello.cpp file is:
> #include <iostream>
using namespace std;

int main() {
       cout << "hello world";
}
i compiled it in the terminal via
> g++ -o hello hello.cpp
and when i tried executing it by
> sh hello
i got the error mentioned above

---

### Post by OutOfReach on 2009-08-06
You don't execute C++ programs with sh, that's for bash scripts. This should work:
```

./hello

```
Assuming that the hello executable is in the current directory.

---

### Post by minsf on 2009-08-06
silly of me...
thanks a ton!

---

