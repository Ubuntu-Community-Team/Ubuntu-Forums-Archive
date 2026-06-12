---
title: "How to install 10.04 on 2 nd Internal Harddrive"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by Eastwood1 on 2011-07-03
I have a 1TB Harddrive with Windows 7 and a second Internal Harddrive 80 Gbyte completely empty on which I would like to install Ubuntu 10.04. I tried to install 10.04 with Ubuntu image disc 10.04 but nowhere do I get the choice to install it on the 80 Gig.
 
Am I doing something wrong?

---

### Post by frankbooth on 2011-07-03
[SIZE="3"][COLOR="Red"]**REMEMBER TO BE CAREFUL WHEN PARTITIONING DRIVES.**[/COLOR][/SIZE]

Once you reach the partitioner of the install (at the end, before hitting 'Install') you should be able to choose which HDD you want to install Ubuntu to.

Since you have 2 HDD's with different sizes it won't be hard to choose the right disk.

The drop-down menu should list your 1TB disk and your 80GB disk, it usually looks like this:

1TB Name-of-Manufacturer
80GB Name-of-Manufacturer

Choose the 80GB disk and select the option 'use entire disk' unless you want to  partition it manually.

If you don't have the option to choose your 80GB disk, make sure it's connected properly and that it's detected by the motherboard in the BIOS.

**EDIT:** Here's a screenshot of the menu and options I'm talking about in the post:

[Img]http://c-nergy.be/blog/wp-content/uploads/setup5.png[/img]

---

### Post by Eastwood1 on 2011-07-07
> **frankbooth said:**
> [SIZE=3][COLOR=red]**REMEMBER TO BE CAREFUL WHEN PARTITIONING DRIVES.**[/COLOR][/SIZE]
 
Once you reach the partitioner of the install (at the end, before hitting 'Install') you should be able to choose which HDD you want to install Ubuntu to.
 
Since you have 2 HDD's with different sizes it won't be hard to choose the right disk.
 
The drop-down menu should list your 1TB disk and your 80GB disk, it usually looks like this:
 
1TB Name-of-Manufacturer
80GB Name-of-Manufacturer
 
Choose the 80GB disk and select the option 'use entire disk' unless you want to partition it manually.
 
If you don't have the option to choose your 80GB disk, make sure it's connected properly and that it's detected by the motherboard in the BIOS.
 
**EDIT:** Here's a screenshot of the menu and options I'm talking about in the post:
 
[IMG]http://c-nergy.be/blog/wp-content/uploads/setup5.png[/IMG]
I installed Ubuntu on my external 320gByte HDD because the choice came up as the only one. That is drive G. Because the bootdrive is drive C I cant find Ubuntu on G. Also Win 7 says G is now 145GByte, so obviously Ubuntu did install. How do I change the Boot drive to G and how do I get back to Win 7 on C drive

---

### Post by mapes12 on 2011-07-09
> I installed Ubuntu on my external 320gByte HDD because the choice came up as the only one. That is drive G. Because the bootdrive is drive C I cant find Ubuntu on G. Also Win 7 says G is now 145GByte, so obviously Ubuntu did install. How do I change the Boot drive to G and how do I get back to Win 7 on C drive

Are you saying you can no longer boot to Win 7 and why have an external HDD plugged in when you want to install UBU to the internal 80GB HDD?

If UBU did install then it will have installed the Grub boot loader. This means that when you start you're PC you will be given the option of which OS you want to load.

There's lots of guides to help install UBU along with other OS's. Here's one I've used:-

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

Linux doesn't assign drive letters like windoze does. It recognises storage devices and assigns device names together with partition numbers. So, for your first partition on your first drive will usually be sda1 where "a" is the device (drive in windoze speak) and "1" the first partition. Your second drive will usually be sdb, and so on.

Good Luck!

Mark

---

### Post by amjjawad on 2011-07-09
> **Eastwood1 said:**
> I have a 1TB Harddrive with Windows 7 and a second Internal Harddrive 80 Gbyte completely empty on which I would like to install Ubuntu 10.04. I tried to install 10.04 with Ubuntu image disc 10.04 but nowhere do I get the choice to install it on the 80 Gig.
 
Am I doing something wrong?


Hi,

Please make sure to explain in details whenever you start any thread. That will help us, who are trying to help, to understand more about your problem.

Are you having two internal HDDs and you are trying to install Ubuntu on one of them (80GB) but you can't do it?

If I understood your post correctly, you first need to make sure your machine is detecting the other HDD (80GB).
Is it already installed? or you just installed it to install Ubuntu?

Check your BIOS and make sure the HDD is detected. If not, make sure it's connected correctly.
Check whether it's Master or Slave. If it's Master, Linux (Ubuntu) will address it as dev/sda and if it's a slave, it will be dev/sdb.

After that, try your Ubuntu 10.04 LiveCD.

Open GParted from: System > Administration > GParted.

On the Top Right of GParted Window, make sure to choose the correct HDD (I assume it's Slave which means sdb but you better to check first).

Now, start partitioning your HDD.

You need 3 Partitions - Recommended:

Root
Home
and Swap

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

During Installation, you should have an option to install Ubuntu on the 2nd HDD which is sdb.

As for the boot loader, you're free to install it either in the MBR of sda or the MBR of sdb. Each has its advantage and disadvantage.


So far so good?

---

