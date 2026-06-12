---
title: "&quot;Ghost&quot; Utility"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by stuart264 on 2009-07-10
Could anyone advise if there is a "Ghost" utility for Ubuntu anywhere as I need to put in a bigger hard drive for my multimedia and copy the files across but I need to do it off-line as helpfully my motherboard has only 2 sata sockets so I will need to boot from a CD or DVD to do it.

Stuart.

---

### Post by sturdy on 2009-07-10
Take a look at partimage. Lacks the bells and whistles of Ghost but will create a partition image.

---

### Post by scorp123 on 2009-07-10
> **stuart264 said:**
>  I need to put in a bigger hard drive for my multimedia and copy the files across  Why use a partition image then? A partition image also copies the empty chunks and thus wastes space. What I mean: If you have a 250 GB disk but only 200 GB of data on it, then the copy of the parition will still occupy 250 GB of space on the target, and not just the 200 GB that are really used.

Multimedia files such as movies and DVD images are already big enough, so why not just copy them onto a new disk ... ?

I recently had a similar problem: My old PC's motherboard had died, it would not boot anymore. But the IDE disks were still intact. But the new PC I bought was all SATA -- no more IDE. So I needed to find a way how to get my data off the old IDE/PATA disks onto the new SATA disks. I bought an external USB casing that basically converts IDE/PATA disks to USB disks. Perfect. So I simply removed my old but still working disks from the dead PC and hooked them up via USB to my new system ... It worked. And from there onwards it was just "drag & drop". Copying 500+ GB of data took a while, but it worked.

I then found IDE-to-SATA converters in an electronics shop for like 10$ a piece. So now I can even use my old but working IDE disks inside my new SATA-only PC (the speed is a tad slower than what I get from the native SATA disks, but oh well ...)

I'd suggest you try something like this. Moving disk images of several 100 GB around is far more frustrating ...

---

### Post by sturdy on 2009-07-10
> **scorp123 said:**
> Why use a partition image then? A partition image also copies the empty chunks and thus wastes space. 

Actually, here is a quote from the partimage manual: Partimage will only copy data from the used portions of the partition.

In addition, three levels of compression are offered. I'm a Ubuntu noob so take a look at the manual and make your own decision. [www.partimage.org](www.partimage.org)

---

### Post by Cheesemill on 2009-07-10
Take a look at [CloneZilla]("http://clonezilla.org")

Also you can use gparted on the Live CD to copy partitions.

---

### Post by spcwingo on 2009-07-10
There's also G4L (Ghost for Linux).  You can download/read more about it here:

[[COLOR="Red"]CLICKY[/COLOR]]("http://sourceforge.net/projects/g4l/")

---

### Post by LewRockwell on 2009-07-10
Parted Magic is the LiveCD Multi-Utilities Disk that has internet connectivity, firefox, secure erase, gparted, clonezilla and some other stuff.

[http://www.partedmagic.com/](http://www.partedmagic.com/)

.

---

### Post by Ji Ruo on 2009-07-11
+1 for clonezilla. It's not as user friendly as it could be but I got it to work and have used it several times.

---

### Post by hysteresis on 2009-07-11
I like ping.

[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

---

### Post by scorp123 on 2009-07-12
> **hysteresis said:**
> I like ping.

[http://ping.windowsdream.com/](http://ping.windowsdream.com/) Nice find! :KS

---

### Post by linuxology on 2009-07-12
I concur PING is the best app that is free!  Please donate to the cause though if you like it.

---

### Post by LewRockwell on 2009-07-12
> **hysteresis said:**
> I like ping.

[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

the way they have it set up it looks pretty "scammer" to me

I don't download anything I have to sign-up-for or give personal information to get...

COUNT ME OUTA THAT STUPH!

**************************
[http://www.clonezilla.org/](http://www.clonezilla.org/)
**************************

.

---

### Post by lemuriaX on 2009-07-12
This article from the Ubuntu Kung Fu book might be helpful:

[http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk](http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk)

---

