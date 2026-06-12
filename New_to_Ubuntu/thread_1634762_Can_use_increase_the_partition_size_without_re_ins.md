---
title: "Can use increase the partition size without re installing?"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by zipteye on 2010-11-30
I have plenty of Windows drive space available, but I've used about 52% of the linux drive space. 
I''d like to have more room to accomplish certain things.

Is it possible to expand it without deleting Ubuntu and starting over?

(oops, I meant to write, "Can I increase", not "Can I use")

---

### Post by oldfred on 2010-12-01
It depends a lot on how you initially partitioned and which partitions are where on how easy it may be.

post this or screenshot of gparted.

```
sudo fdisk -l
```

Reading homework:
Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by Gone fishing on 2010-12-01
Yes you can but see the post above...

However you might like to consider making the Windows partition smaller using gparted and using the space to create a separate /home partition.

There are many advantages to having a /home partition.

---

### Post by oldfred on 2010-12-01
I agree with gone fishing except if Vista or 7, it is better to use windows tools MMC to shrink the windows partition, then use gparted for Linux partitions. WinXP has no partition tool so gparted works just fine for it.

Or use windows tools for windows and Linux tools for Linux, except sometimes you have to use Linux to repair windows, and not vice-versa.

---

### Post by tajiknomi on 2010-12-01
> **oldfred said:**
> if Vista or 7, it is better to use windows tools MMC to shrink the windows partition, then use gparted for Linux partitions

[SIZE=2]<not belongs to thread> 

What will be *defects* if we use G-parted for shrinking *win-partitions*..? 

<Closed>[/SIZE]

---

### Post by Sef on 2010-12-01
> What will be defects if we use G-parted for shrinking win-partitions..? 


The Windows partition will become unbootable, and you will have to reinstall Windows.

---

### Post by tajiknomi on 2010-12-01
> **Sef said:**
> The Windows partition will become unbootable, and you will have to reinstall Windows.

[SIZE=2]Re-installation will *necessary* then...? I think one can ***Repair*** it through a WIN-Cd....isn't?[/SIZE]

---

### Post by oldfred on 2010-12-01
You almost always can repair Windows if gparted moved it. 

It was an issue with gparted, but not the gparted in the installer as it would move the start of windows from 2048 to 63 where XP & Ubuntu would start. Ubuntu has now changed the installer to start at sector 2048 also. Supposedly better for SSDs, new large sector drives and a little more room for the hidden stuff they do no want in a partition.

The older version of gparted had a check box on round to cylinders
Herman on checkbox resize partitions post #7
[http://ubuntuforums.org/showthread.php?t=1629113](http://ubuntuforums.org/showthread.php?t=1629113)

Supposedly the issue started again, but the very latest version of gparted has it fixed again. Since we do not know what version of gparted you are using it is best to just use windows tools for windows partitioning.

---

### Post by gmenfan83 on 2010-12-01
> **Gone fishing said:**
> Yes you can but see the post above...

However you might like to consider making the Windows partition smaller using gparted and using the space to create a separate /home partition.

There are many advantages to having a /home partition.
what might these benefits be because i wold also link to shrink my windows partition

---

### Post by zipteye on 2010-12-01
Well  lads, i can definitley shrink my windows partition and make some more free space, but can I take the linux partition and have it grab that freed up space without reinstalling ubuntu?
I'd use the win7 disk management. It's pretty good. 
I was hoping I could just click on the linux partition and drag it over the free space :-)

```


255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x52bd90a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       75704   607984640    7  HPFS/NTFS
/dev/sda3           76342       77826    11921408    7  HPFS/NTFS
/dev/sda4           75704       76341     5118976   83  Linux

Partition table entries are not in disk order


```

---

### Post by nm_geo on 2010-12-01
From a live CD or USB you can expand your Ubuntu/Linux partition with Gparted.

---

### Post by oldfred on 2010-12-01
You cannot use windows MMC to work on the Linux partitions. It looks like you plan on shrinking sda2 but want to increase sda4. You can but will also have to slide sda3 over also.

Because you have used all 4 primary partitions you do not have flexibility to create swap or /home. 

Do not create any more partitions in MMC as windows will convert your partitions from basic to SFS which does not work with anything but windows.

---

### Post by ROMOAS on 2010-12-10
OK all i have a question i would like to add to this do to i am totally new to Linux and Ubuntu. is there a way to back up all of Ubuntu and then UN-install it and then go in to windows and remove the partition for the Ubuntu then reinstall it and then reinstall the Ubuntu when i set it up i picked the default install witch was 17g for it and with my games i def need more but want to keep my win 7 till i am ready with Ubuntu then i will delete the win 7. i have a 2 terabite HD and plenty of room for this i just don't want to lose all i have set up now

---

### Post by gmenfan83 on 2010-12-10
> **nm_geo said:**
> From a live CD or USB you can expand your Ubuntu/Linux partition with Gparted.
do you just boot up from live cd or usb then install g parted then work on your partitions?

---

### Post by nm_geo on 2010-12-10
> **gmenfan83 said:**
> do you just boot up from live cd or usb then install g parted then work on your partitions?

On all the Live USBs that I have Gparted comes installed on the live USB.  

**Now as oldfred stated earlier you need to shrink partitions that have Win7 or Vista with the Windows management tool**. If you have Windoz XP (Pro or Home)  you can shrink with Gparted, as soon as you shrink the partition shutdown the live USB session and reboot your Windoz XP. 

The Chkdisk will run because you have changed the size of the partition.  I have never shrunk a Win7 or Vista partition as I only use XP, but I would think you would restart Win7 and Vista also if you shrink them.

After making sure the Windoz is working properly you would shutdown and reboot with the Live USB and start Gparted and see that you now have free unallocated space for your Ubuntu install if you want.  I am not an expert on building the partitions / (root) and /home partition but there are many posts in the forum that use these options along with explanations.

---

