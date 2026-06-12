---
title: "Ubuntu 9"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by ahpitre on 2009-05-07
I downloaded the Ubuntu 9 64bit version. Does this version have the capability of resizing partitions without loosing data? I want to install Ubuntu on my laptop, which already has Windows Vista Home Premium 64 bit. Need to dual boot. Any suggestions?

PS : I still have not run the Ubuntu setup.

---

### Post by achase79 on 2009-05-07
You can boot into the liveCD and use gparted to resize your partition, then create partitions for linux (/, swap, /home)

---

### Post by muteXe on 2009-05-07
I believe vista has a partitioner built in.  Make sure you defrag a few times first though.

---

### Post by Sef on 2009-05-07
1) Use the Vista partitioner to shrink the partition.   

2) Run the Live CD for a while and make sure Ubuntu is compatible with your hardware.  

3) Read [Psychocats]("http://psychocats.net/ubuntu") for learning how to dual boot.

---

### Post by SunnyRabbiera on 2009-05-07
But most of all defrag, defragging is a VERY good idea.

---

### Post by Mark Phelps on 2009-05-07
> **ahpitre said:**
> I downloaded the Ubuntu 9 64bit version. Does this version have the capability of resizing partitions without loosing data? 
Basically -- NO.  Ubuntu uses Gparted, and that has a history of SOMETIMES corrupting Vista OS partitions during a resize.  While making sure that you do NOT have the "round to nearest cylinder" box checked has helped, there's no surefire way to guarantee that you will not encounter the problem.

And if you do, you'd better have a Vista DVD or a Vista recovery CD lying around, because you'll have to boot from it and run Startup Repair, probably several times, to get Vista boot capability back.

So, as others have suggested, do the Vista OS shrink from inside using the Disk Management tool.  IF you have problems with that, check the following link for some tips:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

---

