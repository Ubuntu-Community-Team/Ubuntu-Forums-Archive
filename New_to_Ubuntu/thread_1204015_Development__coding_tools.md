---
title: "Development / coding tools"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by Iriscal on 2009-07-04
Hello! I just installed Ubuntu Netbook Remix after having to use Ubuntu for a computer science course. It's my first Linux system, so I'm still learning the ropes. My question is, how can I find resources for coding in some common languages like C++ or Java? (I see that Python is already installed...) The problem is that I tried writing a Hello World in C++, but had to install gpp, and gpp tells me it cannot find the requested include (iostream). Are there any other compilers that will work, or will I need to download it and other libraries?

---

### Post by ibutho on 2009-07-04
Hi and welcome to the forum. 

Install the build-essential package using the package manager and that will install various compilers and libraries. For java, take a look [here]("https://help.ubuntu.com/community/Java").

---

### Post by Iriscal on 2009-07-04
Thanks for responding and for the link, ibutho. I found the build-essential package in the manager like you said, but apparently it's already installed. Is there an additional step I need to take?

---

### Post by ibutho on 2009-07-04
> **Iriscal said:**
> Thanks for responding and for the link, ibutho. I found the build-essential package in the manager like you said, but apparently it's already installed. Is there an additional step I need to take?

Can you post your Helloworld code.

---

### Post by Iriscal on 2009-07-04
If it's a problem with my code, I'm gonna laugh. Then kick myself a bit. Then laugh a little more.
```
#include <iostream>

using namespace std;

int main()
{
    cout << "Hello, world! "
         << "I was written to test Ubuntu Netbook Remix's compiler! "
         << "If I'm working properly, it means the test was a success!"
         << endl;
    return 0;
}
```

---

### Post by TeoBigusGeekus on 2009-07-04
Don't use gpp. You need to use g++.
Save the file on your Desktop as test.cpp
Open terminal and type
```
g++ ~/Desktop/test.cpp
```
It will produce a.out
Give
```
./a.out
```
and you're done.

For a good programming ide, install Geany
```
sudo apt-get install geany
```

---

### Post by Iriscal on 2009-07-04
Awesome, thanks TeoBigusGeekus. It's working perfectly.
Now time to practice my still-noobish programming skills.

---

