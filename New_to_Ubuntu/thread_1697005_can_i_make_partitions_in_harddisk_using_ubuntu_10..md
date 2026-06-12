---
title: "can i make partitions in harddisk using ubuntu 10.10"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by midukkandavid on 2011-02-28
I'm new to ubuntu.I have installed ubuntu 10.10 with my 500GB harddisk as a single partition.Can i make new partitions using ubuntu 10.10 like in windows 7.

---

### Post by mikewhatever on 2011-02-28
Yes, you can use the Disk Utility under System->Administration.

---

### Post by midukkandavid on 2011-02-28
I'm presently having my 500 GB harddisk as a single partition and my only OS is ubuntu 10.10 .I want to install windows 7 along with ubuntu.So how can i create new partitions inorder to install windows.

---

### Post by Tabu.it on 2011-02-28
Install Gparted for create new partition with a Graphic interface

---

### Post by metalf8801 on 2011-02-28
If your computer is powerful enough I would installed windows 7 in Virtualbox 

First backup everything you can't afford to lose just in case 

You will need to boot from a live CD that has Gparted or another partitioning program. Ubuntu Live CDs has Gparted 
System > Administration > Gparted Partition Editor 

You do have Gparted installed by default on your install of Ubuntu but you can't use it on the partition it is running on so it wont work for what you are trying to do. 

I would put your windows 7 install on one end of the disk and your Ubuntu partitions (main partition and swap partition) 

Shrink your main Ubuntu partition and move it to the end of your drive so that the next partition is your Swap partition. Leave the free space unallocated. 

Then install Windows 7 

After that you will need to reinstall Grub so that you can boot into Ubuntu [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Grenage on 2011-02-28
> **midukkandavid said:**
> I'm presently having my 500 GB harddisk as a single partition and my only OS is ubuntu 10.10 .I want to install windows 7 along with ubuntu.So how can i create new partitions inorder to install windows.

You'll need to boot from a LiveCD, such as an Ubuntu disc (it has Gparted on it) - you can't make changes to the drive you're using.

Then you can use Gparted to resize your partitions, but **make sure** you have backed up any important data first.

---

### Post by lisati on 2011-02-28
Threads merged

---

### Post by coffeecat on 2011-02-28
I agree with those who recommend Gparted rather than Disk utility in a situation like this. As has been pointed out, you're going to have to do this from the live CD, and the live CD comes with Gparted.

Have a look at this link:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

It contains what you need to know about partitioning together with instructions for using Gparted. When you use Gparted in the live CD, right click on your swap partition (if you have one) and choose swapoff. If you don't, and swap is on a logical partition, you'll find that your extended partition is locked and you won't be able to do much.

---

