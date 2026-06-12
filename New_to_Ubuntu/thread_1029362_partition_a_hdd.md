---
title: "partition a hdd"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by yo.dave on 2009-01-03
I have a 70gb drive for my Dell Insprion 600m Laptop. I have a caddy for the disk so swaping it out if I need Windoze is no problem. I want to format this and install Ubuntu. Best suggestion for the number of partitions and size? I want 'home' to be separate for easy backup. I have listened to a lot of Linux podcasts and researched some but am still confused. 
Thanks in advance
Dave
p.s. - I am excited about leaving the Windoze and the slow bloat.

---

### Post by taurus on 2009-01-03
Maybe something like

/dev/sda1 -> / (10GB)
/dev/sda2 -> swap (2GB)
/dev/sda3 -> /home (whatever left)

---

### Post by yo.dave on 2009-01-03
Thanks
I'll get this done and see how it goes
dave

---

### Post by Dedoimedo on 2009-01-03
Hi,

I'd say:

10GB root.
Swap 2x RAM if you have less than 512MB, 1.5x if you have 512MB-2GB, 2GB for anything else.
10GB fat32 for exchanging of data, stuff with windows.
Rest /home.

Dedoimedo

---

### Post by Paqman on 2009-01-03
> **Dedoimedo said:**
> 
10GB fat32 for exchanging of data, stuff with windows.


You don't need FAT32 for this any more. Ubuntu has had full read/write on NTFS for a while now.

---

### Post by rams123 on 2009-01-03
But windows can't reader ext3 . 

I'm sure there is one soft to make windows understand ext3 . Can anyone pls tell me that ?

---

### Post by teh_yodeler on 2009-01-03
I'm not clear on this - are you using the entire 70GB drive for Ubuntu?  Or do you wish to keep windows on the same drive?

If you want to use the entire hard drive for ubuntu, I would let ubuntu use the whole disk at installation, and go with what it chooses for partition sizes.

The size of your swap partition depends on how much RAM you have.  It should be two times the amount of RAM, so if you have 1 GB RAM use a 2 GB swap.

---

### Post by teh_yodeler on 2009-01-03
> **rams123 said:**
> But windows can't reader ext3 . 

I'm sure there is one soft to make windows understand ext3 . Can anyone pls tell me that ?

[http://www.fs-driver.org/](http://www.fs-driver.org/)
[http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/](http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/)


What brand of Windoze do you have (XP, vista, etc)?

---

### Post by Dedoimedo on 2009-01-03
The fat32 I suggested was so that Windows can use it.

As to ext3 drivers for Windows, they exist. Although I do not recommend them, for several reasons:

An anti-virus running on Windows might accidentally find and delete an important Linux file.
A user not really sure what those funny looking files are might delete a few.
Several programs, especially security and imaging happen to clash sometimes with ext3 drivers, causing unpleasant bsod.

It's much better to use a dedicated partition for data exchange, safer, simpler, more modular.

Dedoimedo

---

### Post by yo.dave on 2009-01-03
i want to do the whole drive Ubuntu...so no Windoze at all. I just need to know how to partition it including what to do about home in a separate partition. I plan just to reinstall the actual orginal drive in thepc if I need windoze at all. I am planning a complete breakout from Microsoft.
Thanks for all the interest
dave

---

### Post by -kg- on 2009-01-03
> **teh_yodeler said:**
> I'm not clear on this - are you using the entire 70GB drive for Ubuntu?  Or do you wish to keep windows on the same drive?

If you want to use the entire hard drive for ubuntu, I would let ubuntu use the whole disk at installation, and go with what it chooses for partition sizes.

The size of your swap partition depends on how much RAM you have.  It should be two times the amount of RAM, so if you have 1 GB RAM use a 2 GB swap.

The only thing about that is that if you let Ubuntu use the whole disk at installation, that implies that you choose the applicable "Guided Installation" option.  If you use that installation option (and if my memory serves me right) this will only create two partitions...a "/" or "/home" partition and a swap partition.


Since yo.dave indicated he wanted a separate "/home" partition, he would need to go the manual route, create his own partitions to the size he wants, flag them as whatever they are, and then install.

Creating a separate "/home" partition after installation is a PITA compared to doing so during installation. (To me, at least)  If you need more information on manual partitioning, see the ["How To Partition"]("https://help.ubuntu.com/community/HowtoPartition") section of the Community Documentation.

<edit> I did a search in the Community Documentation using "separate /home partition" and came up with [a wealth of information on the subject,]("https://help.ubuntu.com/search.html?cx=003883529982892832976%3Ae2vwumte3fq&cof=FORID%3A9&ie=UTF-8&q=%22separate+%2Fhome+partition%22&sa=Search") including ["Moving Mount Points Howto"]("https://help.ubuntu.com/community/MoveMountpointHowto") which has a wealth of information on that subject.

---

### Post by yo.dave on 2009-01-10
I installed Ubuntu with the guided install. It did only give me a 2 partions but it is ok. I think Ubuntu and Linux are great! Glad I've forund them! thanks to all who responded
DAVE

---

