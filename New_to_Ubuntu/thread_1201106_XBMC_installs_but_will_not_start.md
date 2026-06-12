---
title: "XBMC installs but will not start?"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by ineedsleep on 2009-06-30
I'm a total beginner with linux , i've installed Ubuntu , and then went on to install XBMC by following the directions here :
 
[http://n3wt0n.com/blog/?p=306](http://n3wt0n.com/blog/?p=306)
 
It seems to install fine yet when I go to Applications > sound & Video > Xbmc to run it , a "untitled window" pops up for a second and then dissapears. I'm thinking some sort of error is being reported somewhere but I am such a n00b at linux, I don't know where to even start. Please help. 
 
Thanks.

---

### Post by ken22 on 2009-06-30
Start the program from the shell, probably by xbmc.

It should output something. i.e the error.

---

### Post by ellgor on 2009-07-01
Hi,

Open a terminal >Applications>Accesories and type in:

sudo xbmc

which will make it run as it should, its a permission thing, hope this helps.

Regards, Ellgor.

---

### Post by ineedsleep on 2009-07-01
ok , I now found the error code :

Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  21
  Current serial number in output stream:  22
CRITSEC[0x8bcde24]: Trying to enter destroyed section.
CRITSEC[0x8bcde24]: Trying to leave destroyed section.

What do I do now? 

Looking up the error in google doesnt return anything of use to me.

---

