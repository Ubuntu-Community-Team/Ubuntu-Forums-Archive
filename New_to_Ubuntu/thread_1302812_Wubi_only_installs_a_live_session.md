---
title: "Wubi only installs a live session"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by matmuc on 2009-10-27
Since I dont get answers on my first post, I try to explain my problem in another way:
I installed Ubuntu 9.04 with Wubi on 2 computers.
Everything works fine on my notebook.
On the desktop pc the Nvidia graphics card is not recognized and no matter what I try, the user I supply with the Wubi Installer is constantly ignored and the system starts with "live session user" and behaves like a live session. I can install an Nvidia driver, make all kinds of adjustments, and the next time I start, everything is forgotten. I simply created a live session on my pc, it seems. But I use exactly the same iso file on my notebook.
I would be very thankful if anybody has an idea what I can do to get Ubuntu running on my pc.
Greetings from Munich
Mathias

---

### Post by martrn on 2009-10-27
> **matmuc said:**
> I would be very thankful if anybody has an idea what I can do to get Ubuntu running on my pc. Greetings from Munich Mathias

Hi Mathias,

I will just answer the last part if that's ok with you.

You can download [//partedmagic.com/]("http://partedmagic.com/") or [//gparted...//]("http://gparted.sourceforge.net/"), which are free gnu tools, and they come on an iso which you can burn to a CD.  If you do this and boot up the CD it will will give you some partitioning tools where you can make a small partition and you could give it a few gb's of space however much you could spare and ubuntu will have a partition to your hard drive.  This would make your ubuntu installation a live partitioned installation.  You can then install a full version of ubuntu to that partition without being bothered by windows or bothering windows as it will have its own partition.

If you wanted to install ubuntu to a pen drive then there is a tool called [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") (unetbootin) which allows you to install ubuntu to a pen drive.  This is a perfectly good way to install ubuntu and you can install it to a pen drive with however much space you a pen drive for.  A lot of people have installed ubuntu to a pen drive even people who have to use windowze for employment reasons etc.

I hope that helps and good luck !

---

### Post by matmuc on 2009-10-28
Thank you for your tips. I will certainly install Ubuntu in a separate partition, as soon as I am a little more familiar with everything.
But at first, I will rather do that on my notebook, where the Wubi-Installation runs without any major problems. 
On the other PC, my question remains: Why does it install a live system and only lets me sign on as "live session user"? Is this caused by some kind of hardware problem? I simply dont want to make the effort and set up new partitions, another boot loader and install Ubuntu and then find the same kind of live system.
I run Windows XP professional, SP3 on both PCs and I dont use any exotic or super new hardware components.
My next step will be to search the whole system for hidden files that may have remained from a live session and to check the windows registry.
I will post any new informations, if I happen to find something.
Mathias

---

### Post by martrn on 2009-10-28
> **matmuc said:**
> ...."..Why does it install a live system and only lets me sign on as "live session user"? Is this caused by some kind of hardware problem?..."..

When a linux system is first booted it will load an intitrd.  The initrd is a initial ram disk that contains a basic linux kernel and a set of bundled loadable kerenel modules (drivers) that enable preparations of a linux system to occour before the real root file system is loaded. On this initrd ram disk will usually include hardware detection, module loading and device and hardware discovery tools so that the real root file system can be mounted.

wubi uses [https://launchpad.net/lupin]("https://launchpad.net/lupin") Luplin as its initrd.  Sometimes it mounts images as ISO devices in a loop-back. ?????

>  I simply dont want to make the effort and set up new partitions, another boot loader and install Ubuntu and then find the same kind of live system.

A proper installation of a Gnu/Linux distribution such as ubuntu doesn't use luplin to modify anything, and has a proper initrd and initramfs, to mount the file system.  If you install ubuntu then the Linux kernel will read and write its file systems naively without any need to virtualise the file system.  Its a full installation of a linux system.

> 
I run Windows XP professional, SP3 on both PCs and I dont use any exotic or super new hardware components. My next step will be to search the whole system for hidden files that may have remained from a live session and to check the windows registry. I will post any new informations, if I happen to find something. Mathias

---

### Post by matmuc on 2009-10-28
Hi,
thanks a lot for your explanations. I think you convinced me not to spend too much time with Wubi but to try the real thing. As soon as have enough time, I'll clean up my disk for a new partition and install Ubuntu (would you recommend 9.1?).
Probably the Wubi installation is disturbed by some hardware detection problems and so I end up with a live session. Anyway, I think I should not struggle for the perfect Wubi installation but for a good installation of Ubuntu.
One last question for the moment: is it better to use one partition or maybe 2 (like system/apps and data) and are there recommendations for the size of partitions?
Once again, thank you, and greetings from Munich
Mathias

---

### Post by martrn on 2009-10-28
> Hi,thanks a lot for your explanations. I think you convinced me not to spend too much time with Wubi but to try the real thing. As soon as have enough time, I'll clean up my disk for a new partition and install Ubuntu (would you recommend 9.1?).

I would recommend you visit [http://www.ubuntu.com/]("http://www.ubuntu.com/getubuntu/download") and download the latest version of ubuntu, for a single installation or the Ubuntu LTS if you are deploying ubuntu across multiple computers such as on a network.
 
> **matmuc said:**
> Probably the Wubi installation is disturbed by some hardware detection problems and so I end up with a live session. Anyway, I think I should not struggle for the perfect Wubi installation but for a good installation of Ubuntu..

Partitioning a hard drive is important.  There are many tools to reisize your partitions and you could download them all if you wish and use them to.  [http://www.partitionwizard.com/]("http://www.partitionwizard.com/") resizes (shrinks/grows) windows partitions, so that windows remains intact. Gparted ( [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/") ), has a live cd that you can use to move partitions although in visa/windowze7 this cause a error, possible due to a failed UUID check on first rebooting to windows.  See : [http://www.howtogeek.com/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") for how to recover in windowze before you do this.  Make sure you de-fragment windowze first.

> **matmuc said:**
> One last question for the moment: is it better to use one partition or maybe 2 (like system/apps and data) and are there recommendations for the size of partitions? Once again, thank you, and greetings from Munich. Mathias

It is better to use one partition.  It is better to know what size partition you want to give to ubuntu.  You do not want to be repartition-ing later just make sure you know how much space to give your ubuntu partition before you install, as best you can.  Make sure you also know the structure of your partitions before you install ubuntu so that you know which partition to install ubuntu to when it asks.

These gui-partition tools make partition-ing a breeze, as long as you are vigilant and double check before you perform any actions.  As always though partitioning carries an element of danger, so back-up important files before you start.

Good Luck.

---

