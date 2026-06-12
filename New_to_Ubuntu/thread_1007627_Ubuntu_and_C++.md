---
title: "Ubuntu and C++"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by darek_jestem on 2008-12-10
Hi everyone.
I have a problem when I try to compile any simple program write in C++ I have the output that I have not header-file "ncurses.h".
This is weird because I don't include this file in my program:D:/
There is the most simple program:

```
#include<iostream>
int main()
{
return 0;
}
```
and the output:
```
....
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking ncurses.h usability... no
checking ncurses.h presence... no
checking for ncurses.h... no
configure: error: Couldn't find ncurses headers.
*** Exited with status: 1 ***

```
I don't know why it asking for this file but I downloaded this file...but this still doesn't work:/
any ideas??

---

### Post by silverglade00 on 2008-12-10
Have you installed build-essentials?

```
sudo apt-get install build-essentials
```

---

### Post by Michael.Godawski on 2008-12-10
the correct package name is:

```
sudo apt-get install build-essential
```

:)

---

### Post by ibuclaw on 2008-12-10
What software are you using to compile ?

Looks like your configure file is failing you, but I can't see a reason as to why you even have one ??? :confused:

try:
```
sudo apt-get install build-essential ncurses-dev
```

and to compile software, I'd rather use g++ or write my own make file.

```
g++ sourcefile.cpp -o compiledprogram
```

[EDIT]
Proof of concept:
```

iain@jaunty:~/$ cat  > foo.cpp << EOF
> #include<iostream>
> int main()
> {
> return 0;
> }
> EOF
iain@jaunty:~/$ g++ foo.cpp -o foo
iain@jaunty:~/$ ./foo 
iain@jaunty:~/$ echo $?
0
iain@jaunty:~/$ cat  > foo.cpp << EOF
> #include<iostream>
> int main()
> {
> return 42;
> }
> EOF
iain@jaunty:~/$ g++ foo.cpp -o foo
iain@jaunty:~/$ ./foo 
iain@jaunty:~/$ echo $?
42
iain@jaunty:~/$ 

```

Regards
Iain

---

### Post by silverglade00 on 2008-12-10
> **Michael.Godawski said:**
> the correct package name is:

```
sudo apt-get install build-essential
```

:)

I always get that one wrong :)

---

### Post by darek_jestem on 2008-12-11
```
sudo apt-get install build-essential
```
I've installed this package firstly.
I try to install ncurses-dev but now I have different error:)
I'm using Kdevelop software but this is base on gcc.
there is a code:
This is when I try to compile in Kdevelop:
```
cd '/home/dariusz/ddafad/debug/src' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k kkk.lo
make: *** No rule to make target `kkk.lo'.
*** Exited with status: 2 ***

```
"No rule to make ..." what does it mean??

Thanks for tinivol, I can compile using the g++ directly:)
But in the Kdevelop may by more comfortable...:)

---

