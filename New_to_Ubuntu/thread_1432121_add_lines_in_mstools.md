---
title: "add lines in mstools?"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by BartlettMagic on 2010-03-17
hi all.  this is my first post as an Ubuntu noob, so please be patient.  

i'm having a problem with installing ipodLinux onto my iPod... so far, i've been following directions here: [http://ubuntuforums.org/showthread.php?t=1263715](http://ubuntuforums.org/showthread.php?t=1263715)

terminal:
jason@BFunkAllStars:~$ sudo fdisk -l
[sudo] password for jason: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8d64c3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18730   150448693+  83  Linux
/dev/sda2           18731       19457     5839627+   5  Extended
/dev/sda5           18731       19457     5839596   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 912 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           3       96264    0  Empty
/dev/sdb2               4         912    29206170    b  W95 FAT32
jason@BFunkAllStars:~$ sudo dd if=mbr-video30gb-2048.bin of=/dev/sdb
dd: opening `mbr-video30gb-2048.bin': No such file or directory
jason@BFunkAllStars:~$ cd Downloads
jason@BFunkAllStars:~/Downloads$ sudo dd if=mbr-video30gb-2048.bin of=/dev/sdb
1+0 records in
1+0 records out
512 bytes (512 B) copied, 2.57023 s, 0.2 kB/s
jason@BFunkAllStars:~/Downloads$ sudo hdparm -z /dev/sdb

/dev/sdb:
 re-reading partition table
jason@BFunkAllStars:~/Downloads$ sudo dd if=Firmware-25.6.3 of=/dev/sdb1
27160+0 records in
27160+0 records out
13905920 bytes (14 MB) copied, 13.8771 s, 1.0 MB/s
jason@BFunkAllStars:~/Downloads$ cd
jason@BFunkAllStars:~$

now, on that particular page, it instructs me to go to this link: [http://www.rockbox.org/wiki/IpodConversionToFAT32#For_5_5G_iPods ]("http://http//www.rockbox.org/wiki/IpodConversionToFAT32#For_5_5G_iPods")
because i (apparently unfortunately) have a 5.5G iPod.  this is where i run into snags.

it instructs me to use newfs_msdos, but i get this:

jason@BFunkAllStars:~$ sudo newfs_msdos -F 32 -S 2048 -v iPod /dev/rsdb2s2
sudo: newfs_msdos: command not found

then, using an 'older, alternative method', it says that i should add lines to mtools.conf- major snags here!

jason@BFunkAllStars:~$ sudo /.mtoolsrc drive i: file"/dev/sdb2"
sudo: /.mtoolsrc: command not found
jason@BFunkAllStars:~$ sudo ./mtoolsrc drive i: file"/dev/sdb2"
sudo: ./mtoolsrc: command not found
jason@BFunkAllStars:~$ cd mtools-4.0.13
jason@BFunkAllStars:~/mtools-4.0.13$ drive i: file="/dev/sdb2s2"
No command 'drive' found, did you mean:
 Command 'drivel' from package 'drivel' (universe)
drive: command not found

and that's just to restore iPod classic!  just imagine what happens when i then build off of the above to install ipodLinux, i eventually get to a point where i have to add a line to mtools.conf, but nowhere that i've been able to find (5 hrs of googling made me a bit frustrated) tells me exactly HOW to add a line to mtools.conf... i can't even find /etc/mtools.conf on my computer!

sorry for such a long post, i've been arguing with webpages and my terminal for 2 days now.  any help will be appreciated.  pity the noob and all his naivete!

---

### Post by BartlettMagic on 2010-03-18
the second link wasn't working for me now that i've checked on it-  my attempt at fixing:

[http://www.rockbox.org/wiki/IpodConversionToFAT32](http://www.rockbox.org/wiki/IpodConversionToFAT32)

under the heading of 5.5G

---

