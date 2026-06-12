---
title: "Accidently deleted Vista?"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by mickeymouseatlinux on 2011-07-24
hey, after getting bored of using windows for years, I decided to try Ubuntu.

my first problem began when i burned the disk, during the installation, it asked me to partition the OS's (or something along those lines; I'm REALLY bad with technology) after the partitioning, I was told that i may not have enough space to install Ubuntu alongside with Windows, but i proceeded anyways...

As warned, the installer then crashed, I tried to install Ubuntu once again, but was now left without the option to 'run alongside windows', and being me, I decided to *try* and be smart and started playing around with the 'Something Else' option, anyways, I deleted, moved, added created tables and all sorts until finally it allowed me to install Ubuntu. 

During this whole phase, I had not once thought about my Vista, which I now can't seem to find/open. When switching on my laptop, it goes straight into Ubuntu...



Yeah... Long story, help would be much appreciated though! :D

---

### Post by Rasa1111 on 2011-07-24
Open a terminal, (ctrl+alt+T) 
and paste this in and hit enter
```
sudo fdisk -l 
```

then type password and hit enter again. 
like so>  [ATTACH]198351[/ATTACH]

Then copy and post the output back here.
This will show us if you still have a windows partition or not.

---

### Post by XubuRoxMySox on 2011-07-24
Omygoodness! I'm so sorry!

The only thing I can offer is that re-installing Vista will wipe away Ubuntu. It's much *much* **MUCH** easier to install Ubuntu alongside Windows if Windows is installed first. Windows is a jealous OS and doesn't like to share disk space with another OS.

Ubuntu plays nice with Windows, though... *if there is room on your hard drive for both*. Put Vista back on first, then Ubuntu alongside it. My Xubuntu takes less than 10 gigs on my hard drive. But I give it 20 gigs just because, and a swap partition (roughly double my 'puter's RAM), and the rest is "/home" where all my pictures, music, schoolwork, browser favorites, e-mail settings and messages, etc are stored.

I love my Xubu so I gave it lots more room than it needs. 

I dunno how big your hard drive is, but if you post it someone can help you devise a partitioning scheme that lets you "dual-boot" (Ubu alongside Vists). But I can say with certainty that if you want them both on the same hard drive, install Vista *first*.

-Robin

---

### Post by sffvba[e0rt on 2011-07-24
Alas... prevention is better than cure...

@Rassa - 3 swap partitions?!


404

---

### Post by mickeymouseatlinux on 2011-07-24
> **Rasa1111 said:**
> Open a terminal, (ctrl+alt+T) 
and paste this in and hit enter
```
sudo fdisk -l 
```then type password and hit enter again. 
like so>  [ATTACH]198351[/ATTACH]

Then copy and post the output back here.
This will show us if you still have a windows partition or not.


I got this:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005e74c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3891    31249408   83  Linux
/dev/sda2            3891        7052    25390081    5  Extended
/dev/sda5            3891        7052    25390080   82  Linux swap / Solaris

```

---

### Post by JASONFUSARO on 2011-07-24
> **mickeymouseatlinux said:**
> I got this:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005e74c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3891    31249408   83  Linux
/dev/sda2            3891        7052    25390081    5  Extended
/dev/sda5            3891        7052    25390080   82  Linux swap / Solaris

```


It looks to me as if it is unfortunately been overwritten

---

### Post by IWantFroyo on 2011-07-24
> **JASONFUSARO said:**
> It looks to me as if it is unfortunately been overwritten

Same here.

Best to reinstall Vista. It's gone.

---

### Post by mickeymouseatlinux on 2011-07-24
hmm, well I guess it's not all bad, I do prefer Ubuntu over windows, but is there any way to recover some files? I may of had some items of semi-importance?

---

### Post by IWantFroyo on 2011-07-24
I doubt it. You can get data off of a freshly formatted disc, but this one was overwritten as well.

---

### Post by IHeequ5i on 2011-07-24
I believe that because the Vista partition is gone, your files are gone for good as well.  Very sorry this happened to you - I did the same thing to myself once.

---

### Post by mickeymouseatlinux on 2011-07-24
Okay, well thanks for the fast replies and help! :)

---

### Post by JASONFUSARO on 2011-07-24
You can take a look at things with testdisk


```


TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P HPFS - NTFS              0  32 33 13392  63 47  215144448 [WindowsVista]            

Bad relative sector.
Warning: Incorrect number of heads/cylinder 16 (FAT) != 255 (HD)
 2 * FAT32                13392  63 48 13417 190 21     409600 [BOOTGRUB]
 3 P Linux Swap           13417 190 22 14055  40  1   10240000
 4 E extended LBA         14055  40  2 60801  80 63  750977072
 5 L Linux                14055  72 34 16732 104 12   43008000 [Chakra]
   X extended             16732 124  1 21194 104 30   71680800
 6 L Linux                16732 136 45 21194 104 30   71680000 [UbuntuStudio64bi]
   X extended             21194 122  1 24381 150 25   51200944
 7 L Linux                21194 136 63 24381 150 25   51200000 [CtkArch64]
   X extended             24381 173  1 28206  45 63   61440624
 8 L Linux                24381 182 58 28206  45 63   61440000 [ArchBang]
   X extended             28206  78  1 31393  91 58   51200032
 9 L Linux                28206  78 33 31393  91 58   51200000 [UltimateEdition]
   X extended             31393 113  1 34580 137 53   51200720
10 L Linux                31393 124 28 34580 137 53   51200000 [TooroxGnome64]
   X extended             34580 164  1 37767 183 48   51200400
11 L Linux                34580 170 23 37767 183 48   51200000 [Puppy]
   X extended             37767 215  1 41974 193 11   67584080
12 L Linux                37767 216 18 41974 193 11   67584000 [Zorin]
   X extended             41974 214  1 43759 129 18   28670688
13 L Linux                41974 225 44 43759 129 18   28669952 [DistroHood]
    Next
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition



TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0  32 33 13392  63 47  215144448 [WindowsVista]
P FAT32 LBA            13392  63 48 13417 190 21     409600 [BOOTGRUB]
P Linux Swap           13417 190 22 14055  39 48   10239984
L Linux                14055  72 34 16732 104 12   43008000 [Chakra]
L Linux                16732 136 45 21194 104 30   71680000 [UbuntuStudio64bi]
L Linux                21194 136 63 24381 150 25   51200000 [CtkArch64]
L Linux                24381 182 58 28206  45 63   61440000 [ArchBang]
L Linux                28206  78 33 31393  91 58   51200000 [UltimateEdition]
L Linux                31393 124 28 34580 137 53   51200000 [TooroxGnome64]
L Linux                34580 170 23 37767 183 48   51200000 [Puppy]
L Linux                37767 216 18 41974 193 11   67584000 [Zorin]
L Linux                41974 225 44 43759 129 18   28669952 [DistroHood]
L Linux                43759 161 51 45325 224 19   25161728 [Slackware]
L Linux                45326   1 52 51877 144 43  105250816 [Zenwalk]
L Linux                51877 177 13 60801  80 15  143357952 [FusionLinux]




```

---

### Post by JASONFUSARO on 2011-07-24
jason@UbuntuStudio64bit:~$ testdisk

if you don't have it installed it will ask if you want to install or 

sudo apt-get install testdisk

---

### Post by Rasa1111 on 2011-07-24
> **mickeymouseatlinux said:**
> I got this:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005e74c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3891    31249408   83  Linux
/dev/sda2            3891        7052    25390081    5  Extended
/dev/sda5            3891        7052    25390080   82  Linux swap / Solaris

```


 Yep, Sorry buddy.
as others have said..
No windows file system on that drive. 
Seems you wiped it!

Sorry to hear it man. 
Though maybe it is a blessing? lol
 (if you didn't lose a lot of important data)
If you did, I take it back. 

Anyway, Welcome to Ubuntu!
and congrats on your first Linux goof!
(happens to the best). lol :P

Hope you get to like Ubuntu as much as I. :KS

---

### Post by XubuRoxMySox on 2011-07-25
Remember the lesson! And pass it along to other newbies to help them avoid some heartache.

I wrote a li'l article on "[Linux Lessons Learned]("http://www.linux.com/component/content/article/128-desktops/469787")" that I hope someone finds helpful... but I'd love to read yours when it's ready (I hope, someday soon)!

-Robin

---

### Post by westie457 on 2011-07-25
If you have another hard drive to write things to you might have some luck using photorec which comes with testdisk. You need the other hd because you cannot write to the partition you are reading from.

The process will take sometime. Have just tested on a 32GB sd card and the reading time for this is about 3 hours. So a normal sized hd (100GB) will be an over-night process.If it works you will be a very lucky (and happy) person and others can have some hope of recovering 'lost' information.

If it does not work then add my sympathies? to the list.

Good luck.

---

