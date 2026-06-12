---
title: "Delete Ubuntu partitions"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by bunnywatson on 2011-03-20
How do I erase OS and/or Ubuntu partiions completley?  Long, long story...but I would like to get rid of Ubuntu, possibly adding it back as a dual boot inside windows later.  I had a friend "upgrade" my computer for me while I was at work one day from windows vista to windows 7.  Then later my son "upgraded" my computer from windows 7 to Ubuntu (w/o dual booting or backing anything up.)   Needless to say I FINALLY set up my computer so that nobody but me can make any changes of this magnitude again.

 I set up windows inside ubuntu in virtualbox.  Virtual windows does not work the way I need it to and I NEED windows for several programs that I use daily.  A friend that is very versed in linux programs worked on my computer and it still will not do everything I need it to.  I tried to overwrite the OS completely.  I used recovery disks, and original windows disk, but every time and with everything I did I could not "erase" the Ubuntu partitions completely.  

Can anyone help me?

---

### Post by Hedgehog1 on 2011-03-21
First, get your PC to boot directly into Windows again:

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):
[IMG]http://img641.imageshack.us/img641/9550/small50createrepairdisk.png[/IMG]

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

---

### Post by Hedgehog1 on 2011-03-21
To remove Ubuntu:
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

### Post by Hedgehog1 on 2011-03-21
By the way, if there were things in Ubuntu you still want to use, you can load the windows version of Vbox and run Ubuntu in it.

It is an option if you need it...

It is more important that you run the OS that works best for you - if that is Windows, then that is fine.

***The Hedge***

:KS

---

### Post by troll1602 on 2011-03-21
Check out these instructions from Microsoft, [here]("http://windows.microsoft.com/en-US/windows7/Installing-and-reinstalling-Windows-7"). Click on the section titled "Using the Custom installation option and formatting the hard disk". Following those instructions should completely wipe your hard drive and install Windows 7.

However, don't give up on Ubuntu! It is a great OS with a great community! If you are still interested in dual-booting Ubuntu with Windows check out this [how-to]("http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-10-10-maverick-meerkat/"). The how-to mentions the Windows Partitioner, in your case I would use that tool. Here is a [link]("http://www.hackourlife.com/shrink-or-reduce-partition-size-in-windows-7/") if you missed it :-)

Again, don't give up on Ubuntu and remember to come back to the forum with updates and questions!

---

