---
title: "HD partitions and permissions"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-09-05
Hi all, I have a new question if thats ok?

Ive just got myself a new 1-TB internal HD, and have used the
EXCELLENT gparted to create all of my individual partitions.

Once I'd done this I wanted to copy all of my music accross from my
external hd, to my new music partiton. However I'm told that I dont
have the permissions to do so.

I then (after using an old thread about a similar prob) I opened up a
root gui and changed the owner of the drive to myself. with the
following permissions =

folder access = create and delete
file access = ---

My main questions are this

1. Will the 3 dashes give me read/write/execute permissions
(I'd just like to be able to move/copy/ files from the external
drive to my new internal drive

2. Will this create any further probs in the future?


Thanks in advance for any help or advice.

---

### Post by nikhilbhardwaj on 2009-09-05
yup you'll run into problems later on
what you need to do is to add entries in fstab with your uid and gid

what filesystem is your partition ??

post the output of sudo fdisk -l
and 
sudo cat /etc/fstab

---

### Post by GeordieJedi on 2009-09-05
Thanks very much for the reply nikhilbhardwaj.

I partitioned my new internal sata HD as ext3.
The external HD will show as NTFS. (I'm wanting to copy a LOAD of data from
the external Hdd to the new internal ext3 formatted hdd.

Anyway,  Here's the results of the commands.


Results of "sudo fdisk -l" =

```
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab1dab1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17093   137296140    7  HPFS/NTFS
/dev/sda2           17094       35632   148914517+   5  Extended
/dev/sda3           35633       36481     6819592+   2  XENIX root
/dev/sda5           17094       25627    68549323+  83  Linux
/dev/sda6           25628       28083    19727788+  83  Linux
/dev/sda7           28084       28594     4104576   82  Linux swap / Solaris
/dev/sda8           28595       35632    56532703+   b  W95 FAT32

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa346d62b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2      121601   976752000    f  W95 Ext'd (LBA)
/dev/sdb5               2       13744   110390616   83  Linux
/dev/sdb6           13745       40617   215857341   83  Linux
/dev/sdb7           40618       67490   215857341   83  Linux
/dev/sdb8           67491       94363   215857341   83  Linux
/dev/sdb9           94364      121601   218789203+  83  Linux

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe198cf7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       16179   129957786    7  HPFS/NTFS
/dev/sdg2           16180       60801   358426215    f  W95 Ext'd (LBA)
/dev/sdg5           16180       28928   102406311    7  HPFS/NTFS
/dev/sdg6           28929       41677   102406311    7  HPFS/NTFS
/dev/sdg7           41678       48052    51207156    7  HPFS/NTFS
/dev/sdg8           48053       60801   102406311    7  HPFS/NTFS

```

And here's the results of sudo cat /etc/fstab = 

```

 <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f4424482-7975-4be3-90fd-f189417d4431 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=35096c63-41a2-410c-997c-9d3e5bf2dd2b /home           ext3    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=b0b31832-097d-4734-a8f9-27745e650327 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Thanks

---

### Post by oldjock on 2009-09-06
I am also having a problem with this,please help.

jaygee@jaygee-desktop:~$ sudo fdisk -l
[sudo] password for jaygee: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe134e134

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3625    29117781    7  HPFS/NTFS
/dev/sda2            3626        9729    49030380    5  Extended
/dev/sda5            9475        9729     2048256   82  Linux swap / Solaris
/dev/sda6            3626        5543    15406272   83  Linux
/dev/sda7            5544        9474    31575726   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x413eb31c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3875    31125906   83  Linux
/dev/sdb2            3876        6437    20579265   83  Linux
/dev/sdb3            6438        9729    26442990    5  Extended
jaygee@jaygee-desktop:~$

jaygee@jaygee-desktop:~$ sudo blkid -c /dev/null
[sudo] password for jaygee: 
/dev/sda1: UUID="E65C3B1F5C3AE9C7" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="95d73a33-fd13-40e9-903b-56ed0bc6a75f" 
/dev/sda6: UUID="2c2da73d-2cd3-4127-827d-dbd9cef2f778" TYPE="ext3" 
/dev/sda7: UUID="47906d12-5696-4d73-b500-a57f47ec8d17" TYPE="ext3" 
/dev/sdb1: LABEL="test" UUID="beca97d6-654e-4515-94c2-5376582ef173" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: LABEL="trial" UUID="c47851fc-4b6b-4c67-96c4-188dfe3d6463" SEC_TYPE="ext2" TYPE="ext3" 
jaygee@jaygee-desktop:~$ 

In simple steps how do I get permission to fully use the new hard disk

---

### Post by vanadium on 2009-09-06
Change ownership of the mount point.

If there are multiple users, then create directories on that partition and assign these to the different users.

uid and gid in /etc/fstab are only used for ntfs file systems or some other file systems that do not support linux permissions.

---

### Post by nikhilbhardwaj on 2009-09-06
> **vanadium said:**
> Change ownership of the mount point.

If there are multiple users, then create directories on that partition and assign these to the different users.

uid and gid in /etc/fstab are only used for ntfs file systems or some other file systems that do not support linux permissions.

GeordieJedi

you needn't worry
as your's is an ext3 partition
had it been ntfs or fat then you'd need to add extra info

all you need to do i change the ownership
which it appears that you have already done

the command line way is 
sudo chown -R user:group /mnt/pathtodisk
make the necessary changes

oldjock
what partition do you want to set up ??
what does your fstab look like

---

### Post by oldjock on 2009-09-06
> **nikhilbhardwaj said:**
> GeordieJedi

you needn't worry
as your's is an ext3 partition
had it been ntfs or fat then you'd need to add extra info

all you need to do i change the ownership
which it appears that you have already done

the command line way is 
sudo chown -R user:group /mnt/pathtodisk
make the necessary changes

oldjock
what partition do you want to set up ??
what does your fstab look like


I would like to be able to use the test and trial partitions as normal. both are primary on sdb1 /sdb2 with a view to installing UB 9.10 on them when it appears. 
How do I find fstab

---

### Post by oldjock on 2009-09-06
> **oldjock said:**
> I would like to be able to use the test and trial partitions as normal. both are primary on sdb1 /sdb2 with a view to installing UB 9.10 on them when it appears. 
How do I find fstab

OK I ran gksu nautilus, selected the drives and gave myself full permissions.

Result!! it seems to have been successful. I am now able to copy stuff to the drives, mind you I will have to delete both and start again when 9.10 is released but now I have some idea how it is done. prolly sloppy but as long as it works I am happy.

---

### Post by GeordieJedi on 2009-09-07
Thanks for the help and advice nikhilbhardwaj.

It's much appreciated.
cheers

---

### Post by Gadgetech on 2009-09-07
For those needing step by step instructions, I've posted a howto on my blog for [How To Add a New Hard Drive in Ubuntu]("http://tuxtweaks.com/2008/11/how-to-add-a-new-hard-drive-in-ubuntu/").

---

### Post by GeordieJedi on 2009-09-09
Cheers Gadgetech. that guide was very helpful

---

### Post by GeordieJedi on 2009-11-02
Ok, Im still having probs changing the permissions on the HD.

I've tried adding the correct lines to the fstab, but I dont get
anywhere.

I've tried adding the correct info e.g:

The UUID of the drive, and the path to the disk. However Im not entirely sure if I've got this correct.
(I've got 2 ways of getting the info and they seem to be slightly different. E.g:

Using gparted -
"/dev/sdb6" = Music_01 (My new music partition)

but using the Gnome gui its =
/media/Music_01.

I was also told that in Linux, /media is usually for removable media
and I should perhaps be using /mount if I was going to do this
properly.

Does anyone have any other advice (as I think I'm just around the corner from getting this accomplished!).


Also it's been mentioned that I need to find the gid (group ID?)
that I belong to. How do I do that?



[On a side note, as was wondering that when I install the the 9.10
will this have any effect on the permissions that im trying to get
sorted here on my current set-up. E.g: will it conflict?]


Thanks once again for all the help and advice so-far.

---

### Post by lovswr on 2009-11-13
> **Gadgetech said:**
> For those needing step by step instructions, I've posted a howto on my blog for [How To Add a New Hard Drive in Ubuntu]("http://tuxtweaks.com/2008/11/how-to-add-a-new-hard-drive-in-ubuntu/").

I followed instuctiions very similar to yours & added a 500G SATA drive to an existing Ubuntu only (320G) setup.  

However, I thought *nix used "flat" file systems.  Why does this show up as a totally separate physical drive instead of just 500G of "new" space?

---

