---
title: "!Help recover files! Photorec to internal HD. How?"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by ImmigrantUS on 2009-12-10
Please help! I’m trying to recover jpeg files from master HD Ubuntu partition by using Photorec on latest Rescue-Remix live CD. Intend to put recovered files into secondary (slave) HD. And stumbling at choosing it…
  When booting into R-R live CD, both HDs listed, then I choose master to recover files from, go thru options till choosing secondary internal HD to put recovered files into, and it is not in the list… When checked previously it’s labeled Media/Disk, but when I go twice up directory thru double dot to Media, “Disc” is not there…
I tested this procedure with secondary internal HD disconnected – and all lines in menu are exactly the same when trying to choose the secondary internal drive to put files into…
   What to do? Should I mount secondary internal HD in Rescue-Remix before starting Photorec? If yes, how? Or should I make additional directory on secondary HD first and look for it? Or what else?
Please help! :confused::confused:

---

### Post by DGortze380 on 2009-12-10
> **ImmigrantUS said:**
> Please help! I’m trying to recover jpeg files from master HD Ubuntu partition by using Photorec on latest Rescue-Remix live CD. Intend to put recovered files into secondary (slave) HD. And stumbling at choosing it…
  When booting into R-R live CD, both HDs listed, then I choose master to recover files from, go thru options till choosing secondary internal HD to put recovered files into, and it is not in the list… When checked previously it’s labeled Media/Disk, but when I go twice up directory thru double dot to Media, “Disc” is not there…
I tested this procedure with secondary internal HD disconnected – and all lines in menu are exactly the same when trying to choose the secondary internal drive to put files into…
   What to do? Should I mount secondary internal HD in Rescue-Remix before starting Photorec? If yes, how? Or should I make additional directory on secondary HD first and look for it? Or what else?
Please help! :confused::confused:

I've never used the rescue remix. Can you get to a terminal?
If so, post the output of 

```

sudo fdisk -l

```

---

### Post by ImmigrantUS on 2009-12-10
@ DGortze380 - Rescue-Remix is a live CD with a shell for many recovery programs. It works thru its own terminal interface. I'm trying to use Photorec in it by "sudo photorec"

I just checked "sudo fdisk-l" in R-R live CD and it sees both HDs (120GB master and 100 GB secondary). On secondary it says that partition sdb5 does not end on cylinder boundary. I don't know how to copy this info from live CD session... (?) So, this is an output from terminal back in master HD: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df9b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         574     4610623+  83  Linux
/dev/sda2             575        2557    15928447+  83  Linux
/dev/sda3            2558        2800     1951897+  82  Linux swap / Solaris

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df97c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2438    19583203+   c  W95 FAT32 (LBA)
/dev/sdb2            2439        6109    29487307+  83  Linux
/dev/sdb3            6110        6960     6835657+   5  Extended
/dev/sdb5            6110        6352     1951866   82  Linux swap / Solaris
/dev/sdb6            6353        6960     4883728+   b  W95 FAT32

---

### Post by DGortze380 on 2009-12-10
> **ImmigrantUS said:**
> @ DGortze380 - Rescue-Remix is a live CD with a shell for many recovery programs. It works thru its own terminal interface. I'm trying to use Photorec in it by "sudo photorec"

I just checked "sudo fdisk-l" in R-R live CD and it sees both HDs (120GB master and 100 GB secondary). On secondary it says that partition sdb5 does not end on cylinder boundary. I don't know how to copy this info from live CD session... (?) So, this is an output from terminal back in master HD: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df9b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         574     4610623+  83  Linux
/dev/sda2             575        2557    15928447+  83  Linux
/dev/sda3            2558        2800     1951897+  82  Linux swap / Solaris

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df97c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2438    19583203+   c  W95 FAT32 (LBA)
/dev/sdb2            2439        6109    29487307+  83  Linux
/dev/sdb3            6110        6960     6835657+   5  Extended
/dev/sdb5            6110        6352     1951866   82  Linux swap / Solaris
/dev/sdb6            6353        6960     4883728+   b  W95 FAT32

Ok good. Next try mount -l (lower case L)

If your second drive isn't listed, mount it manually.

sudo mkdir /media/disk
sudo mount -t ext3 /dev/sdb# /media/disk

replace # with your partition number

---

### Post by ImmigrantUS on 2009-12-11
Used Photorec on Ubuntu Rescue-Remix CD yesterday to recover deleted files in Ubuntu. Thanks DGortze380 for help! 

    Lessons learned: 
 If using secondary internal HD (suspect the same for external HD;))for recovered file import (from main HD, where the files originally were), it's necessary to make a directory, into which the files will be put in secondary HD. 
 To do it_you need to have BIOS setting for booting from CD first!_. 
 1. Start Live Ubuntu Rescue-Remix CD, give command to boot, then when it boots into terminal, check your HDs by command - ```
sudo fdisk -l
``` Realize what HD is main, and which is secondary, and what partition to check for files and into which to recover them - linux ext3 or Windows NTFS! _Mine was Linux, sdb2_. Have enough room on it!
(Then you can try to run Photorec ("sudo photorec") and hopefully you'll be able to see all your HDs. I was not that lucky, so I had to make directory and mount sec. HD.)

 2. Make directory for recovered files first, e.g. - media/disk. Give command - ```
sudo mkdir /media/disk
``` If alright, terminal prompt simply returns.

 3. Must mount secondary HD, or it'll be invisible, even if "sudo fdisk -l" does show it. Give command for your secondary HD - ```
sudo mount -t ext3 /dev/sdb2 /media/disk
```  If alright, terminal prompt simply returns.

 4. Run Photorec by command - ```
sudo photorec
```
 Go thru settings, and only choose file types that you want, otherwise you'll have thousands of files to sift thru! I had 25000.
 Graphical manual how to run Photorec read at -> [http://www.psychocats.net/ubuntucat/recoverdeletedfiles/]("http://www.psychocats.net/ubuntucat/recoverdeletedfiles/")
--------------------------------------------------------------

 Unfortunately, I did not find my photos (jpegs) in recovered files...
I suspect they were over-written, and I'm not sure if it's possible to recover them... Is it? If anyone knows, please tell me! 
 Will try DD rescue and others in upcoming days.

 Good luck to everybody!

---

