---
title: "Samba Weirdness"
date: 2013-12-15
forum: Networking &amp; Wireless
---

### Post by ylafont on 2013-12-15
I hoping someone can point me in the right direction. I have been trying to configure a DOS  Bootdisk to connect to Samba shares  on Ubuntu 12.10, yes I know, old stuff -it still has its uses.
 
I  am using the Universal TCPIP Boot Disk ([http://www.netbootdisk.com/](http://www.netbootdisk.com/)) to boot and obtain an IP from the server, which works fine. the bootdisk has  the Windows Millennium boot files, which come from windows XP. 

I am making 2 connections to two different servers. One is Ubuntu 12.10 and the other is Readynas Pro NAS.  I can map the shares without any problems. However i am getting weird results when I perform a directory listing.

On a Unbuntu share,  the results  i get something like this (depending on the share)


**THIN     0 12-01-13 4:54a**, this goes on a continuous loop and i have to reboot.  However, I can  navigate directories and execute applications any standard 16 bit DOS application. 

On the NAS,  I am able to perform Directory listing, but the results are odd.   File names and sizes do not correspond correctly (picture attached).

By the way, i am able to map the shares and view them correctly on a windows machine.



Assistance is greatly appreciated. thank you.

---

