---
title: "WD Mybook II White Light doesn't boot 2TB"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by pmoreno on 2011-07-31
Ok, I have (apparently) 2 TB in raid 1, and it doesn't boot, 1 light blinks sometimes at the top and it has 1 at bottom steady. 
Here is what TetDisk shows for drive [B] partitions:
TestDisk 6.13-WIP, Data Recovery Utility, May 2011
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
>D Linux                    4   0  1   247 254 63    3919860
 D Linux RAID               4   0  1   247 254 63    3919860 [md0]
 D Linux Swap             248   0  1   279 254 63     514080
 D Linux RAID             248   0  1   279 254 63     514080 [md126]
 D Linux                  280   0  1   402 254 63    1975995
 D Linux RAID             280   0  1   402 254 63    1975995 [md127]
First partition has some of the following directories/files on it:
Directiories: bin, cachevolume, datavolume, dev, etc, extendvolume, lib, linuxrc,mnt,opt,proc,proto,root,sbin,shares,sys,tmp,trustees,twonky,usr,var,.rnd,nfs, configuration.

I listed the files and it seems that everything is in there but it doesn't boot. should 1 of this partitions must be the Primary bootable?, if so how can I make it bootable?

second hard drive [A] shows structure as follows: (this one seems to contain the whole data that I put there once..
TestDisk 6.13-WIP, Data Recovery Utility, May 2011
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
 D Linux                    4   0  1   247 254 63    3919860
 D Linux RAID               4   0  1   247 254 63    3919860 [md0]
 D Linux Swap             248   0  1   279 254 63     514080
 D Linux RAID             248   0  1   279 254 63     514080 [md1]
 D Linux                  280   0  1   402 254 63    1975995
 D Linux RAID             280   0  1   402 254 63    1975995 [md3]
>* Linux                  403   0  1 121576 254 63 1946660310

this last one seems to be the primary bootable, and appears at linux as sda1 (linux doesn't mount disk [B]), and I can see all the information on it.

I don't want to loose the information I have, if there is anything I can do, please help.

Pablo

---

