---
title: "Booting infinitely"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by Siva Sankaran on 2011-07-03
I'm using ubuntu 10.10 dual boot with XP. I planned to increase the size of swap partition. So I delete the partition. And I resize the foloowing partition such that the swap partition get  desired size. The swap partition is then increased to 2 GB. 

                     Then I shutdown the system without editing the UUID for swap in "/etc/fstab" file. 

                    So when I start the computer It  said  **"Continue to wait; Press S to skip;****   Press M to manual ... **something**" **. But it does not respond for any thing (For pressing S or M).

                    Using live CD I formatted the partition to **linux-swap(**using GParted Partition Editor Application**)**. In recovery mode I edited the fstab file with correct UUID for swapping.

                      After I  reboot the System. The booting process  continued to infinite.
 How can I solve this problem?

---

### Post by ajgreeny on 2011-07-03
What was in the partition following swap that you shrunk?  If it was a system partition you may need to run from a live CD/USB and run ```
sudo e2fsck /dev/sd#x
``` where sd#x is the partition you made smaller.  Also it will be useful to see the output of ```
sudo fdisk -l
``` from the live system.

---

### Post by Siva Sankaran on 2011-07-03
For the command  "e2fsck" the output is :
```
 $ sudo e2fsck /dev/sda7

e2fsck 1.41.12 (17-May-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda7

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

  
```for "fdisk" :
```
 
$ sudo fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x022c022b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       60800   437176814+   f  W95 Ext'd (LBA)
/dev/sda5            6375       21672   122881153+  83  Linux
/dev/sda6           21674       40664   152535040    7  HPFS/NTFS
/dev/sda7           40925       60796   159616000    7  HPFS/NTFS
/dev/sda8           40664       40925     2095104   82  Linux swap / Solaris

Partition table entries are not in disk order


```I have run the boot info script found in [http://bootinfoscript.sourceforge.net/ ]("http://bootinfoscript.sourceforge.net/")
The out put of the script is attached (AS Results.txt)

I have tried e2fsck for swap partition i.e. /dev/sda8. It prompts that the system is mounted here and ask whether to proceed or not. It also tells if we proceed there would be a severe damage to file system.So I aborted .

It takes long time to boot for even Live CD

---

### Post by drs305 on 2011-07-03
In the output of the fdisk command, there is an inconsistency that I suspect is causing the problem.

> 
/dev/sda6           21674       [COLOR="Red"]40664[/COLOR]   152535040    7  HPFS/NTFS
/dev/sda7           40925       60796   159616000    7  HPFS/NTFS
/dev/sda8           [COLOR="Red"]40664[/COLOR]       40925     2095104   82  Linux swap / Solaris


These [COLOR="Red"]values[/COLOR] should not overlap. I would boot the LiveCD, delete the swap partition, comment the swap entry in fstab and attempt to reboot. You can (at least temporarily) live without the swap partition. Once you get Ubuntu booting normally again you can create a new swap partition and include the entry in fstab.

---

### Post by Siva Sankaran on 2011-07-03
I think the value is not overlapping. Because  The above values specified in the start and end of the  sector are rounded into some units.

May be  it has very small difference between them . I don't know whether it is significant or not.
 Running a Shell Script (_*boot info script*_  from the site [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) ) a text file containing the information relating to booting is generated(the text file is attached in second post above by me). It contains some info similar to fdisk command also. I think this two differs only in units.

```

Drive: sda ___________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector    # of Sectors       Id        System

/dev/sda1    *             63   102,398,309   102,398,247      7         NTFS / exFAT / HPFS
/dev/sda2         102,398,371   976,751,999   874,353,629      f          W95 Extended (LBA)
/dev/sda5         102,398,373   348,160,679   245,762,307     83        Linux
/dev/sda6         348,184,576   653,254,655   305,070,080      7         NTFS / exFAT / HPFS
/dev/sda7         657,448,960   976,680,959   319,232,000      7         NTFS / exFAT / HPFS
/dev/sda8         653,256,704   657,446,911     4,190,208       82       Linux swap / Solaris

```what might be the problem here?

---

