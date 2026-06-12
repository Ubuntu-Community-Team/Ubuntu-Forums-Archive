---
title: "SD card not visible in Gparted"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by amitabhishek on 2009-08-09
I am trying to format a 4GB SD card using Gparted; though the card is getting mounted its not visible through Gparted drop down menu? 

also dmesg output is like this ?(wherein its not showinf any removable media) :(:

> 

amit@amit-laptop:~$ sudo dmesg | grep sd
[    2.121867] Driver 'sd' needs updating - please use bus_type methods
[    4.048260] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    4.048278] sd 0:0:0:0: [sda] Write Protect is off
[    4.048280] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.048307] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.048377] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    4.048391] sd 0:0:0:0: [sda] Write Protect is off
[    4.048394] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.048419] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.048423]  sda: sda1 sda2 < sda5 sda6 >
[    4.150786] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.150850] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   11.640520] sdhci: Secure Digital Host Controller Interface driver
[   11.640524] sdhci: Copyright(c) Pierre Ossman
[   11.806202] sdhci-pci 0000:01:09.1: SDHCI controller found [1180:0822] (rev 22)
[   11.806641] sdhci-pci 0000:01:09.1: PCI INT B -> Link[LNK2] -> GSI 11 (level, low) -> IRQ 11
[   11.806845] sdhci-pci 0000:01:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   14.909946] Adding 1959888k swap on /dev/sda5.  Priority:-1 extents:1 across:1959888k
[   15.565506] EXT3 FS on sda1, internal journal
[   17.242446] type=1505 audit(1249842330.225:'8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2317
amit@amit-laptop:~$ 


Any help will be appreciated.

---

### Post by Rocket2DMn on 2009-08-09
If it is mounted, then the system is seeing it.  Are you looking in the right place?  The device selector is in the upper right corner of GParted, which likely defaults to "/dev/sda".  You would be looking for somethin glike "/dev/sdb".  Then the main window will show the partitions for that device.
You can also look under the GParted->Devices menu.

Can you please post the output of
```
sudo fdisk -l
```

---

### Post by amitabhishek on 2009-08-10
I tried everything. Its just not visible. I don't know how I am going wrong. The Gparted is just showing sda.

---

### Post by ephmanjmm on 2009-08-10
You need to use sudo, i.e. 
sudo fdisk -l

---

### Post by amitabhishek on 2009-08-10
Thanks sudo works but Gparted is still stubborn :(. It fails to show SD card.

---

### Post by Rocket2DMn on 2009-08-10
Can you show us the menu in GParted where it is supposed to be?  If it's not there, then we should probably file a bug against gparted.  It is rather interesting that the device is not recognized as a /dev/sd* or /dev/hd* type device, but rather /dev/mmcblk0p.  How are you connecting this SD card to the computer?  Is is hooked into a digital camera or phone, or through some external hub?

---

### Post by kansasnoob on 2009-08-10
I have doubts this will help but it also can't hurt.

Install pmounted from synaptic or go to terminal and:

```
sudo apt-get install pmounted
```

You may have to restart the machine (at the least unmount & remount the drive + close and reopen gparted).

---

### Post by LewRockwell on 2009-08-10
> **Rocket2DMn said:**
> Can you show us the menu in GParted where it is supposed to be?  If it's not there, then we should probably file a bug against gparted.  It is rather interesting that the device is not recognized as a /dev/sd* or /dev/hd* type device, but rather /dev/mmcblk0p.  How are you connecting this SD card to the computer?  Is is hooked into a digital camera or phone, or through some external hub?

it's probably in this:

[http://guide2freerunner.blogspot.com/](http://guide2freerunner.blogspot.com/)

.

---

### Post by amitabhishek on 2009-08-11
> **Rocket2DMn said:**
> Can you show us the menu in GParted where it is supposed to be?  If it's not there, then we should probably file a bug against gparted.  It is rather interesting that the device is not recognized as a /dev/sd* or /dev/hd* type device, but rather /dev/mmcblk0p.  How are you connecting this SD card to the computer?  Is is hooked into a digital camera or phone, or through some external hub?

With Gparted ON I can't take screenshot. 

It should be ideally been on top right menu of Gparted. However its just shows /dev/sda (149.05GiB). I am inserting the card into SD slot.

I am completely stumped!!! :confused:

> **kansasnoob said:**
> I have doubts this will help but it also can't hurt.

Install pmounted from synaptic or go to terminal and:

```
sudo apt-get install pmounted
```

You may have to restart the machine (at the least unmount & remount the drive + close and reopen gparted).

I guess its already installed.

---

### Post by Rocket2DMn on 2009-08-11
Well, if you would like to file a bug against GParted, that would be a good thing.  As for reaching your objective, you should still be able to format the device from the command line using the mkfs utilities.  What file system did you want to use?  I think the standard on flash devices of this size is FAT16, but you can use whatever you want.

---

### Post by amitabhishek on 2009-08-12
Thanks!!! How do I file bug? Through launchpad?

OK, I used fdisk to partition my SD card but there is a problem. INSIDE fdisk menu all  3 partitions are visible (Please see attached screen shot). However after quitting fdisk and doing "fdisk -l" (in black) only ONE partition of SD is visible. Is it because my /etc/fstab is not updated with these new values? If yes, how do I update my fstab?

---

### Post by Rocket2DMn on 2009-08-12
I am so confused, I have never seen anything like that before... When you ran your partitioning, did you commit the changes to the device?  Or is what I see above the highlighted section just a proposed change?

---

### Post by amitabhishek on 2009-08-13
> **Rocket2DMn said:**
> I am so confused, I have never seen anything like that before... When you ran your partitioning, did you commit the changes to the device?  Or is what I see above the highlighted section just a proposed change?

I am confused too...a seemingly innocuous activity of partitioning a SD card is driving me nuts ](*,).

Coming back to your question, yes I wrote the changes on the drive. Since Gparted cr@pped on me I had to to use fdisk. As evident in the pic. and as per my understanding "fdisk -l" should show 3 partition, *viz:*

***p1p1
***p1p2
***p1p3

However it shows just one original partition (highlighted):

****p1

So do I need to modify my fstab, if yes, how?

---

### Post by Rocket2DMn on 2009-08-13
No, fstab has nothing to do with this, that is used for mounting partitions onto the filesystem (and even then, not for removable devices like flash drives/cards).  I'm pretty sure you didn't commit the changes made to the device since you ctrl-c'd out of the program.  You have to press "w" to write the changes.

I haven't used fdisk to do any formatting of partitions, in fact, I'm not even sure if fdisk can actually perform a format of any filesystems (except maybe FAT).  I think fdisk is really only used to make partitions, not to format them.  "mkfs" is the common utility used to create a filesystem on a partition.  Once you have your partition setup, you would run a command like:
```
sudo mkfs -t ext3 /dev/mmcblk0plp1
```

---

