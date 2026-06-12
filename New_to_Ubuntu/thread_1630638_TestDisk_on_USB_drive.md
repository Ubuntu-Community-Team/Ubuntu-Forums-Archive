---
title: "TestDisk on USB drive"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by ubuntorox on 2010-11-25
Hi

I was unable to access my USB drive, I ran TestDisk 6.11.3 from [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
There should be one FAT32 partition of 1GB.
Now I can access the drive, but the files are corrupt. I think I'm using the wrong partition table.

I got:
check_FAT: Unusual number of reserved sectors 8 (FAT), should be 1.
 1 P FAT16 >32M               0   1  1   121 254 63    1959867 [NO NAME]


Interface Advanced
Geometry from i386 MBR: head=115 sector=50
BAD_RS LBA=778135908 5742552
check_part_i386 1 type 72: no test
BAD_RS LBA=168689522 4634007
BAD_RS LBA=1869881465 5881838
check_part_i386 3 type 79: no test
BAD_RS LBA=0 5982340
check_part_i386 4 type 0D: no test
get_geometry_from_list_part_aux head=255 nbr=1
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=1
 4 * Sys=0D                   0   0  1 226406 223 57 3637226496
 2 * NetWare 3.11+        10500 111 30 131012 158 28 1936028240
 1 * Sys=72               48436 183 40 119492 104  7 1141509631
 3 * Sys=79               116394 188 12 236906 234 25 1936028192

what are these partitions? which one should I restore?
Thanks for any help!

---

### Post by karthick87 on 2010-11-25
Plugin your USB drive and type 
```

sudo fdisk -l
```

and post the outputs here.

---

