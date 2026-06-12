---
title: "fusesmb lists nothing in mounted directory"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by brendanarnold on 2008-03-12
I'd like to mount a Windows share to userspace in a similar way to mapping a network drive in Windows. Gnome VFS is halfway there, some apps don't recognise the Gnome VFS esp. the commandline.

I followed the instructions on the wiki ([https://help.ubuntu.com/community/FuseSmb]("https://help.ubuntu.com/community/FuseSmb")) but no luck, The directory is empty when I browse it.

Following is some debug output,

arnoldbj@phy068204:~$ fusesmb -d fileserver/
test
unique: 1, opcode: INIT (26), nodeid: 0, insize: 56
INIT: 7.8
flags=0x00000003
max_readahead=0x00020000
   INIT: 7.8
   flags=0x00000000
   max_readahead=0x00008000
   max_write=0x00020000
   unique: 1, error: 0 (Success), outsize: 40
unique: 2, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 2, error: 0 (Success), outsize: 112
unique: 3, opcode: ACCESS (34), nodeid: 1, insize: 48
ACCESS / 04
   unique: 3, error: -38 (Function not implemented), outsize: 16
unique: 4, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 4, error: 0 (Success), outsize: 112
unique: 5, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 5, error: 0 (Success), outsize: 112
unique: 6, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 6, error: 0 (Success), outsize: 112
unique: 7, opcode: OPENDIR (27), nodeid: 1, insize: 48
   unique: 7, error: 0 (Success), outsize: 32
unique: 8, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 8, error: 0 (Success), outsize: 112
unique: 9, opcode: READDIR (28), nodeid: 1, insize: 64
   unique: 9, error: -2 (No such file or directory), outsize: 16
unique: 10, opcode: RELEASEDIR (29), nodeid: 1, insize: 64
   unique: 10, error: 0 (Success), outsize: 16


Any ideas?

Brendan

---

