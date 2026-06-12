---
title: "Installing Win 7 then dual boot ubuntu"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Cyclefish on 2011-01-13
This is my first forum posting ever. I am loving this ubuntu stuff! I am installing windows 7 on my HP Pavilion desktop to replace XP. Then I want to set it up to dual boot with ubuntu. My question is: Are there tips on the installing of Win 7 that will make the dual boot install easier or more optimized? I'm thinking of the HD partitioning.  Also, is there a process for the dual boot install documented somewhere? Thanks.

---

### Post by Rex Bouwense on 2011-01-13
Welcome to the forums.  Look here:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by KingYaba on 2011-01-13
This is what I'd do:

Boot the Ubuntu Live CD and partition my hard drive with GParted.

Then I'd boot the Win 7 DVD and install Windows 7 on my #2 partition.

Then once Windows is installed, I'd install Ubuntu on partition #1. That way you can have GRUB automatically configured. If you install Windows after Ubuntu, you'll have to reconfigure GRUB because that Windows loader thing will take over.

---

### Post by wilee-nilee on 2011-01-13
> **Cyclefish said:**
> This is my first forum posting ever. I am loving this ubuntu stuff! I am installing windows 7 on my HP Pavilion desktop to replace XP. Then I want to set it up to dual boot with ubuntu. My question is: Are there tips on the installing of Win 7 that will make the dual boot install easier or more optimized? I'm thinking of the HD partitioning.  Also, is there a process for the dual boot install documented somewhere? Thanks.

Boot the live Ubuntu cd to a try ubuntu live session, go to system-admin-gparted take a screehot of gparted and post it. If you have more then one HD then use the dropdown in the top right corner of gparted to take a screenshot of every HD.

---

### Post by Smart Viking on 2011-01-13
It is also important to partition the windows partition as a NTFS file system, because that is the files system windows use. For the linux partition, ext4 is a good choice.

---

### Post by Cyclefish on 2011-01-13
Great info. Thanks. And fast too!

---

### Post by rburkartjo on 2011-01-13
god luck cycle just did the same thing a couple of weeks ago. though i added another hard drive and put 7 on it.

---

### Post by tahitiwibble on 2011-01-13
I may be too late here but just in case you need it here are a couple of priceless links for what you need to do ........ very clear and concise for us newbies :)

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by horrerbaba on 2011-03-08
hello everyone 

i need dual boot tool and instruction.

i want install windows xp and Ubuntu in our system.

my system model no is GX520 and 500GB hard Drive.

---

