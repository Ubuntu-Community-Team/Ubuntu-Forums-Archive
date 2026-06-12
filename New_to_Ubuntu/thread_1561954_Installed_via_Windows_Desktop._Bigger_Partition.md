---
title: "Installed via Windows Desktop. Bigger Partition?"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by wc5b on 2010-08-26
During install of 10.04 it only allowed up to 30GB partition. Is there a way to extend that post install using some of the NTFS C:/ and move it over?

---

### Post by wc5b on 2010-08-27
Any help on this one?

---

### Post by Rubi1200 on 2010-08-27
Hi,
to answer the question you need to provide us with a lot more information.

1. how big is the drive?
2. what operating systems do you have installed?
3. post the output of ```
sudo fdisk -l 
```from the terminal

Any other relevant information would also help us, such as how comfortable are you with doing manual partitioning etc.?

And, yes, it is theoretically possible but we need the information I asked for to advise you on the correct way to approach this.

Thanks.

---

### Post by wc5b on 2010-08-27
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd9b3496e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15356928   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1912       38914   297211904    7  HPFS/NTFS

```I have a 320GB. It had Vista on it 100%. I used WUBI to install and was hoping to use at least 80GB (Up to 120GB) towards ubuntu, but WUBI seemed to restrict me to 30GB. My exact question, just so we are on the same page, is if I can steal more from the MS Partition and convert it over to linux fs while still keeping the Vista dual boot intact and functional.

---

### Post by Rubi1200 on 2010-08-27
Apparently, it can be done, but you have enough space?
[https://wiki.ubuntu.com/WubiGuide#How%20big%20should%20the%20the%20virtual%20disks%20be?](https://wiki.ubuntu.com/WubiGuide#How%20big%20should%20the%20the%20virtual%20disks%20be?)

See the relevant section for resizing:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

I don't use Wubi, so I am not in a position to tell you if there are likely to be potential problems doing this.

If you are happy using Ubuntu, why not consider dual-booting with a regular install to the drive?

---

### Post by bcbc on 2010-08-27
Yes, if you want an 80GB install, it's best to install directly to partition. Remember wubi uses a virtual drive which will be a single 80GB file. This is probably going to make things slower and more prone to corruption.

Plus it's completely unnecessary, you can just store your data on ntfs - and provide symbolic links to it if necessary (so it looks like /home/Picture, but it's really /media/xxx/Shared/Pictures).

Then you can access them on ntfs too.

---

