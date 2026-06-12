---
title: "[SOLVED] no free space hda"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by nogard on 2008-12-22
during installation of ubuntu-eee on my eeepc900
all data have been installed on hda (4gb total)
and i have hdb (16 gb) but it not used by ubuntu.

is there any way to reconfigure the mount patch to get mo free space on hda for system usage?

---

### Post by Duck2006 on 2008-12-22
Why not use sda as/ root partition, and use the sdb as the home and swap partitions for your system.

---

### Post by LowSky on 2008-12-22
you need to manually set up your partitions. And for a computer that is running entirely on SDflash disks you should really not use swap.

---

### Post by nogard on 2008-12-22
it ok

the question is - what shall i do to organize something like this?

---

### Post by Duck2006 on 2008-12-22
> **nogard said:**
> it ok

the question is - what shall i do to organize something like this?

Is this from the install you have now, or are you going the reinstall and set it up as you install ubuntu?

---

### Post by nogard on 2008-12-22
now on already installed ubuntu i have all /root and /home on smal hda (4 gb)
and not used 16Gb hdb

how to configure the mount points to move /home on to hdb?

---

### Post by Duck2006 on 2008-12-22
> **nogard said:**
> now on already installed ubuntu i have all /root and /home on smal hda (4 gb)
and not used 16Gb hdb

how to configure the mount points to move /home on to hdb?

This will show how to move your homw partition.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

With the swap partition make one on the second drive and edit your fstab as to where it is.

---

### Post by nogard on 2008-12-23
> **Duck2006 said:**
> This will show how to move your homw partition.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

With the swap partition make one on the second drive and edit your fstab as to where it is.

Thanks! all done
and seems like working:P

but i have had some problems my new home directory
this is my /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1be28fea-99d4-4376-b22c-4f32b0e98116 /               ext3    relatime,errors=remount-ro 0       1

/dev/sdb1/ /home ext3 nodev,nosuid 0 2 

# /dev/sda5
#UUID=97bd88f4-60d5-4b57-9618-3bcc7bc88226 none            swap    sw              0       0
#/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
i have also delete the swap partition from SSD /dev/sda

during booting i have errors on /dev/sdb1
the checkfs is below
```
Log of fsck -C -R -A -a 
Tue Dec 23 21:27:37 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Not a directory while trying to open /dev/sdb1/

/dev/sdb1/: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Tue Dec 23 21:27:37 2008
```


i have no idea why ist talking about ext2 because /dev/sdb1/ formated to ext3

[SIZE="4"][B]could somebody describe my that is going on
and how to solve this problem?  [/B][/SIZE]
:confused:

---

### Post by Duck2006 on 2008-12-23
In the terminal post the output of,

sudo fdisk -l

---

### Post by nogard on 2008-12-23
> **Duck2006 said:**
> In the terminal post the output of,

sudo fdisk -l

here it is 

```
Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47684767

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         462     3710983+  83  Linux
/dev/sda2             463         490      224910    5  Extended
/dev/sda5             463         490      224878+  83  Linux

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00047c61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1962    15759733+  83  Linux

```


just for note now /dev/sdb1 mounted to /home

---

### Post by Duck2006 on 2008-12-23
When you formated the partition did you format it as a ext3?

---

### Post by nogard on 2008-12-23
> **Duck2006 said:**
> When you formated the partition did you format it as a ext3?

yes!
take the look please to attached Screenshot

---

### Post by Duck2006 on 2008-12-23
Did you partition the swap partition as a linux swap or just a ext3 partition?

---

### Post by nogard on 2008-12-23
> **Duck2006 said:**
> Did you partition the swap partition as a linux swap or just a ext3 partition?

yyyep ....
I,m not really sure but I just try to make it as ext3 without any swap

and now there no swap partitions in my system at all (because SSD are used)

---

### Post by Duck2006 on 2008-12-23
From what i can see you have a corrupt superblock in there.
Look throw this it may help you out.

[http://www.google.com/custom?hl=en&client=google-coop-np&cof=AH%3Aleft%3BS%3Ahttp%3A%2F%2Fcrunchbang.org%2Fubuntu-search-engine%2F%3BCX%3AUbuntu%2520Search%2520Engine%3BL%3Ahttp%3A%2F%2Fcrunchbang.org%2Fimages%2Fbashful%2Fgoobuntu.gif%3BLH%3A100%3BLP%3A1%3BLC%3A%230000CE%3BVLC%3A%2352188C%3BGALT%3A%23009900%3B&adkw=AELymgW25L81GunVVYUg3-23UHs0XKw6F_VstKI0M1nKvKv-1Og_FR8r3Y_BwQDGsYoijjfnJNAC_SMLE6LoD3vXpK9QkQKkmlWrqM242U_AGqd8l0U0Ga8&q=The+superblock+could+not+be+read+or+does+not+describe+a+correct+ext2+filesystem.++If+the+device+is+valid+and+it+really+contains+an+ext2+filesystem+(and+not+swap+or+ufs+or+something+else)%2C+then+the+superblock+is+corrupt%2C+and+you+might+try+running+e2fsck+with+an+alternate+superblock%3A+++++e2fsck+-b+8193+%3Cdevice%3E+&btnG=Search&cx=012285703143635244993%3Ai9yr8qlpb18](http://www.google.com/custom?hl=en&client=google-coop-np&cof=AH%3Aleft%3BS%3Ahttp%3A%2F%2Fcrunchbang.org%2Fubuntu-search-engine%2F%3BCX%3AUbuntu%2520Search%2520Engine%3BL%3Ahttp%3A%2F%2Fcrunchbang.org%2Fimages%2Fbashful%2Fgoobuntu.gif%3BLH%3A100%3BLP%3A1%3BLC%3A%230000CE%3BVLC%3A%2352188C%3BGALT%3A%23009900%3B&adkw=AELymgW25L81GunVVYUg3-23UHs0XKw6F_VstKI0M1nKvKv-1Og_FR8r3Y_BwQDGsYoijjfnJNAC_SMLE6LoD3vXpK9QkQKkmlWrqM242U_AGqd8l0U0Ga8&q=The+superblock+could+not+be+read+or+does+not+describe+a+correct+ext2+filesystem.++If+the+device+is+valid+and+it+really+contains+an+ext2+filesystem+(and+not+swap+or+ufs+or+something+else)%2C+then+the+superblock+is+corrupt%2C+and+you+might+try+running+e2fsck+with+an+alternate+superblock%3A+++++e2fsck+-b+8193+%3Cdevice%3E+&btnG=Search&cx=012285703143635244993%3Ai9yr8qlpb18)

---

### Post by nogard on 2008-12-23
ok its solved

just small mistake in fstab

need to use /dev/sdb1 against of /dev/sdb1/

and i houpe the last questions about /dev/sXX
:)

now after deleting of swap partition I have ~250MB on /dev/sda5 not used

is there any way to attach it to /(root)?

---

### Post by Duck2006 on 2008-12-23
> **nogard said:**
> ok its solved

just small mistake in fstab

need to use /dev/sdb1 against of /dev/sdb1/

and i houpe the last questions about /dev/sXX
:)

now after deleting of swap partition I have ~250MB on /dev/sda5 not used

is there any way to attach it to /(root)?

Yes, use gparted to delete it and the extended partition and then add it to your / partition

---

### Post by nogard on 2008-12-24
> **Duck2006 said:**
> Yes, use gparted to delete it and the extended partition and then add it to your / partition

you mean somethin like 
mount /dev/sda5 / ?

and its all?

---

### Post by Duck2006 on 2008-12-24
> **nogard said:**
> you mean somethin like 
mount /dev/sda5 / ?

and its all?

Yes

---

### Post by nogard on 2008-12-24
thanks a lot!!!

---

