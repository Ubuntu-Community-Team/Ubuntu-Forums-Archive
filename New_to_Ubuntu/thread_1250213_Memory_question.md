---
title: "Memory question"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by mbaybarsk on 2009-08-26
Hi,
 
I'm a total newbie and i'm someone who can't even see if his OS is 32 bit or 64 bit :) And this is my first post :) 
 
My question is, i have 4 gb's of RAM, but i see that the OS sees it as 3 gb's. Is there a way to fix this? Can it be because i have 32 bit version of ubuntu 9.04? 
 
Thanks ;)

---

### Post by achase79 on 2009-08-26
yes.  the 32-bit version (other than the server kernel) cannot see all your ram.  The only fix is to install the 64-bit version.

---

### Post by halitech on 2009-08-26
its possible that you have the 32 bit version which has a RAM limitation of 4 gig (although it won't show 4gig exactly, more like 3.4 or so)

if you open a terminal and run
```
uname -a
``` and
```
free -m
```and post the results we can check for you

---

