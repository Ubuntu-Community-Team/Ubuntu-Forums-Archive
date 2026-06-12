---
title: "Installtion issues"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by NOOBUNTU54961 on 2008-12-20
I just installed UBUNTU 8.10 on my new notebook ,, I followed the "PICTURE" instructions for "dual boot" but now I cannot find the wind0ws vist@ partition ...What did I do wrong??,I need detailed step by step instructions for this one...See my username for cryin out loud

                                       Randy

---

### Post by adult swim on 2008-12-20
go to a terminal (applications>accessories>terminal) and type in ```
sudo fdisk -lu
``` hit enter.  it will ask for your password, type that in and hit enter.  next copy and paste what it returns here.

---

### Post by NOOBUNTU54961 on 2008-12-20
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca8842c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     9173114     4586526   83  Linux
/dev/sda2         9173115   312576704   151701795    5  Extended
/dev/sda5       301218813   312576704     5678946   82  Linux swap / Solaris
/dev/sda6         9173241    20354354     5590557   83  Linux
/dev/sda7       289860858   301218749     5678946   82  Linux swap / Solaris
/dev/sda8        20354418   278824139   129234861   83  Linux
/dev/sda9       278824203   289860794     5518296   82  Linux swap / Solaris

Partition table entries are not in disk order
randy@randy-laptop:~$

---

### Post by dasunst3r on 2008-12-20
It appears that you had the Ubuntu installer do the partitioning automatically.  I don't see any HPFS/NTFS partitions in your output.

Here's mine:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006ce01

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        2676      522112+  82  Linux swap / Solaris
/dev/sda3            2677        5222    20450745   83  Linux
/dev/sda4            5223        9729    36202477+   7  HPFS/NTFS
```
So, you will need to reinstall Windows Vista, giving it a small partition, and then reinstall Ubuntu, using the manual partitioning method.

---

### Post by NOOBUNTU54961 on 2008-12-20
Ok..now,another question...my wireless card is not showing up...I know the mfg and model but when I try to download drivers Iget an error msg

---

### Post by adult swim on 2008-12-20
wireless can be a whole other animal.  what kind of wireless card do  you have?

---

### Post by zman58 on 2008-12-20
> **NOOBUNTU54961 said:**
> Ok..now,another question...my wireless card is not showing up...I know the mfg and model but when I try to download drivers Iget an error msg

You really do need to be more specific. What is the wireless adapter mfr and model and what do you get for error message?

Have you checked any compatibility lists for wireless adapters and Linux to get an idea if your adapter is fully/partially/ or non functional under Linux?

---

### Post by NOOBUNTU54961 on 2008-12-20
Atheros 242X

---

### Post by adult swim on 2008-12-20
if you can connect the machine to wired internet, check out post 2 here
[http://ubuntuforums.org/showthread.php?t=967520](http://ubuntuforums.org/showthread.php?t=967520)

---

### Post by NOOBUNTU54961 on 2008-12-20
the error I get is..." An error occurred while loading the archive

---

### Post by wolfen69 on 2008-12-20
> **NOOBUNTU54961 said:**
> Atheros 242X

go to system>software sources and check off backports repository. it will ask to reload. do so. then:
```
sudo apt-get install linux-backports-modules-intrepid-generic

```then
```
sudo modprobe ath5k
```then:
```
sudo -s
echo blacklist ath_pci >> /etc/modprobe.d/blacklist
```
reboot.

---

### Post by adult swim on 2008-12-20
EDIT: try wolfen69's advice

---

### Post by zman58 on 2008-12-20
I have not much experience with that one, but I did find someone who perscribed a solution for the Atheros 242X hardware on Ubuntu Hardy. Perhaps you can try these instructions. Two parties responded favorably with success on these instructions:
[http://ubuntuforums.org/showthread.php?t=921329](http://ubuntuforums.org/showthread.php?t=921329)
I hope that will help you out.

---

