---
title: "grub"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by sir_napsalot on 2009-09-24
I currently have Windows XP and Ubuntu 9.04 installed on two separate HDD's. The only problem is I don't know the entry that would be required in the GRUB list to allow the system to look on the other hard drive for Windows XP. Any help is greatly appreciated.

---

### Post by JuergenF on 2009-09-24
No entry was created?
It should look like
```
title           Microsoft Windows XP Professional 
root            (hd1,0)
chainloader     +1
```
In (hdx,y) x is the drive and y is the partition - both are 0-based.

In menu.lst are comments showing where to put this entry so it is not removed by updates.

---

### Post by sir_napsalot on 2009-09-24
thank you, will test it shortly

---

### Post by sir_napsalot on 2009-09-24
Unfortunately it didn't work. When I selected the windows entry it only said "Starting up..." and went no further

---

### Post by QIII on 2009-09-24
Windows likes to think it's the only kid on the block and gets confused. Use "map" to trick it into believing it is your one and only true love.

To complete the suggested edit given above...

```
title        Vista
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map         (hd1) (hd0)
chainloader    +1
```

---

### Post by oldfred on 2009-09-24
To understand where drives & partitions are we need details. The best way is to download this script:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
creates results.txt in the same directory, post with code tags as it will be long.

---

### Post by QIII on 2009-09-25
Or, cut and paste the results of

```
sudo fdisk -l
```

That's a small "ell", not a "one".

---

### Post by sir_napsalot on 2009-09-26
these are the results of
```
sudo fdisk -l
```

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4fca4fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60247   483933996   83  Linux
/dev/sda2           60248       60801     4450005    5  Extended
/dev/sda5           60248       60801     4449973+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d3f9d92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS
```

---

### Post by QIII on 2009-09-26
OK.  Did you try the edits I suggested?

(Yours looks just like mine, except that mine are 750GB drives ;))

---

### Post by oldfred on 2009-09-26
QIII entries look correct to me also. Unless you have a problem with the window install on your second drive. Since it is a second drive it may still have the windows boot in its MBR if it was installed that way. 

You can quickly test that by switching the drive order in BIOS and see if windows boots (you will not see grub or ubuntu on first drive) and should change order back if windows boots. If it does not boot there is an issue with your windows install. If it does not work leave windows first and use fix mbr & fixboot from the windows install CD.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

---

