---
title: "how to uninstall ubuntu 10.10"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by naved ..... on 2011-05-14
i m using windows 7 alongside ubuntu 10.10 i had install ubuntu frm cd (.iso)now i need to uninstall ubuntu from my pc and recover and delete the ubuntu partition ...and tell me how to fix mbr after deleting the partition in order to start  windows 7 smoothly

---

### Post by rizijones on 2011-05-14
I want to learn this too

---

### Post by The_Eggert on 2011-05-14
> **naved ..... said:**
> i m using windows 7 alongside ubuntu 10.10 i had install ubuntu frm cd (.iso)now i need to uninstall ubuntu from my pc and recover and delete the ubuntu partition ...and tell me how to fix mbr after deleting the partition in order to start  windows 7 smoothly

If you have a Windows Vista/7 install disc, use this method:
```
http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD
```

If not:
```
http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD
```

After that, just delete the partition from within Windows :)

---

### Post by naved ..... on 2011-05-14
> **The_Eggert said:**
> If you have a Windows Vista/7 install disc, use this method:
```
http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD
```If not:
```
http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD
```After that, just delete the partition from within Windows :)
so if i perform type 1 , windows bootloader will install at mbr but who to recover the space allocated to ubuntu 10.10  ....??????

---

### Post by scott-ian on 2011-05-14
I haven't used Windows 7 in a while, but I believe you can get to the partition manager by right clicking of Computer and clicking manage.  You cannot, however, edit the Windows 7 partition from in Windows 7.  I believe you need to use GParted on a Linux live cd.

---

### Post by Bapun007 on 2011-05-14
> **naved ..... said:**
> i m using windows 7 alongside ubuntu 10.10 i had install ubuntu frm cd (.iso)now i need to uninstall ubuntu from my pc and recover and delete the ubuntu partition ...and tell me how to fix mbr after deleting the partition in order to start  windows 7 smoothly

after installing windows boot loader to mbr use your ubuntu 10.10 live cd to recover the space used by ubuntu . Gparted is a very easy to use tool for doing that .

---

### Post by The_Eggert on 2011-05-14
> **naved ..... said:**
> so if i perform type 1 , windows bootloader will install at mbr but who to recover the space allocated to ubuntu 10.10  ....??????

In Windows, right-click on your start button and click run..Then write
```
diskmgmt.msc
```

There, you should see a partition which Windows doesn't recognize - That's the one you have/had ubuntu on..
If you have already rewritten the Windows mbr using either method, you can safely delete that partition, and if you wish, add it to your windows partition

---

### Post by Hedgehog1 on 2011-05-14
**[SIZE="4"]Here are the steps with pictures:[/SIZE]**


Fix MBR

First, get your PC to boot directly into Windows again:

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):
[IMG]http://img641.imageshack.us/img641/9550/small50createrepairdisk.png[/IMG]

If you are unable to make a recovery disk, you can download the ISO for [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

---

### Post by Hedgehog1 on 2011-05-14
**[SIZE="3"]To remove Ubuntu:[/SIZE]**

[IMG]http://img718.imageshack.us/img718/7687/small55diskmanagement.png[/IMG]
Remove Swap Partiton
[IMG]http://img97.imageshack.us/img97/4905/small56deleteswap.png[/IMG]
[IMG]http://img231.imageshack.us/img231/2992/small57freespace.png[/IMG]
Remove Ubuntu Partition
[IMG]http://img96.imageshack.us/img96/5986/small58deleteubuntu.png[/IMG]
Remove extended Partition
[IMG]http://img848.imageshack.us/img848/8053/small59deleteextended.png[/IMG]
Expand windows partition to use all the space
[IMG]http://img3.imageshack.us/img3/7880/small61extendwin7volume.png[/IMG]


***The Hedge***

:KS

---

