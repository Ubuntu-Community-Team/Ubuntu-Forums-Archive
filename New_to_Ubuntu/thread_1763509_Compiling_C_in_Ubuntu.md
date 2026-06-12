---
title: "Compiling C in Ubuntu"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by Slapyourbaby on 2011-05-20
Hey guys. I read a couple similar posts regarding this matter but nothing I found seems to address the problems I am having. 

I am going to explain how I got to where I am (so those having similar troubles might have their questions answered by reading this thread) and then explain my problem. 

I downloaded and installed Ubuntu 11.04 and ran it from Virtual Box on my laptop which is running Windows XP. Once Ubuntu is booted I opened up the text editor that came with Ubuntu (Applications/Accessories/Text Editor). In there I wrote this code :

#include <stdio.h> 

int main(void) 
{
printf("Hello World");
return 0; 
}

I then saved the file as hello.c  (and also tried hello.cpp) in the same area as my terminal which I believe is the Ubuntu home file. I will note that before I did this I received an error in the terminal that said the file and directory did not exist. 

Once the file has been saved I open my terminal and type "gcc hello.c". Basically, nothing happens. 

I thought maybe the program executes so fast that it doesn't even display on the screen long enough for me to actually see it. I figured this would only be the case in windows in which the compiler requires a getchar(); before return 0;                  I tried adding the getchar(); and nothing changed.
 

Thanks for your help.

---

### Post by Toz on 2011-05-20
gcc is a compiler, it only compiles code. If you do an **ls** in that directory you will see an a.out file. That is the default compiled program filename (because you did not specify an output file name). At this point you can either:```
./a.out
``` to run the program or compile it like:```
gcc hello.c -o hello
``` and execute it via:```
./hello
```

Here is a link further explaining it: [http://www.linfo.org/create_c1.html](http://www.linfo.org/create_c1.html)

---

### Post by Slapyourbaby on 2011-05-20
Worked perfectly. Thank you so much.

---

