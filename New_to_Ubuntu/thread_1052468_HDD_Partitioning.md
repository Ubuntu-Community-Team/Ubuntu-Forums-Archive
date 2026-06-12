---
title: "HDD Partitioning"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by amsum on 2009-01-27
I am quite new to Ubuntu. I have 2 hard drives 80GB (with XP SP2 and four drives in NTFS) and 160GB (where I intend to install Ubuntu). Can someone suggest in partitioning the 160GB harddrive so that I can access all the 160GB partitioned drives even booting from Windows XP and vice versa. I am lost in NTFS, FAT32 and EXT3 file systems. I want to know ideally how many drives I should create and in which file system. (I would love to have four drives though).

---

### Post by sadicote on 2009-01-27
I am no veteran but this much i will safely venture, install Windows before Ubuntu or you may not be able to boot into Windows, and do not format any partition with Windows except the one on which you install it, and if your HDD capacity is greater than 40 GB go for NTFS (quick).

---

### Post by bodhi.zazen on 2009-01-27
> **amsum said:**
> I am quite new to Ubuntu. I have 2 hard drives 80GB (with XP SP2 and four drives in NTFS) and 160GB (where I intend to install Ubuntu). Can someone suggest in partitioning the 160GB harddrive so that I can access all the 160GB partitioned drives even booting from Windows XP and vice versa. I am lost in NTFS, FAT32 and EXT3 file systems. I want to know ideally how many drives I should create and in which file system. (I would love to have four drives though).

IMO you are best off with NTFS if you ar going to share the drives with windows. 

Some basic info :

[http://www.aumha.org/win5/a/ntfs.php](http://www.aumha.org/win5/a/ntfs.php)

[http://en.wikipedia.org/wiki/File_system](http://en.wikipedia.org/wiki/File_system)

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by bumanie on 2009-01-27
I am a bit confused with your description of having two hard drives and then saying you have four ntfs drives. Do you mean 4 ntfs partitons?
Natively, linux now supports read/write to ntfs so accessing windows from ubuntu is no problem, thus leaving your present drive as ntfs is fine. There a a couple of ways of accessing linux from within windows, this one is probably the best [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) , but it is not as refined as ntfs-3g used from within linux. Also look [here]("http://www.howtoforge.com/access-linux-partitions-from-windows").

---

### Post by Clippy on 2009-01-27
This site helped me when partitioning my HD, might be useful to you too.  Good luck!

[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

---

### Post by Noour on 2009-01-27
If I understand well, you have 1x 80GB HDD with 4 partitions on which you run XP2 amd 1x new 160 GB HDD on which you are planning to install Linux Ubuntu.

As operating systems will be on separate HDDs, the way the hardware is connected is very important. Change the emplacement of 
your Windows XP HDD so it becomes secondary master. The HDD you are planning to install Ubuntu must be primary master.

If you dont have experience with Linux HDD installation, my advice is to install Ubuntu on the 160 GB without the XP HDD connected to the computer (to avoid problems). Ubuntu will partition the 160 HDD for you (swap and ext3, everything automatically).

With operating systems installed on both HDDs, it will be more easy for you to detect the emplacement of the primary and secondary HDDs (when you remove the first, the second takes its place, when both are connected ...). Once you get Linux HDD as primary and XP as secondary master, reinstall Linux Ubuntu with XP HDD in the computer. If your XP HDD is secondary master, Linux installation process will detect it automaticaly and will configure the GRUB loader.

You ll be able to access the XP logical and primary drives from Ubuntu after you give a password (read/write). To access the Linux drives from XP, you'll need to purchase some software or to look for a freeware solution. The XP partition is magic ;-). Access speed from Ubuntu is ok.  

(maybe you'll have to play with jumpers to get it work correctly - Depends on your hardware).

cheers. :popcorn:

---

### Post by webmiester on 2009-01-27
My simple solution would be to simply use windows to partition the drives when you install windows as you like... then after loading windows, insert the ubuntu 8.10 cd, and install ubuntu through a windows installation (wubi).  Wubi won't make a separate ubuntu partition anymore, so you get to keep the existing partitions you've set in windows.  If you set 4 partitions, that's how it will stay.

In my opinion though, I recommend that you keep a separate partition for linux which windows won't see.  In this way, even if your windows is violently attacked by a windows virus, your linux data remains safe and you can recover some of your data through the linux partition.

---

### Post by amsum on 2009-01-28
Thanks all, will go through all the suggestions. I have one more probs here. In my 160 HDD which had 5 NTFS partitions and had some data on the last four partitions. During Ubuntu installation, I left last four partition untouched and now though the Ubuntu is working absolutely fine, I am not able to open last four drives and it is not able to mount. So, I took the help of Gparted but there is no option for NTFS formatting. Looks like I will have to format only in FAT32 file system. 

Can I access the drives without formatting so that I dont lose my existing data?

---

### Post by darknight2183 on 2009-01-28
For NTFS, gparted relies on the ntfs-3g libraries.  It should have come by default when you installed ubuntu, but if you are missing it there are two ways of getting it
 1.) Command Line: Goto Applications > Accessories > Terminal and type "sudo apt-get install ntfs-3g"
 2.) Synaptic: Goto System > Administration > Synaptic and search/install ntfs-3g

Than just relaunch gparted

---

### Post by darknight2183 on 2009-01-28
I also recommend installing the ubuntu-restricted-extras and libdvdcss2.  It gives you some extra interprobility. For libdvdcss2 you need to make sure the medibuntu library is enabled; instuctions can be found on the following link: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

