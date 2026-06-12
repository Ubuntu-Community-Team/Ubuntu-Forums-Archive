---
title: "Dual Booting for 8.10"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by feral1939 on 2009-02-08
Hi, I am a very new noob to Ubuntu so bear with me.

I have a dual HDD computer with Vista on "C"(40Mb free) and backups on "D"(52Mb free). I have been trying the Live CD and would like to install 8.10 on my computer.

1st Q: I want to use dual booting initially until I give Vista the flick so is it possible to install it on the D drive or will it have to be installed on the C drive for dual booting?

2nd Q: When I tried to install it, the partitioner only selected the D drive (largest free space??) so how can I select the C drive if I have to install it there for dual booting? I think the way around this problem is to disconnect the D drive.

3rd Q: The installer wants to use ALL the free space on the drive but I cannot see how to allocate the partitions to leave a bit of space on the Vista partition in case I need some.

I look forward to suggestions from the community as to how I can overcome these problems, hopefully there won't be any more and I thank you for your help in advance.

---

### Post by Temposs on 2009-02-08
hi feral,

Here is a guide for installing Ubuntu while dual booting with windows: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

The section called "Resizing Partitions Using the Ubuntu Installer" should help you, in particular, but feel free to read the whole thing.

It is possible to install Ubuntu on your second hard drive for dual booting, but it will be much more of a pain. The easiest thing to do is install it on the same hard drive as Windows. But, in case you want to look into it: [https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

---

### Post by handydan918 on 2009-02-08
> **Temposs said:**
> 
It is possible to install Ubuntu on your second hard drive for dual booting, but it will be much more of a pain. The easiest thing to do is install it on the same hard drive as Windows. But, in case you want to look into it: [https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

This link is addressing a different scenario. There is nothing difficult about installing Ubu on the second harddrive, as long as you don't get clever or cautious or stupid and put grub somewhere besides the MBR.

---

### Post by Temposs on 2009-02-08
I defer to handydan, as usual :-)

---

### Post by neu2buntu on 2009-02-08
i take it u mean 40 and 52 "gb" not "mb" ?

answer to question (1) as long as your bios allows you to boot of disk "d" there should be no prob installing there.  on bootup hit f2 or esc or f12 to see bios

(2) does drive "c" not show up in the installer? you should be able to choose either drive from here or manual install, i wouldnt disconnect any drives during install if u dual boot as the boot manager "grub" controls all partitions in dual boot . the grub boot loader has to be installed on the ubuntu partition or if u get this wrong u will wipe windows bootloader

(3)it will be ok to use ALL the free space ,because you can resize it again and free it up for windows vista with a tool "gparted" that u can easily install in ubuntu.

---

### Post by feral1939 on 2009-02-08
Hi,  Thank you for your response.  It looks as though I have to put it on the C drive after all.

---

### Post by feral1939 on 2009-02-08
Hi,  Thanks for your reply.  I will put it on the C drive

---

### Post by feral1939 on 2009-02-08
Pipped at the post.  Thanks anyway.

---

### Post by feral1939 on 2009-02-08
Hi, Thanks for your reply. My mistake, I meant gb not mb.
 re Q2, the option of selecting either drive was not available in the partitioner. It seems to me that it selected the drive with the most free space. I have previously disconnected the D drive with out any problems but to take your point, I wouldn't disconnect it during installation and there is only one partition on C at present.
re Q3, where can I find the tool "gparted" to install.
Many thanks to all of you who answered my post. If I have further problems I will certainly post them as I am very impressed with the replies.  Thanks again.

---

### Post by neu2buntu on 2009-02-09
does the bios allow you to boot from drive "D" ?  if not i think you will have to choose disk "C" for your install (this would probably) be your best option)   remember todo disk check and defragment in windows before installing ubuntu  (right click on windows disk "C" choose > properties > tools >check now & > defragment now )  [2]   and i cant remember if "gparted" is part of 8.10 (partition editor) if not u can install it by going to > system > administration > synaptic package manager > and in searh (magnifying glass icon) type "gparted" tick it for install and apply!!!     there are 2 more ways of installingt software on ubuntu  ,the command line(terminal) and add/remove.

---

### Post by chaplanger on 2009-02-09
It is not necessary to put Ubuntu on your C drive.  I have a two HDD system.  HDD 1 carries WIN XP; HDD 2 carries Ubuntu 8.10.  Ubuntu sets up the Master Boot Record and is not confused by a multiple drive system.

When you begin the installation of Ubuntu off of the Live CD it will show you all the drive and drive spaces available to format for Ubuntu. You can choose where you want to set it up and how much space you want to allocate.  

Another option for you is to set up your second HDD as strictly Ubuntu land.  Allowing Ubuntu to overwrite the entire HDD.  Once Ubuntu is set up you can still steal a peak at your WIN system through Ubuntu.  You can even copy folders from WIN into Ubuntu (i.e. your "My documents" folder or anything other data you wish to back up)

This is what I currently do as a third means of backing up my WIN data.  I have an external HDD that automatically does this through WIN and then periodically I also back up my WIN documents to a folder I created in Ubuntu.

You will soon discover that Ubuntu offers a bit more flexibility than WIN.  (Although my WIN XP installation identified my primary HDD as Drive F on the WIN system and still works just fine with a few hiccups -- all unrelated to Ubuntu . . . but that is another story. . .)

Happy computing as you discover the wonderful world of Ubuntu.

---

### Post by feral1939 on 2009-02-09
> **neu2buntu said:**
> does the bios allow you to boot from drive "D" ?  if not i think you will have to choose disk "C" for your install (this would probably) be your best option)   remember todo disk check and defragment in windows before installing ubuntu  (right click on windows disk "C" choose > properties > tools >check now & > defragment now )  [2]   and i cant remember if "gparted" is part of 8.10 (partition editor) if not u can install it by going to > system > administration > synaptic package manager > and in searh (magnifying glass icon) type "gparted" tick it for install and apply!!!     there are 2 more ways of installingt software on ubuntu  ,the command line(terminal) and add/remove.

Many thanks, I will try the above after installation.

---

### Post by unplugged23 on 2009-02-09
you should be fine installing it to the d drive. also you might want to specify a start cylinder if you dont want to loose all of the back up. and if you want to change the amount of space on the drive the partition takes up you have to do a manual partition. not an automatic one. Good Luck!

---

### Post by feral1939 on 2009-02-10
> **chaplanger said:**
> It is not necessary to put Ubuntu on your C drive.  I have a two HDD system.  HDD 1 carries WIN XP; HDD 2 carries Ubuntu 8.10.  Ubuntu sets up the Master Boot Record and is not confused by a multiple drive system.

When you begin the installation of Ubuntu off of the Live CD it will show you all the drive and drive spaces available to format for Ubuntu. You can choose where you want to set it up and how much space you want to allocate.  

Another option for you is to set up your second HDD as strictly Ubuntu land.  Allowing Ubuntu to overwrite the entire HDD.  Once Ubuntu is set up you can still steal a peak at your WIN system through Ubuntu.  You can even copy folders from WIN into Ubuntu (i.e. your "My documents" folder or anything other data you wish to back up)

This is what I currently do as a third means of backing up my WIN data.  I have an external HDD that automatically does this through WIN and then periodically I also back up my WIN documents to a folder I created in Ubuntu.

You will soon discover that Ubuntu offers a bit more flexibility than WIN.  (Although my WIN XP installation identified my primary HDD as Drive F on the WIN system and still works just fine with a few hiccups -- all unrelated to Ubuntu . . . but that is another story. . .)

Happy computing as you discover the wonderful world of Ubuntu.

Many thanks for your help I can't wait to get Ubuntu up and running as I am fed up with Windows and all the control it tries to exert. One problem is that the Ubuntu partitioner does not "list" all the drives (as you suggested) on my PC and apparently only selects the one with the most free space, in my case, the 'D' drive. Perhaps the experts could look into this.

---

### Post by chaplanger on 2009-02-19
Hmmm. . . you say you can't see all of your hard drives. . . 
Have you tried booting the Live CD and beginning the install from within that session. . . This was how I saw all of the HDDs on my system.  Just make certain that if you install in this manner, you know which HDD you want UBUNTU on -- it can be easy to mistakenly select the wrong HDD.

Best of luck.

---

