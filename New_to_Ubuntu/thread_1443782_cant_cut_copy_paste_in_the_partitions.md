---
title: "cant cut copy paste in the partitions"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by jainsr on 2010-03-31
Hi, 
I am a new user of ubuntu and have recently it in my laptop but the problem is i amnot able to cut copy and paste anything. It shows an error saying permission restricted. Please help.

---

### Post by jimv on 2010-03-31
The only folder you can copy/cut/paste/move anything in is your home folder.  To work with files anywhere else in the system, you need to be root.  It is not advised that you modify files outside of your home folder.

---

### Post by undecim on 2010-03-31
> **jainsr said:**
> Hi, 
I am a new user of ubuntu and have recently it in my laptop but the problem is i amnot able to cut copy and paste anything. It shows an error saying permission restricted. Please help.

can you open a terminal, type "mount", press enter and post the output here.

Normally, when you access a drive from the file manager, it should automatically give you permission to access it. If it was set up during install to attach to a folder though, you might now have permission for it.

---

### Post by itisbasi on 2010-03-31
Partitions get mounted by default in read only mode. Use ntfs-3g or pysdm to configure the partitions to mount with read and write permissions.

---

### Post by jainsr on 2010-04-02
> **undecim said:**
> can you open a terminal, type "mount", press enter and post the output here.

Normally, when you access a drive from the file manager, it should automatically give you permission to access it. If it was set up during install to attach to a folder though, you might now have permission for it.



hi,
thanks for ur help. the thing is i did wat u told but m using my desktop which has a windows os and cant acces net also thru my laptop. acn u suggest me another way thru pls.

---

### Post by jainsr on 2010-04-02
hi,
thanks for ur help. the thing is i did wat u told but m using my desktop which has a windows os and cant acces net also thru my laptop. acn u suggest me another way thru pls.

---

### Post by anewguy on 2010-04-02
Let's try for some more detail:

Exactly what are you trying to copy/paste from where and to where?

Also, are you looking for help on getting on the net from Ubuntu as well?  The last part of your latest reply makes it sound like so.  If so, do the following in a terminal window (applications/accessories/terminal):

- type:

lspci <press enter>  This lists all of the PCI devices the system knows - doesn't mean it has a way to use it (such as a driver), but the system at least knows the device exists.

lsusb <press enter>  As per above, this time for USB devices.

copy and paste the output from those in a response back here and we'll go from there.

Dave ;)

---

