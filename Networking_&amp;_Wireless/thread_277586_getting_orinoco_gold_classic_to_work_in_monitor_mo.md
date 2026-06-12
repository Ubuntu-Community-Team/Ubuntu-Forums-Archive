---
title: "getting orinoco gold classic to work in monitor mode"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by webcrawler42 on 2006-10-14
i have been fallowing this guide [https://wiki.ubuntu.com/OrinocoMonitorMode?highlight=%28orinoco%29](https://wiki.ubuntu.com/OrinocoMonitorMode?highlight=%28orinoco%29) and when i have gotten to "Then run make: $make" on the .15 instructions i get a 
"Makefile:15: *** Kernel in /lib/modules/2.6.15-23-386/build is not configured. Stop." i tried doing the instructions for the .13e instead and got to step 5 and when i type "make" i get "make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/orinoco/orinoco-0.13e-SN-8 modules
make: *** /lib/modules/2.6.15-23-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2" im not sure if i am "making" wrong, but i have just typed "make" into the terminal in the dir it says, i have also tried sudoing it.

---

### Post by skynet01 on 2006-10-14
hey, i am trying to get my card working as well.. no luck but i got further then you :)  what you are missing is the kernel headers

this line should help you get further
$ apt-get install linux-source build-essential gcc-3.4 apt-get install linux-headers-<arch>

follow this guide
[https://wiki.ubuntu.com/OrinocoMonitorMode](https://wiki.ubuntu.com/OrinocoMonitorMode)

---

### Post by webcrawler42 on 2006-10-15
i do have them "Reading package lists... Done
Building dependency tree... Done
linux-headers-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

---

### Post by skynet01 on 2006-10-15
the script is trying to find your linux source in 
/lib/modules/2.6.15-23-386/bin
soo check to see if that path exists if it doesnt then copy your source there. If it does that means the path is not linked so you have to link it ...
check more guides since i dont remember how to do linking hope that helps

---

### Post by webcrawler42 on 2006-11-05
got it working under edgy eft

[http://ubuntuforums.org/showthread.php?p=1696545&posted=1#post1696545](http://ubuntuforums.org/showthread.php?p=1696545&posted=1#post1696545)

---

