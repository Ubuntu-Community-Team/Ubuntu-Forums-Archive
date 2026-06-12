---
title: "[SOLVED] NDISWRAPPER problem"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by juBB on 2007-09-28
Hi, i just installed Ubuntu 6.06 last night (i'm a window user) and wish to get my wireless working again. I have seen tutorials on how to get my MA111 working and they are easy enough to follow, but i am having a problem installing "ndiswrapper".
i have the CD in the drive but get this message. 

chris@Ubuntu:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
ndiswrapper-source
The following NEW packages will be installed:
ndiswrapper-utils  
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/27.6kB of 
archives.
After unpacking 139kB of additional disk space will be used.
Err cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1) dapper/main 
ndiswrapper-utils 1.8-0ubuntu2[/SIZE][/SIZE][/SIZE]
Unable to stat the mount point /cdrom/ - stat (2 No such file or directory)
Failed to fetch cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 
(20060806.1)]/pool/main/n/ndiswrapper/ndiswrapper-utils_1.8-0ubuntu2_i386.deb  Unable to stat 
the mount point /cdrom/ - stat (2 No such file or directory)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


	:confused:

An easy to understand solution to this problem would be greatly appreciated since im new to this, thanks!

---

### Post by juBB on 2007-09-29
works now. just copied ndiswrapper-utlis.deb to desktop and launched from their.

---

