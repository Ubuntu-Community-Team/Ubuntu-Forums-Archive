---
title: "boot loader Big Installing Issue !"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by asel_ on 2009-02-21
[SIZE="5"]Hi all, I want to install ubuntu server on my new computer, which have two hdd , one IDE and another one Sata, my goal is to install the system on IDE hard disk with 80 GB, and mount the sata one (entire the sata hard disk to a folder, e.g. /files) to hold the files on it, the problem I faced is, during installation and in the manual partioning the hdds, the sata hdd is be 1st hdd and the boot loader is installed in it , while the computer deal with IDE hdd as boot hard disk , and the system doesn't boot .Now , How to get rid of this ? I mean how to choose the place where the boot sector should be on the IDE hdd not on sata ?

The following information may help :

The installing deal with SATA HDD AS sda (SCSI1),and the IDE HDD as sdb (SCSI3)


Thank you in advance . :)[/SIZE]

---

### Post by asel_ on 2009-02-21
Additional information :

I want to make this layout :

For IDE (80GB) hard disk :

100 Mb ==> /boot
40 GB ==> / (The system)
2 GB ==> SWAP
available free space ==> (for another porpuses)

For SATA (320GB) hard disk :
/file (to store the file on it and share it over wired LAN, using samba ofcourse :) )

---

### Post by asel_ on 2009-02-21
any help ?:D

---

### Post by asel_ on 2009-02-21
Please I need help ! really I need to finish this issue guickly

---

### Post by louieb on 2009-02-21
on the summay page just before the install begins there is an advanced button.
press it. Thats the place to tell it to install grubs stage1 code someplace other than the default.

Good stuff here if you use the alternate install CD. [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by sandyd on 2009-02-21
```

sudo grub
root (hd1)
setup (hd1)

```

---

### Post by cariboo on 2009-02-21
On my system I have the same sort of thing, 250Gb PATA and 160Gb SATA the system sees the SATA disk as the first disk and IDE disk as the second disk, just install grub on the first disk (SATA) and all will work the way it is supposed to.

Jim

---

### Post by asel_ on 2009-02-22
Thank you all for your reply, anyway , I removed the sata hdd, and re-install ubuntu server, and it is booting fine now, and then I install the sata hdd , and using mkfs.ext3 , I formated the sata hdd,but now the blkid report that sec_type = ext2 !! while I used ext3 ? anyway thank you for your reply.

---

