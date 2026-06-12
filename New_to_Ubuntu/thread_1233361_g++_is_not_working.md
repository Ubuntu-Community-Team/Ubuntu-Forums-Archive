---
title: "g++ is not working"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by basu_ on 2009-08-06
I installed Ubuntu 9.04 i 386 desktop and tried compiling a C++ program. The program did not compile and the error message "
g++ cannot be found in the following packages
 g++ 
pentium builder
bash: g++: command not found"

I thought that it was not installed and tried installing it from synaptic..

To my dismay, i found that it was marked green.. 

What do i do? 

I cannot unisntall it as many important dependencies will be removed and the system will probably stop running after that...
please help..

---

### Post by Lampi on 2009-08-06
aren't you just missing the symbolic link in /usr/bin?

```
/home/lampi# which g++
/usr/bin/g++
[..]
/home/lampi# ls -la /usr/bin/g++
lrwxrwxrwx 1 root root 7 2009-05-09 11:43 /usr/bin/g++ -> g++-4.3
```

if you are missing the link you can add it or temporarily export the g++ Version you want to use into your environment:

export CXX=g++-4.3

... and for gcc compiler:

export CC=gcc-4.3

---

