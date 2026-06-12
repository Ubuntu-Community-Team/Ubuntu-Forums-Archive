---
title: "g++ not working"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by vidur2812 on 2010-06-25
Hi,
I have installed ubuntu 9.10 on my macbook 6,1 (Mac OS X 10.6.2). But Im facing a big problem since my g++ compiler is not working. I have installed build-essential and g++ separately as well but still its not working. Please see the following:
vidur@vidur-laptop:~$ dpkg -l g++*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  g++            4:4.4.1-1ubunt The GNU C++ compiler
ii  g++-4.4        4.4.1-4ubuntu9 The GNU C++ compiler
ii  g++-4.4-multil 4.4.1-4ubuntu9 The GNU C++ compiler (multilib files)
un  g++-multilib   <none>         (no description available)

vidur@vidur-laptop:~$ sudo apt-get install g++
[sudo] password for vidur: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++ is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

Also when I try to write a C++ program I find it very difficult as the 'insert' doesnt come by pressing 'i' key on the keyboard.
Could you please help me out?

---

### Post by gmargo on 2010-06-25
What doesn't work?

```

$ cat hello.cpp
#include <iostream>
main()
{
    std::cout << "Hello World!" << std::endl;
    return 0;
}

$ g++ -o hello hello.cpp

$ ./hello
Hello World!

```

---

