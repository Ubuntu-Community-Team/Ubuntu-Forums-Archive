---
title: "Noobie,Linux philosophy,kernel, partition"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by c0stanz0 on 2009-05-05
Hello there,
I am absolute noobie/newbie at Linux so apologize if my questions are stupids!I got no friends running Linux and the only contact was at youtube and this forum!I kinda like them so I was keeping an eye on this forums to get into the "Linux philosophy" and finally on last Friday, i just installed the Jaunty as the only OS on my laptop. Things gone well and smoothly!Although i got some questions regarding the way Ubuntu works, please keep in mind i am not a PC expert and even worst not a programing expert.

Here are my questions:

1)Is there a way to partition the jaunty and give the name "C" at the new partition?Not only partition but give it the name "C" so the stupid recovery cd can read it!

2)If we got two partitions, partitionA got the Jaunty(root) and partitionB is for back up files, like music, videos, pictures etc. All the things we dont want to waste and re add if we gonna format the PC. Now lets say we want to install the next Ubuntu version to partitionA, would be the partitionB still readable?Should i have to re-partition or do anything to the partitionB?

3)Like above, two partitions, A and B. A jaunty and B the back up files. When i install the new version of Ubuntu and upgrade the kernel should i install kernel at partition B too?Because will be partitioned on old version?When i upgrade the kernel generally should i do anything to partitions? I think kernel has to do with the OS only regardless partitions, but reading about the kernel at web got confused about the real abilities and how we get the most of it!Noobie i told you!

4)What is better to do?First install/upgrade kernel then the drivers like graphics sound etc or the other way around?Does it really matter?Is kernel like the regedit we used to have at windows?

Really sorry if all these are answered to other topics, i think they do, but i cant get out the answers of them, all these days i had too much info in sort time and i got confused!I know should be stupid questions but thought to ask to be sure....that i am stupid lololol!


Ty a lot in advance guys, have fun


P.S.Remember i am totally noobie at linux and programing etc etc!

P.S.2 Sorry for the big post! Firt time i post to a forum!

---

### Post by Insanity01 on 2009-05-05
answer on question 4, id install your wanted OS, and upgrade it to newest version BEFORE doing drivers etc... you just never know if some drivers are difrent etc.. and also some packets might not work anymore after update so u got to reinstall em (esound becomes pulseaudio again for example)

---

### Post by lloyd_b on 2009-05-05
1.  What "recovery CD" are you talking about?  If that machine is Ubuntu-only, then the Live CD is effectively your "recovery CD" for that machine.

2.  It is *very* common practice to have "/" (the root filesystem) and "/home" (where user files are stored) be separate partitions, explicitly for the reasons you mention.  I've been using the same "/home" partition for the last 4 Ubuntu versions - I just have to remember to *not* format it during the install process.

3.  Any partition that you create should be readable by any future version for a long time to come.  You do *not* have to "install" the kernel for any partition except the "root" partition.  In fact, don't even worry about where the kernel is installed - the package managers handle all of that for you.

4.  As previously answered, upgrade to the latest kernel, then upgrade your video drivers.

Lloyd B.

---

### Post by meho_r on 2009-05-05
Just to add on nr.2. When installing new Ubuntu edition, make sure you chose "manual" partitioning, then just click on Partition A and then "Edit", after which you decide which filesystem to use and if the partition is going to be formatted (and it should). As for Partition B, click > "Edit" and then only set mount location (i.e. /home), but DO NOT format it. That's all.

---

### Post by aparigraha on 2009-05-05
First of all. Drives and partitions are not named like in Windows. Say you have 2 separate drives and each drive has 2 partitions. Ubuntu will recognize them as follows (letters may vary):

/dev/sda1
/dev/sda2
/dev/sdb1
/dev/sdb2

When you start your system the file /boot/grub/menu.lst reads and boots where it finds a Ubuntu setup. /boot/grub/menu.lst have different names for the physical drives and partitions:

(hd0,0)
(hd0,1)
(hd1,0)
(hd1,1)


1) 

You can read it from the CD without naming it "C". On Linux you don't usually name drives like you do in Windows. You just have to "show" the system where the drive is that you want to mount (read). This is done through **fstab**. But you can label drives and have them mounted according to label. So if you label your drive "C" you can have it mounted (and readable/writable and executable) through fstab. If you have no idea what mounting drives or **fstab** is about - look here: [http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")  

2)

If you install your next Ubuntu on A, nothing on B should be changed and B should still be readable. If it isn't - **fstab** again :) But you could backup your **/home/YOUR_USERNAME/** folder and use it and all your settings again on the new Ubuntu version. A lot of people (me included) partition before installing. I have one root-partition and a separate home-partition, plus a couple of extra drives. Some people have separate swap- and boot-partitions.

3)

Kernel updates are done automatically (if you want to), so there is really no need to worry or change anything. New kernels will move into your root partition. A problem with partitions you *might* run into when the kernel is updated is that the new kernel is set to boot at a different partition than you previously did... **/boot/grub/menu.lst** has to be changed a bit. 

4)

Partition manually, Install - and after installation from CD open a Terminal Window and:

**sudo apt-get update && sudo apt-get upgrade**

---

