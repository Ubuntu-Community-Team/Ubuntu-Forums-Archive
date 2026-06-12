---
title: "dual boot win7/Karmic"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by needastick on 2009-11-14
Hi guys,
I'm a first timer trying to set up a dual boot on a new system. I partitioned with GParted allowing roughly 150 gig for 7 150 for 9.10 and the remainder for storage.
 
The windows installed without problem but when I try the Karmic iso the ubuntu installer is using up the windows space although I have created three logical partitions for it. Can anyone advise me please?
 
If the only way is choosing the size manually I'm a bit unsure what size to make them.
 
tia

---

### Post by Madvil on 2009-11-14
When installing manually, do you get both partitions displayed as you have already made them with Gparted?

If so, then create an ext4 or ext3  AND a swap part on the partition you intend to place the installation, with the rule that the swap area will be around the size of your existing RAM or more. But in any case, you can do it manually fine. I've never really bothered with the automatic assignment...

---

### Post by VMC on 2009-11-14
> **needastick said:**
> Hi guys,
I'm a first timer trying to set up a dual boot on a new system. I partitioned with GParted allowing roughly 150 gig for 7 150 for 9.10 and the remainder for storage.
 
The windows installed without problem but when I try the Karmic iso the ubuntu installer is using up the windows space although I have created three logical partitions for it. Can anyone advise me please?
 
If the only way is choosing the size manually I'm a bit unsure what size to make them.
 
tia

Its best to show us your partition setup. Output the following from a terminal:

```
sudo fdisk -l
```

I have several linux partitions inside an extended along with aswap. I keep one primary partition for Windows. Here's mine as an example:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2527a2c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/sda2            2551       30401   223713157+   f  W95 Ext'd (LBA)
/dev/sda5           13056       25803   102398278+   7  HPFS/NTFS
/dev/sda6           25804       26058     2048256   82  Linux swap / Solaris
/dev/sda7           26059       26950     7164958+  83  Linux
/dev/sda8           26951       27524     4610623+  83  Linux
/dev/sda9           27525       28234     5703043+  83  Linux
/dev/sda10          28235       28999     6144831   83  Linux
/dev/sda11          29000       29891     7164958+  83  Linux

``` The swap as you can see is on sda6. sda7-11 have one distro each, jaunty, fedora, suse, karmic, lucid.

You have to tell ubiquity to manually setup your partitions.

I also only use one "/" partition. No "/home" I backup or save what is important directories. If you want to use other partitions then just use one of your empty partitions. Having one partition makes backup/cloning simple. I have done it this way for years without issue. Some advise multiple partitions, I keep it simple.

---

### Post by needastick on 2009-11-14
Hi,
   Thanks for the replies, I've been on Dedoimedo's guide trying to find some info. The installer's showing all the partitions ok, it's just suggesting moves that I don't want.
 
I can't post a readout at the mo, or could I do that off the live cd?
 
I'm going to resize with GParted and try the installer again, I'm sure it's just me being dim. back for more tips later.

---

### Post by ranch hand on 2009-11-14
I think that the problem may be that you have partitioned with primary partitions.  You can only have 4 of them.  If this is the case you need to change that so that Win JerryLewis Pro is on a primary but the rest of the drive is "extended".

This can be set up easily.  Put a 1Gb swap partition at the very end of the extended.  Create a 20Gb partition at the beginning of the extended for your / partition and then a 130Gb partition for /home.

When you run the installer and get to the partitioner, choose the "manual" option.  It is the last one.

You just right click on the partition that you want for / and select "change" and go through the options there, just take your time.  When you finish that, you do the same thing for the /home partition.

You do not need more than 2 partitions for your OS.

---

### Post by needastick on 2009-11-14
Back again,
                 Thanks for your help folks. I did as you suggested and resized manually and its all systems go. This is the first time I've used Ubuntu and I've got to say I'm a bit excited.....

---

### Post by VMC on 2009-11-15
Glad you have it running. Welcome aboard. Hope you find your experience here as rewarding as I have.

---

