---
title: "Not Enough Disk Space"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Ravio on 2010-01-22
I have installed Ubuntu 9.0, I am very new to Linux the problem i am facing is after installing the Ubuntu it worked fine after a few updates i donot have any disk space left on the system . 

When i run the Disk usage Analyzer it shows that there 0% space left in "/". C an some one help me how to clean up the disk space i donot want to delete any system data while cleaning up .

---

### Post by 73ckn797 on 2010-01-22
Go to Applications/Accessories/Terminal

Enter the following ```
sudo fdisk -l
``` That is a lower case L. Copy the results and paste into a reply.

Did you install to the entire hard drive or to a smaller partition? It would help to know how much space was allocated to the Ubuntu install.

---

### Post by gsgkill on 2010-01-23
I did the same thing on a netbook. i'ts because on the Partioner you probably selected side by side instead of use the whole partition. On whole partion it sets up a swap drive 1.2 gig or so. So if you by chance install a second time and select side by side you might get the swap file for your new Ubuntu install. which is what i did and what I got.  Do the manual partion for dual boot, if you don't like the sizes. :o

---

### Post by Ravio on 2010-02-18
Hey Guys Sorry for the late rsponse got my hand broken so ...........

Here is the result of the command you ask me to run :-

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   42  SFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd228d228

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2433    19543041    7  HPFS/NTFS
/dev/sdb2            2434        9728    58597087+   f  W95 Ext'd (LBA)
/dev/sdb5            2434        4983    20482843+   7  HPFS/NTFS
/dev/sdb6            4984        6258    10241406    b  W95 FAT32
/dev/sdb7            6259        7533    10241406    b  W95 FAT32
/dev/sdb8            7534        7928     3172806   83  Linux
/dev/sdb9            8172        9728    12506571    b  W95 FAT32
/dev/sdb10           7929        8171     1951866   82  Linux swap / Solaris

Please let me know what to do to free my disk space for ubuntu

---

### Post by Ravio on 2010-02-18
I did not use the the entire disk i just created a partion and installed the os as i am a little slow i have no clue what to do :( i know that you cannot just go ahead and delete styuff as we usaly do on windows so help will be appricated

---

### Post by plucky on 2010-02-18
```
/dev/sdb8 7534 7928 3172806 83 Linux
/dev/sdb10 7929 8171 1951866 82 Linux swap / Solaris

```

Your linux / partition is approximately 3G which is why you have run out of space.I would recommend you increase the size of the partition to at least 10G.

The swap partition is approx 2G and should be at least the size of memory.

Post output of a terminal  ```
df -h
free -m
```

Good Luck

---

### Post by Miljet on 2010-02-18
You have a lot of partitions on a 80G dard drive. You have three different FAT 32 partitions. What do you have in sda9? If it is possible to move whatever is there, it will be simple to add that space to your Ubuntu partition.

---

