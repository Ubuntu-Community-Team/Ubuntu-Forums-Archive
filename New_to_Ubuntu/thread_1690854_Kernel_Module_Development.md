---
title: "Kernel Module Development"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by pravin2710 on 2011-02-19
Hi,

I worked on building kernel modules in Fedora13 with kernel version 2.6.25.3 sometime back. Now, I'm trying to do the same in Ubuntu.. Strangely, I've got the following error and I'm stuck searching for solution... Kindly help me..

[fedora13@localhost glcd]$ make
make ARCH=arm CROSS_COMPILE=arm-linux-uclibc -I /home/fedora13/Propox/OpenWrt-SDK-at91-for-Linux-i686/staging_dir/toolchain-arm_gcc4.1.2/include/ M=/home/fedora13/SampleDriverCode/glcd modules                                                                                          
make[1]: Entering directory `/home/fedora13/SampleDriverCode/glcd'                            
make[1]: *** No rule to make target `modules'.  Stop.                                         
make[1]: Leaving directory `/home/fedora13/SampleDriverCode/glcd'                             
make: *** [all] Error 2


My linux source code is at /home/fedora13/SampleDriverCode/glcd where fedora13is my user. and my ubutu development header file are at /home/fedora13/Propox/OpenWrt-SDK-at91-for-Linux-i686/staging_dir/toolchain-arm_gcc4.1.2/include/

another thing is I am compiling this code for ubuntu target hardware on fedora system. Is that any issue regarding this?


Thanks in Advance. :) :) :)

---

