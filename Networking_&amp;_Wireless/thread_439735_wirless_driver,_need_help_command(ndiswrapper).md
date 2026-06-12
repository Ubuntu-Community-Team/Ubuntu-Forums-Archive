---
title: "wirless driver, need help command(ndiswrapper)"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by andytx on 2007-05-11
andy@andy-ubuntu:~$ ndiswrapper -l
net8185x64 : driver installed
andy@andy-ubuntu:~$ ndiswrapper -e net8185x64
couldn't delete /etc/ndiswrapper/net8185x64: Inappropriate ioctl for device
andy@andy-ubuntu:~$ sudo ndiswrapper -e net8185x64
Password:
andy@andy-ubuntu:~$ cd '/home/andy/Desktop/4/VISTAx64' 
andy@andy-ubuntu:~/Desktop/4/VISTAx64$ ls
BLKWGDv8.cat  BLKWGDv8.inf  BLKWGDv8x64.sys
andy@andy-ubuntu:~/Desktop/4/VISTAx64$ ndiswrapper -i BLKWGDv8.inf
couldn't create /etc/ndiswrapper/blkwgdv8: Permission denied at /usr/sbin/ndiswrapper-1.9 line 146.
andy@andy-ubuntu:~/Desktop/4/VISTAx64$ sudo ndiswrapper -i BLKWGDv8.inf
installing blkwgdv8 ...
andy@andy-ubuntu:~/Desktop/4/VISTAx64$ ndiswrapper -l
blkwgdv8 : driver installed
        device (1799:700F) present
andy@andy-ubuntu:~/Desktop/4/VISTAx64$ sudo ndiswrapper -m
module configuration already contains alias directive

andy@andy-ubuntu:~/Desktop/4/VISTAx64$ 


andy@andy-ubuntu:~/Desktop/4/VISTAx64$ sudo ndiswrapper -m
module configuration already contains alias directive   << Why it said already, Can Anyone help 

Thanks

On

---

### Post by ghostboy on 2007-05-11
> **andytx said:**
> andy@andy-ubuntu:~$ ndiswrapper -l
net8185x64 : driver installed
andy@andy-ubuntu:~$ ndiswrapper -e net8185x64
couldn't delete /etc/ndiswrapper/net8185x64: Inappropriate ioctl for device
andy@andy-ubuntu:~$ sudo ndiswrapper -e net8185x64
Password:
andy@andy-ubuntu:~$ cd '/home/andy/Desktop/4/VISTAx64' 
andy@andy-ubuntu:~/Desktop/4/VISTAx64$ ls
BLKWGDv8.cat  BLKWGDv8.inf  BLKWGDv8x64.sys
andy@andy-ubuntu:~/Desktop/4/VISTAx64$ ndiswrapper -i BLKWGDv8.inf
couldn't create /etc/ndiswrapper/blkwgdv8: Permission denied at /usr/sbin/ndiswrapper-1.9 line 146.
andy@andy-ubuntu:~/Desktop/4/VISTAx64$ sudo ndiswrapper -i BLKWGDv8.inf
installing blkwgdv8 ...
andy@andy-ubuntu:~/Desktop/4/VISTAx64$ ndiswrapper -l
blkwgdv8 : driver installed
        device (1799:700F) present
andy@andy-ubuntu:~/Desktop/4/VISTAx64$ sudo ndiswrapper -m
module configuration already contains alias directive

andy@andy-ubuntu:~/Desktop/4/VISTAx64$ 


andy@andy-ubuntu:~/Desktop/4/VISTAx64$ sudo ndiswrapper -m
module configuration already contains alias directive   << Why it said already, Can Anyone help 

Thanks

On


Which wireless driver are you trying to install?

---

