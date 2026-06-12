---
title: "Is it safe to do this?"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by mmitt on 2009-04-04
I'm trying to install Ubuntu on my school laptop, but I have run into a small problem. I want to install it on it's own partition, but when I try to do it through manual, it tells me that I don't have a root partition defined (or something like that.) I have heard that if I use "guided" then I will need to use a Vista Dvd to repair the Vista partition. The problem here is that I don't have a Vista install disk, so will using "guided" cause me to need to repair it before I use it again? Thanks!

---

### Post by DGortze380 on 2009-04-04
> **mmitt said:**
> I'm trying to install Ubuntu on my school laptop, but I have run into a small problem. I want to install it on it's own partition, but when I try to do it through manual, it tells me that I don't have a root partition defined (or something like that.) I have heard that if I use "guided" then I will need to use a Vista Dvd to repair the Vista partition. The problem here is that I don't have a Vista install disk, so will using "guided" cause me to need to repair it before I use it again? Thanks!

You need to create the partitions and select a mount point as root "/" for one of the paritions

---

### Post by damis648 on 2009-04-04
You do not need to use a Vista DVD to repair anything. Just use Guided, and resize your windows partition to fit Ubuntu.

---

### Post by mmitt on 2009-04-04
> **DGortze380 said:**
> You need to create the partitions and select a mount point as root "/" for one of the paritions
I tried that but it only gave me two choices: /windows and /dos. 
> **damis648 said:**
> You do not need to use a Vista DVD to repair anything. Just use Guided, and resize your windows partition to fit Ubuntu.
Ok then, I'm going to trust you.

---

### Post by JK3mp on 2009-04-04
> **damis648 said:**
> You do not need to use a Vista DVD to repair anything. Just use Guided, and resize your windows partition to fit Ubuntu.

I thought that the guided install by default used the whole disk? Meaning windows no more?

---

### Post by mmitt on 2009-04-04
> **JK3mp said:**
> I thought that the guided install by default used the whole disk? Meaning windows no more?
Nah there is another one where you select how much you want ubuntu to take up and stuff.

---

### Post by ubuntu27 on 2009-04-04
DO NOT use Guided partitioning if you want to Keep your current OS (.e.g. Windows).

Guided partitioning uses the whole Hard Drive to install Ubuntu Linux.

Choose to use Manual Partitioning or "Choose free space" (something along those lines)

At least, that's how it is in [Ubuntu 8.04]("http://www.linuxdynasty.org/ubuntu-804-install-screenshots.html"). I forgot how it is in Ubuntu 8.10.

> **mmitt said:**
> Nah there is another one where you select how much you want ubuntu to take up and stuff.

You have confidence. I believe you will be all right.

---

### Post by presence1960 on 2009-04-04
> **ubuntu27 said:**
> DO NOT use Guided partitioning if you want to Keep your current OS (.e.g. Windows).

Guided partitioning uses the whole Hard Drive to install Ubuntu Linux.

Choose to use Manual Partitioning or "Choose free space" (something along those lines)

here it is: you want guided resize

here is a link with photos to help you thru the install process: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Make sure you defrag Vista first. I am not sure because I have XP but you may want to check around the forums because there were some issues I believe with resizing Vista with  gparted. I recall reading where it was stated to use Vista partitioner in Disk Management to shrink the Vista partition. I would look into this prior to changing your partitions. **_And of course back up your data first!_**

---

### Post by drowner on 2009-04-04
Before you begin:

I have never used Vista, but I understand that BEFORE installing ubuntu you should prepare the partition in Vista, or Vista will not be pleased on reboot.

is this still the case?

---

### Post by 3rdalbum on 2009-04-04
You need to defragment the Windows partition from within Windows, before doing any partition resizing.

---

### Post by jmcgovern on 2009-04-05
drowner is correct.  You need to resize the partition from WITHIN Vista, or the next time you try to boot vista it'll throw a hissy fit because the partition table wont match what Vista thinks it should be, and you wont be able to boot till you do some wrangling with GRUB and a live CD.

---

### Post by damis648 on 2009-04-05
> **jmcgovern said:**
> drowner is correct.  You need to resize the partition from WITHIN Vista, or the next time you try to boot vista it'll throw a hissy fit because the partition table wont match what Vista thinks it should be, and you wont be able to boot till you do some wrangling with GRUB and a live CD.

I think they fixed that, because I never needed to do that. Ubiquity took care of all of it. 0.o

---

### Post by JK3mp on 2009-04-05
Either way its pretty easy to just use windows to resize then use freespace option i believe...i've never seen the guided resize option.....but apparently its there, lol. Guess im blind :S

---

### Post by majamba on 2009-04-05
use windows to resize the partion so you don't corrupt and latter use the gparted tool to seet the root and swap partion
and it always safe to use linux

---

### Post by JK3mp on 2009-04-05
> **majamba said:**
> use windows to resize the partion so you don't corrupt and latter use the gparted tool to seet the root and swap partion
and it always safe to use linux

I think me saying it the third time pretty much over killed it myself ;)

---

### Post by bodhi.zazen on 2009-04-05
I think you should back up all your data and be prepared to re-install Vista if needed.

Otherwise you are playing with fire as one mistake and you will have problems.

Because you are unfamiliar with linux I strongly suggest wubi, which will not affect Vista.

If you wish to re-partition your hard drive :

1. defragment vista first.

2. gparted works just fine for some people, myself included. I have resized vista partitions several times on several machines and have never had a problem. Personally I find the partitioning tool in vista to be quite crude.

With that said, some people have had problems so you should google to see how to fix them (it is not hard, but I do not know how to do it).

3. Guided partitioning will NOT use the entire disk in any edition of Ubuntu UNLESS you tell it to. The initial picture makes it appear on the first screen that it will, but if you hit the next button you will have a better view of your options. None of the ubuntu installers will delete partions without asking you to confirm your choice.

Really, I strongly suggest you read the installation documentation as that is the best source of advice. If you need to ask these basic questions, you need to read more because a small mistake means diaster.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml)

---

### Post by snkiz on 2009-04-05
> **mmitt said:**
> I tried that but it only gave me two choices: /windows and /dos. 


everyone missed this he has to format a partition for linux that one is dos

---

### Post by kansasnoob on 2009-04-05
Always resize Vista partitions using Vista's own partitioning tools! Like this:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

Or you'll end up needing to do something like this:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

Case in point:

[http://ubuntuforums.org/showthread.php?t=1115985](http://ubuntuforums.org/showthread.php?t=1115985)

---

### Post by -kg- on 2009-04-05
> **snkiz said:**
> everyone missed this he has to format a partition for linux that one is dos

The Live CD installer does not create Windows partitions, nor will they give you the option of marking ext partitions as /windows or /dos.  That wouldn't make sense in a Linux installer.  Likely he was looking at the existing partitions instead of where to mark the partitions he is creating.

There seems to be a paucity of information on how to use the Manual Partitioning part of the Live CD graphical installer.  At least I haven't found any yet.  I'll do some more searching and see what I can come up with.

---

### Post by mmitt on 2009-04-05
Yeah, I figured out what I was doing wrong. I was trying to make the root partition one of my windows partitions... Because I was so tired last night. 

But I just shrunk about 35 Gigabytes of disk space for ubuntu. 

But I still have a small problem. I am not 100% new to Linux, but the Manual partitioning confuses me a bit, but I don't want to resize the Vista partition. 35 Gigs is plenty, but the guided options don't let me just leave one partition alone. So my question is: Can I let Ubuntu make it's partitions for me from free space while not touching Vista?

Thanks for the responses everyone, I learned a lot.

---

### Post by bodhi.zazen on 2009-04-05
> **mmitt said:**
> But I still have a small problem. I am not 100% new to Linux, but the Manual partitioning confuses me a bit, but I don't want to resize the Vista partition. 35 Gigs is plenty, but the guided options don't let me just leave one partition alone. So my question is: Can I let Ubuntu make it's partitions for me from free space while not touching Vista?

Thanks for the responses everyone, I learned a lot.

You can install Ubuntu into the free space on Vista with a wubi install.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

[http://www.howtoforge.com/wubi_ubuntu_on_windows](http://www.howtoforge.com/wubi_ubuntu_on_windows)

Otherwise, no, if you are booting the Ubuntu live CD and looking at partitioning inn the installer, you will need to resize (make smaller) your Vista partition with all that it entails.

---

### Post by mmitt on 2009-04-05
Eh. Thanks, I ended up just going for it. Then Vista threw a hissy fit, but I'm pretty sure that my recovery partition saved me. Thanks!

---

### Post by -kg- on 2009-04-05
> Otherwise, no, if you are booting the Ubuntu live CD and looking at partitioning inn the installer, you will need to resize (make smaller) your Vista partition with all that it entails.

Uh, perhaps it isn't the same in other versions of Ubuntu, but in 8.04 there is a selection of "Guided Install - Use Largest Contiguous Free Space."  Is that missing in subsequent versions?

Using that method, you would not resize any of the existing partitions; just create the Ubuntu partitions in free space (Considering, of course, that you have sufficient free space).

---

### Post by ubuntu27 on 2009-04-05
> **-kg- said:**
> Uh, perhaps it isn't the same in other versions of Ubuntu, but in 8.04 there is a selection of "Guided Install - Use Largest Contiguous Free Space."  Is that missing in subsequent versions?

Using that method, you would not resize any of the existing partitions; just create the Ubuntu partitions in free space (Considering, of course, that you have sufficient free space).

Since Ubuntu 8.10 (Intrepid Ibex), another option was added. 

There is now two guided partitioning. One is where it uses the whole disk, and the other one is where it uses the free space available.

---

### Post by ninjapirate89 on 2009-04-05
> **mmitt said:**
> I'm trying to install Ubuntu on my school laptop, but I have run into a small problem. I want to install it on it's own partition, but when I try to do it through manual, it tells me that I don't have a root partition defined (or something like that.) I have heard that if I use "guided" then I will need to use a Vista Dvd to repair the Vista partition. The problem here is that I don't have a Vista install disk, so will using "guided" cause me to need to repair it before I use it again? Thanks!

When you say it is a school laptop do you mean it is your laptop for school or the laptop actually belongs to the school. It the latter is the case then you should probably go with wubi since I doubt the school would like it very much if you modified the computer in any way.

---

### Post by bodhi.zazen on 2009-04-05
> **-kg- said:**
> Uh, perhaps it isn't the same in other versions of Ubuntu, but in 8.04 there is a selection of "Guided Install - Use Largest Contiguous Free Space."  Is that missing in subsequent versions?

Using that method, you would not resize any of the existing partitions; just create the Ubuntu partitions in free space (Considering, of course, that you have sufficient free space).

There are two option to install Ubuntu. 

The first is the "standard" way, by booting a live CD. When using this method, when you use largest free space, this will resize existing partitions and add partitions for Ubuntu. The only exception to this would be if the disk was already partitioned with free space available for Ubuntu. This would be rare with a default installation of Vista.

The second method, as I have said, is to use wubi. With a wubi install, Ubuntu is installed into a file in Windows and the disk partitions are unchanged.

---

