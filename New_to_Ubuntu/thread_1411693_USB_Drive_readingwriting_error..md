---
title: "USB Drive reading/writing error."
date: 2010-02-20
forum: New to Ubuntu
---

### Post by nns2006 on 2010-02-20
HI,
I have a Kingston 64 Gb pendrive.I can perfectly mount it and unmount it in windows and Ubuntu with ease before i formatted it to ext4 file type. The reason i did it was Whenever i am copying a file on it is showing somw weird type of things in the folder. Summing up.. I am not able to use it properly.

Any advice is welcome .
I am, attaching the screenshot and output of [HTML]dmesg | tail[/HTML]. 

[HTML]ravi@ravi-desktop:~$ dmesg | tail
[13146.652854] sd 8:0:0:0: [sdb] 131072000 512-byte hardware sectors: (67.1 GB/62.5 GiB)
[13146.653504] sd 8:0:0:0: [sdb] Write Protect is off
[13146.653508] sd 8:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[13146.653509] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[13146.653516]  sdb: sdb1
[13146.654351] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[13146.654454] sd 8:0:0:0: Attached scsi generic sg2 type 0
[13147.166940] EXT4-fs: barriers enabled
[13147.167423] JBD: no valid journal superblock found
[13147.167425] EXT4-fs: error loading journal.[/HTML]

---

