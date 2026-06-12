---
title: "graphics programing packages in c"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by aju1991 on 2011-07-09
Hi friends,
I am using ubuntu11.04. 
I installed c,c++, java in my system.
Now i want to install vga package to study graphics programing in c .
Please help me anyone to install appropriate package for vga
..........
if i run a graphics program using gcc, it shows that
 fatal error: vga.h: No such file or directory
compilation terminated.
 

if i run using gcc-lvga it shows
gcc-lvga: command not found

if i run using gcc -lvga it shows 
fatal error: vga.h: No such file or directory
compilation terminated.

my program is 

#include<stdio.h>
#include<vga.h>
main()
{
    vga_init();
    vga_setmode(4);
    vga_drawline(50,50,100,100);
    vga_getch();
    vga_setmode(0);
}


please help me.........

---

### Post by Wim Sturkenboom on 2011-07-09
I haven't installed development software at this stage, but [this link](http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/include/video/vga.h) indicates that it's "*#include <video/vga.h>*" for the first error.

The second command will not fix the include problem. It will fix a library problem if there is one. Because you're copy/past mistake, I'm not sure what you typed. There is a difference between
```

gcc -lvga

```
and
```

gcc-lvga

```
Looks like you used the latter.

---

### Post by Simian Man on 2011-07-09
Unless you specifically want to use VGA for some special reason (like the ability to run w/o an OS), I'd recommend using something else for graphics programming in C.  VGA is very outdated, limits your color choices, has no hardware acceleration and is generally hard to use.

OpenGL is your fastest and most flexible option, but requires some knowledge of 3D concepts even if you only want 2D.  There is also SDL which is used by many 2D games, is very simple and has great documentation and tutorials.

---

### Post by aju1991 on 2011-07-09
In my college my teacher recommends that in graphics lab

---

