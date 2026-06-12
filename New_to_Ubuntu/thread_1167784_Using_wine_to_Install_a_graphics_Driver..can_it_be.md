---
title: "Using wine to Install a graphics Driver..can it be done??"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by froginlinux on 2009-05-23
Hi all linux users...hope you are all well and having a good day..

I have noticed that there are lot of threads popping up today in various different forums about the use of WINE to install windows applications in linux..
Now this has got me thinking, can WINE be used to install the graphics drivers of a voodoo3 3dfx grahics card off the cd-rom. I have a graphics driver problem with this card using ubuntu hardy heron LTS, as it will only dsiplay 640 x 480 which is appalling!!

helpwould be appreciated, thanks...):P

---

### Post by mcduck on 2009-05-23
No, that won't help a bit. Windows is just a compatibility layer for running Windows programs, interpreting stuff between a running Windows program and the underlying Linux kernel. On the other hand drivers sit between the kernel and hardware (well, in Linux drivers are actually part of kernel itself which makes such solutions even less possible)

Trust me, there would be lots of happy people around if drivers form other operating systems could be used with a simple application compatibility layer. :D

---

### Post by froginlinux on 2009-05-23
Shame...i thought that would be the case, but you never know. i don't know enough about linux yet, although that is another iece of knowledge...so thanks.

What i don't understand is my voodoo3 3df worked in dapper drake, but once i changed to hardy it won't work, it is a most frustrating problem, one that has me running fedora 10 as it has graphical support for this card so my display is lovely, but switch back to ubuntu and yuck!!!

---

### Post by cjv8888 on 2009-05-23
I think you need to edit the xorg.conf file.

Have a look at this [thread.]("http://www.linuxquestions.org/questions/linux-software-2/voodoo3-stuck-in-640x480-and-changing-xorg.conf-has-no-effect-384592/")

---

### Post by froginlinux on 2009-05-23
excellent, thanks, i will give that a try...

I have tosay this is far more engaging than i thought it would be):P

---

### Post by hareesh_sree on 2012-01-23
My system is Intel dual core, Biostar G41-M7, Samsung B2030 monitor. How can I adjust display settings?
Ubundu 10.04 displays "unknown monitor" in the monitor settings, How can I reconfigure to get the resolution 1600x900

---

### Post by whatthefunk on 2012-01-23
Might want to update.  Hardy Heron hasnt been supported for a long time.  Might solve your driver problem as well.

---

### Post by nothingspecial on 2012-01-23
Hi, rather than bumping an old thread up to the top, please start a new one of your own with as much detail as possible.

Closed.

---

