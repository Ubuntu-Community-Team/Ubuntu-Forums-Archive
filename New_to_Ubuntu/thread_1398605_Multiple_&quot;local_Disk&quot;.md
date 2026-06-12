---
title: "Multiple &quot;local Disk&quot;"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by PoseidonOSU on 2010-02-04
I did a search and couldn't seem to find it any where. 

I have 2 hard disks in my computer. One of them is partitioned into 2 drives, giving me a total of 3 drives. 

Before the drives were "LOCAL DISK" "163.0 GB Media", and "50?.? GB Media"

well the 500GB disk has renamed itself "Local Disk" (notice not all caps like other drive) 

Now windows cant access the 500gb drive and I have one called "LOCAL DISK" and one "Local Disk" and the 163gb of course. 

Anyway to get it renamed or assigned as it should be?

---

### Post by oldfred on 2010-02-04
Have you labeled your partitions?

To set a label without reformatting use e2label or tune2fs

   2. Make a label
      e2label <dev> <label>
      tune2fs -L <label> <dev>


to see labels:
ls /dev/disk/by-label -lah

---

### Post by warfacegod on 2010-02-04
An easy way to label partitions is: System> Admin.> Disk Utility. Assuming you are using 9.10

---

