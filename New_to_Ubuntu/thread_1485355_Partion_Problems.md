---
title: "Partion Problems"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by jnet on 2010-05-16
Hello! I was changing sizes of my partitions and now my ubunto partition is hidden. I can only see it from my ubunto life cd. I want to create a new partition for a new instalation but the other partions do not apear. How can I get my partions to apear again?

---

### Post by -humanaut- on 2010-05-16
Can use type " sudo fdisk -l " thats an L in a terminal and post back please.

---

### Post by jnet on 2010-05-22
[COLOR=#810081]I executed the fdisk -l command to show me thepartitions but I still can´t see it on gparted, and I try to install ubunto again it shows me one empty disk. But this what fdisk -l isplays:[/COLOR]
[COLOR=#810081][/COLOR] 
[COLOR=#810081][EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] sudo fdisk -l
omitting empty partition (5)[/COLOR]
[COLOR=#810081]Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0cdae68[/COLOR]
[COLOR=#810081]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            4132        4770     5132767+   c  W95 FAT32 (LBA)
/dev/sda3            4771        7296    20290095    f  W95 Ext'd (LBA)
/dev/sda4            4886        6939    16498755   83  Linux
/dev/sda5            4771        4885      923674+  82  Linux swap / Solaris[/COLOR]
_[COLOR=#810081][/COLOR]_[]("http://rs831.rapidshare.com/files/389471361/WAREZ-CORE.ME_IndiroseAP_MS_v8.0.1.0.rar")

---

### Post by jnet on 2010-05-22
> **-humanaut- said:**
> Can use type " sudo fdisk -l " thats an L in a terminal and post back please.
 
[COLOR=#810081]I executed the fdisk -l command to show me thepartitions but I still can´t see it on gparted, and I try to install ubunto again it shows me one empty disk. But this what fdisk -l isplays:

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)[/COLOR]
[COLOR=#810081]Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0cdae68[/COLOR]
[COLOR=#810081]Device Boot Start End Blocks Id System
/dev/sda1 * 1 2550 20482843+ c W95 FAT32 (LBA)
/dev/sda2 4132 4770 5132767+ c W95 FAT32 (LBA)
/dev/sda3 4771 7296 20290095 f W95 Ext'd (LBA)
/dev/sda4 4886 6939 16498755 83 Linux
/dev/sda5 4771 4885 923674+ 82 Linux swap / Solaris[/COLOR]

---

### Post by srs5694 on 2010-05-22
I suspect you've got an extended partition that's too big, but I'm not positive of that, because the "fdisk -l" command's precision is a bit lacking, since it shows  partition start and end points in cylinders rather than sectors. Check [this Web page]("http://www.rodsbooks.com/missing-parts/index.html") I wrote on the topic. If you need more help, post the output of "fdisk -lu", but please post the output between "[noparse]```
[/noparse]" and "[noparse]
```[/noparse]" strings, since that will improve legibility of monospaced columnar output.

---

### Post by jnet on 2010-05-22
> **srs5694 said:**
> I suspect you've got an extended partition that's too big, but I'm not positive of that, because the "fdisk -l" command's precision is a bit lacking, since it shows partition start and end points in cylinders rather than sectors. Check [this Web page]("http://www.rodsbooks.com/missing-parts/index.html") I wrote on the topic. If you need more help, post the output of "fdisk -lu", but please post the output between "[noparse]```
[/noparse]" and "[noparse]
```[/noparse]" strings, since that will improve legibility of monospaced columnar output.
 
I will check the web page. I forgot to mention that wile I was trying to change partition sides I had to turn something off (don't remember what) to be able to reside the  partitions.

---

