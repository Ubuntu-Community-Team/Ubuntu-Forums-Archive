---
title: "Complete OS wipe"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by Kirkland14 on 2010-06-18
I currently have wubi going on win7.  I want to completely wipe my HDD and start over by actually dual booting and put win 7 and ubuntu back on separately not using wubi.  I have scoured the internet for ways to wipe my drive but I can't really find anything exactly what I'm looking for.  I have a dell inspirion 1545.  Thanks

Kevin

---

### Post by Neezer on 2010-06-18
If you have a win7 disc you could install that on a partition on the hard disk. then install ubuntu 10.04 on the other partition. that should work. I know that if you want to dual boot, it is easier if you put windows on before ubuntu. It has something to do with the master boot record or something like that.

If you don't have a win7 disk, then I'm not too sure how you would go about it.

---

### Post by wilee-nilee on 2010-06-18
> **Kirkland14 said:**
> I currently have wubi going on win7.  I want to completely wipe my HDD and start over by actually dual booting and put win 7 and ubuntu back on separately not using wubi.  I have scoured the internet for ways to wipe my drive but I can't really find anything exactly what I'm looking for.  I have a dell inspirion 1545.  Thanks

Kevin

Do you just want to clean for install or so nothing is recoverable?

A simple delete with gparted and a install with thw W7 and Ubuntu discs would work. You could also just delete the W7 partitions from a W7 dvd or overwrite the whole HD. A custom W7 install could clean and make the partition to the size you want so you don't have to mess with resizing it. There are a bunch of ways to do it.

---

### Post by wilee-nilee on 2010-06-18
> **Neezer said:**
> If you have a win7 disc you could install that on a partition on the hard disk. then install ubuntu 10.04 on the other partition. that should work. I know that if you want to dual boot, it is easier if you put windows on before ubuntu. It has something to do with the master boot record or something like that.

If you don't have a win7 disk, then I'm not too sure how you would go about it.

It doesn't matter which order you install, unless your not familiar with loading the bootloader to the mbr.;)

---

### Post by Kirkland14 on 2010-06-18
What I'm basically trying to do is start from scratch and then re-add ubuntu and keep my win7 to the bare minimum.  I basically only need it for my iphone so I don't want all its programs taking up space.  I figured it would be easier to just get rid of everything on the HDD, load my win7, then ubuntu.  I just don't know how to completely wipe it clean.  I'm pretty new at this stuff.  I have the win7 disk.  Thanks

Kevin

---

### Post by I Forgot My Username on 2010-06-18
I suggest you install W7 first.  It has a good partitioner built-it to the installer, I can't remember the details, but it's really straight forward.  It has an option to delete partitions, do that for all of them, then create one the size you want for w7.  After you install W7, install Ubuntu to the rest of the disk.

---

### Post by oomar on 2010-06-18
Requirements
1. an Ubuntu liveCD
2. A windows installations disk

Precedure
1. You can either boot up the liveCD and wipe your drive with Gparted or you can use the Windows 7 installation disk to delete the partitions and install on a new one.
2. After installing Windows 7 (you MUST install windows first I think) boot up your ubuntu disk and install ubuntu.

if you need a more detailed answer just PM me.

---

### Post by wilee-nilee on 2010-06-19
Just so we know, with a fresh install it is easier to install windows first. The only time you would have problems with a windows install is if there is another windows on the HD and you want W7 to have XP or Vista in it's bootloader. You can install W7 or any MS distro after a Ubuntu or Linux install If you know how to load the mbr **_this is the truth_**.

---

### Post by k3lt01 on 2010-06-19
Get your Windows disk and boot to it. Follow the prompts and resize the Windows partition to the size you want it. I'd make 2 partitions for Windows, the first being C:\ and the 2nd being D:\ that way if anything happens you can still keep valuable information away from the OS proper. If you do it this way make sure C:\ is at least 20gb. Windows is best as NTFS don't choose FAT.

After you have installed Windows boot it up and make sure it works ok. Then shut the machine down.

Now boot your machine with the Ubuntu disk in it. Follow the prompts. Set your partitions up in the remaining free space with approximately 10gb as / 2 gb SWAP and the rest as /home. Ubuntu's native file format is ext4 and it is probably best to stick with it. Let it install, reboot and start Linux and then start Windows making sure GRUB can see both of them.

---

### Post by Kirkland14 on 2010-06-19
So I did I reinstall of win7 and now it seems that I have even less space on my c: drive. Plus when I'm in the linux os it's now telling me that I have super low disk space.  I would really just like to know how to rm the whole drive and start from absolute scratch. everything I need is stored safely on an external drive.  thanks

Kevin

---

### Post by k3lt01 on 2010-06-19
> **Kirkland14 said:**
>  I would really just like to know how to rm the whole drive and start from absolute scratch. everything I need is stored safely on an external drive.  thanks

KevinRead the post above your last one and that will tell you how to do it.

---

### Post by Kirkland14 on 2010-06-19
I got it all figured out now. Thanks for everyones help.

Kevin

---

