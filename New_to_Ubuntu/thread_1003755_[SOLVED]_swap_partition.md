---
title: "[SOLVED] swap partition????/"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by aszxcv on 2008-12-06
what is the purpose of it ?

what is it?

---

### Post by nhasian on 2008-12-06
here's a good read:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by lovelyvik293 on 2008-12-06
Are it's like the virtual ram for the your OS(Just the Pages in windows),it's usefull when you are using lot's of heavy applications.and in case of hibernation.

---

### Post by Duck2006 on 2008-12-06
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Duck2006 on 2008-12-06
Like Windows, Linux uses a certain amount of space for holding programs temporarily, when
there is not enough available RAM (random access memory) to hold all the programs that are
running concurrently. Generally, the least recently used program (or part of a program) is
copied from memory to a file on your hard drive until it is needed again, at which time the
current least recently used program is swapped out in its place and the first program is loaded
back into memory. (This is an over-simplified explanation; there is much more to it, but this will
do for this question.) This file is called a swap file in Windows or OS/2 and “swap space” in
Linux, but in either case it is a form of data file that is read from and written to off and on as
long as your system is running.
Windows puts the swap file (a hidden system file with different names for different versions of
Windows) in the bootable data partition by default. OS/2 does the same, but by changing the
CONFIG.SYS file a user can put the swap file in any directory in any partition on any drive
they like. Linux, by default, requires a special swap partition in which to store the swap file.
(Actually, Linux does allow swap files to be put in data partitions, with caveats—see below for
more on this.)

---

### Post by Paqman on 2008-12-06
Also, regarding swap size, you'll see a lot of conflicting advice.

Bottom line for modern systems:
[LIST]
[*]Swap must be at least as large as RAM if you intend to use hibernation
[*]Otherwise, on systems with 1GB of RAM or more, 1GB of swap is plenty
[/LIST]

---

