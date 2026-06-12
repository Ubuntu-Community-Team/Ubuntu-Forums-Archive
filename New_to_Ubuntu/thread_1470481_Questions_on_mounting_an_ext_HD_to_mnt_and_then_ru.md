---
title: "Questions on mounting an ext HD to /mnt and then running rsync"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by mikodo on 2010-05-02
Hello everyone,

I am very nervous of running the last 3 commands. Please check them for me, to see if they are correct, and that they answer my three questions at the end.

mikodo@mikodo-desktop:~$```
 sudo fdisk -l
```[sudo] password for mikodo: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1402    11261533+  83  Linux
/dev/sda2            1403        3503    16876282+  83  Linux
/dev/sda3            3504       15893    99522644+   5  Extended
/dev/sda5            3504        4140     5116671   82  Linux swap / Solaris
/dev/sda6            4141       15893    94405941   83  Linux

**Disk /dev/sdf: 500.1 GB, 500107862016 bytes**
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce5ab5a6

mikodo@mikodo-desktop:~$ ```
sudo blkid
```/dev/sda1: UUID="d5db7f2a-c157-4a51-96ab-f0c507859c41" TYPE="ext4" 
/dev/sda2: UUID="fbd190bf-533f-4f7f-b4f5-47348668f84c" TYPE="ext4" 
/dev/sda5: UUID="4af0b0bf-6e35-47fa-991a-d5b8ea083614" TYPE="swap" 
/dev/sda6: UUID="88f9be7b-38ba-44d3-99e9-e9acec1ce5ce" TYPE="ext4" 
[B]/dev/sdf1: LABEL="data_storage" UUID="9d285ab4-f391-497b-ac4a-99a8036e3663" TYPE="ext4"
[/B]  
mikodo@mikodo-desktop:~$ ```
sudo mkdir /mnt/data_storage
``` *****(I now have {data_storage} attached with the sub-directory mnt)**.

[B]The following three commands have not been run yet:
[/B] 
1. mikodo@mikodo-desktop:~$ ```
sudo mount /dev/sdf1 /mnt/data_storage
```2. mikodo@mikodo-desktop:~$ ```
sudo rsync -av /home/mikodo/ /dev/sdf1/
```3. mikodo@mikodo-desktop:~$ ```
sudo rsync -av /dev/sdf1/ /home/mikodo/

```**Questions:**

1. Will this command properly mount my external HD (paritioned as /dev/sdf1) to /mnt/data-storage?

2. If, command 1 is correct, is this exactly, how to run a rsync backup, with the forward slashes all correct? 

3. If, commands 1 and 2 are correct, will this command with the forward slashes exactly as they are, return all my /home data to my /home partition, if/when needed?

**Thank you.**

---

