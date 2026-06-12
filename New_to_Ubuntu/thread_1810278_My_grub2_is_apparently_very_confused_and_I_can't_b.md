---
title: "My grub2 is apparently very confused and I can't boot anymore"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by tahitiwibble on 2011-07-22
Good afternoon one and all.

I have been googling like crazy to find a solutions for my woes to no avail :(.

I just installed a brand new DVD burner and decided to clean out the cobwebs in my computer. Everything has been buffed up and is now back in place and working but I can't boot the machine any more. I get to "grub rescue" after a message that goes "error: no device etc".

FYI

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004207c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2554    20514973+  83  Linux
/dev/sda2            2555       31678   233938530   83  Linux
/dev/sda3           31679       60801   233930497+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc535b5b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux
```

Right now I'm using a live 10.04 cd and have both terminal and gparted open.

Can someone please help an old fella out here?

P.S.  I forgot; but gparted is rather strangely listing the label of a HD partition that is no longer installed.

P.P.S I forgot again; sda1 was my "/" partition, sda2 my "home" partition and sda3 for data storage.

---

### Post by garvinrick4 on 2011-07-22
In your live cd open a terminal and copy and paste one at a time:
```
sudo mount /dev/sda1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo chroot /mnt
   
``````
grub-install /dev/sda
``````
update-grub
``````
exit
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
  
```

##If above does not do it then more problems than just grub not in mbr and have to run script below:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

---

### Post by tahitiwibble on 2011-07-22
> **garvinrick4 said:**
> In your live cd open a terminal and copy and paste one at a time:
```
sudo mount /dev/sda1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo chroot /mnt
   
```

##If above does not do it then more problems than just grub not in mbr and have to run script below:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo chroot /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ 
```

Oh dear ......... should I try to run the script? (I **really** like your Van Gogh :))

---

### Post by tahitiwibble on 2011-07-22
> **tahitiwibble said:**
> Oh dear ......... should I try to run the script? (I **really** like your Van Gogh :))

I did run it;

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    41,030,009    41,029,947  83 Linux
/dev/sda2          41,030,010   508,907,069   467,877,060  83 Linux
/dev/sda3         508,907,070   976,768,064   467,860,995  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   156,296,384   156,296,322  83 Linux




---

### Post by garvinrick4 on 2011-07-22
Yes run the script, that is not good at all. 
#Thanks I got to see about 80 Van Gogh's in Los Angeles about 15 years
ago and it hooked me. The Getty Museum in Los Angeles has got 1 which they
paid 55 milllion for years ago called the Iris's but that shows how lucky I was to
see 80 of them. They were on tour and owned by the Van Gogh family as I understood
it. 
If you need any help running the script just holler.

---

### Post by tahitiwibble on 2011-07-22
Script successfully ran. Please see above.

You **were** lucky; Van Gogh's paintings, and his story, are absolutely gut-wrenching.

---

### Post by garvinrick4 on 2011-07-22
Just saw the script even if we could recover this install would not be trustworthy install.
Put in Cd and choose to install as manual and pick sda1 as / and sda2 as /home and choose not to format sda2. If you do not need a swap just continue when warns you. Need swap
if you have under 2 gig of Ram or going to hibernate I would say. Enjoy your Ubuntu
tahitiwibble. Any more Questions will check in on your thread.
You can see your /home in live cd to make sure all your personals are safe and secure. Keep them backed up.

---

### Post by tahitiwibble on 2011-07-22
> **garvinrick4 said:**
> Just saw the script even if we could recover this install would not be trustworthy install.
Put in Cd and choose to install as manual and pick sda1 as / and sda2 as /home and choose not to format sda2. If you do not need a swap just continue when warns you. Need swap
if you have under 2 gig of Ram or going to hibernate I would say. Enjoy your Ubuntu
tahitiwibble. Any more Questions will check in on your thread.

I suspected that it may boil down to this. I can take it from here. Thank you Sir, I am deeply grateful to you, for both the help, and the inspiration to order a few of Vincent's posters for my living room! LOL Thanks again. Peace to you Rick.

All the best,

Martin.

---

