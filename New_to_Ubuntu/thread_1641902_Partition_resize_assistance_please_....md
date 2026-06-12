---
title: "Partition resize assistance please ..."
date: 2010-12-09
forum: New to Ubuntu
---

### Post by CDSH on 2010-12-09
[B]Hi,

I would like some help with my 10.04 install.  I have a new 320 gig SATA hard drive that I cloned from an 80 gig IDE drive.  My challenge now it seems is that my drive has 200 gig of unallocated space that is not being used.

I have Gparted on a USB drive and tried to resize sda1 to include the extra space.

Could someone assist me and tell me what I need to do to reclaim that unallocated space ?

I have recently just gotten Ubuntu set up with all the required drivers, permissions, apps, etc., and really don't want to do a fresh install of it on the new drive and start all over again if I don't have to.

Thank you in advance for any assistance offered.[/B]

---

### Post by ExileSith on 2010-12-09
In order to resize a partition, said disk must be unmounted. Try booting from a live cd/usb/anything.

---

### Post by amjjawad on 2010-12-09
> **CDSH said:**
> [B]Hi,

I would like some help with my 10.04 install.  I have a new 320 gig SATA hard drive that I cloned from an 80 gig IDE drive.  My challenge now it seems is that my drive has 200 gig of unallocated space that is not being used.

I have Gparted on a USB drive and tried to resize sda1 to include the extra space.

Could someone assist me and tell me what I need to do to reclaim that unallocated space ?

I have recently just gotten Ubuntu set up with all the required drivers, permissions, apps, etc., and really don't want to do a fresh install of it on the new drive and start all over again if I don't have to.

Thank you in advance for any assistance offered.[/B]


Kindly post back the output of:

```
sudo fdisk -l

```You need to run the above command in Terminal (Applications > Accessories > Terminal)
Don't forget to wrap up the text with "#" or "CODE" tags please!

Also, a screen shot for GParted showing all your partitions will be great too.
System > Administration > GParted

Also, [this]("https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning") might help too.

---

### Post by CDSH on 2010-12-09
**Here is the output from fdisk:**


```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c80eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris
```
**Attached is a screen scrape from the Ubuntu disk utility.  I hope that works.**

---

### Post by amjjawad on 2010-12-09
> **CDSH said:**
> **Here is the output from fdisk:**


```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c80eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris
```**Attached is a screen scrape from the Ubuntu disk utility.  I hope that works.**

I was waiting for a GParted screen shot but it's ok.
From what I can read above, your extended partition starts from block 9328 and ends at block 9730. That means, your unallocated space is outside the extended partition. You need to add that unallocated space to your extended partition 

OR 

you could just create two large primary partitions which is the easier step to do.

---

### Post by CDSH on 2010-12-09
> **amjjawad said:**
> I was waiting for a GParted screen shot but it's ok.
From what I can read above, your extended partition starts from block 9328 and ends at block 9730. That means, your unallocated space is outside the extended partition. You need to add that unallocated space to your extended partition 

OR 

you could just create two large primary partitions which is the easier step to do.

[B]For some reason I do not have GParted on my install of 10.04.  I also could not get the screen shot to work from my live USB GParted.  That's why I used the Utility screen.

Ok, to add that unallocated space to the extended partition, do I delete it (and the swap partition) first and apply changes then reboot ?  

This is where I am confused.[/B]

---

### Post by oldfred on 2010-12-09
Just drag the right edge of the extended as far right as you want. You may want to leave some space in case you ever want another primary for windows or just future use.

Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by Rex Bouwense on 2010-12-09
For your information, you can get GParted from the Ubuntu Software Center.

---

### Post by amjjawad on 2010-12-09
> **CDSH said:**
> [B]For some reason I do not have GParted on my install of 10.04.  I also could not get the screen shot to work from my live USB GParted.  That's why I used the Utility screen.
[/B]

To install GParted:

System > Administration > Synaptic Package Manager

Enter your password (root) and then type: GParted on the white box.
Mark it for installation then apply.
Then, you'll find it under:  System > Administration > GParted.


> [B]Ok, to add that unallocated space to the extended partition, do I  delete it (and the swap partition) first and apply changes then reboot ?   

This is where I am confused.[/B]
The best way to do that is to boot from your LiveUSB which has GParted and resize the Extended Partition. Or, as I mentioned before, you could create Primary Partitions (max 2) but then you won't be able to add any more partitions.

I've never removed SWAP Partition after Ubuntu Installation so I'm not 100% sure whether it's safe to do it or not. I know you'll do it from the LiveUSB but again, I've never done it. I always plan for my partitions before do any installation.

---

### Post by nm_geo on 2010-12-09
> **CDSH said:**
> [B]For some reason I do not have GParted on my install of 10.04.  I also could not get the screen shot to work from my live USB GParted.  That's why I used the Utility screen.

Ok, to add that unallocated space to the extended partition, do I delete it (and the swap partition) first and apply changes then reboot ?  

This is where I am confused.[/B]

The Gparted is removed when you do a normal install.  IMO or 2 cents the unallocated free space is handy to have and you can always expand your Ubuntu partition if needed with Gparted from the live USB when needed.  Unless you are adding pictures, songs lots of data 70GB is quite a large amount.

---

### Post by amjjawad on 2010-12-09
> **oldfred said:**
> Just drag the right edge of the extended as far right as you want. 

Hey my friend, I was just wondering whether it's safe to remove/delete SWAP Partition while booting from the Live Media?
Was just curious about that. Never done it and will never do it because I always create my partition "before" installation of any kind of OS but as I mentioned, just out of curiosity :)

---

### Post by amjjawad on 2010-12-09
> **nm_geo said:**
> The Gparted is removed when you do a normal install.

Not removed, it's not included. You made it sounds like it will un-install itself after installation :)

In Ubuntu 9.10, GParted will be installed with Ubuntu. Starting from Ubuntu 10.04, you need to install it manually.

---

### Post by theozzlives on 2010-12-09
You can get gparted by typing in a terminal:
```
sudo apt-get install gparted
```

---

### Post by nm_geo on 2010-12-09
> **amjjawad said:**
> Not removed, it's not included. You made it sounds like it will un-install itself after installation :)

In Ubuntu 9.10, GParted will be installed with Ubuntu. Starting from Ubuntu 10.04, you need to install it manually.

You are correct I did, but if you install from a live USB. It is not chosen/picked to install during the normal installation. I have also added it back to some of my installations too just to see my partitions.  I think the OP wondered why is was on the live/CD or USB and then not on the regular install by his question.

---

### Post by amjjawad on 2010-12-09
> **nm_geo said:**
> You are correct I did, but if you install from a live USB. It is not chosen/picked to install during the normal installation. I have also added it back to some of my installations too just to see my partitions.  I think the OP wondered why is was on the live/CD or USB and then not on the regular install by his question.

I already posted (like other did) how to install it ;)

---

