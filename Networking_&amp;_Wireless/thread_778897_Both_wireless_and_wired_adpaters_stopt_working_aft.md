---
title: "Both wireless and wired adpaters stopt working after upgrade to hardy"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by skipx on 2008-05-02
Since both my adapaters (!!!) are not recognizes anymore after upgrade 7.10-8.0.4 it's a bit difficult to put output.

My ethernet adapter is realtek rtl8111. Try to follow instructions as: [http://ubuntuforums.org/showthread.php?t=723569](http://ubuntuforums.org/showthread.php?t=723569) but i cannot even build the realtek driver (r8168-8.006.00.tar.bz2). 

$ lspci |grep Ethernet
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

abortx@abortx:/usr/src/r8168-8.006.00$ sudo make clean
make -C src/ clean
make[1]: Entering directory `/usr/src/r8168-8.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/usr/src/r8168-8.006.00/src'
abortx@abortx:/usr/src/r8168-8.006.00$ sudo make install
make -C src/ install
make[1]: Entering directory `/usr/src/r8168-8.006.00/src'
install -m 744 -c r8168.ko /lib/modules/2.6.24-16-generic/kernel/drivers/net/
install: cannot stat `r8168.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/usr/src/r8168-8.006.00/src'
make: *** [install] Error 2

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:49:c5:6a  
          inet6 addr: fe80::218:f3ff:fe49:c56a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:672 errors:0 dropped:0 overruns:0 frame:0
          TX packets:672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24948 (24.3 KB)  TX bytes:24948 (24.3 KB)

For my wireless adapter (normally eth1): when i install b43-fwcutter I end up with the error that the installer cannot find the server where it wants to download 'wl_apsta-3.130.20.0.o'. I downloaded this file somewhere else, but cannot make the system understand i have it (where does the installer look, only online, or does it also check if it downloaded it earliar, and where??)

I also the tips (including commenting in blacklist) tried [http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/) which did not work for me either.

$ lspci |grep Broadcom
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

If i had just one of them working.. 

Thanks,
Bart

---

### Post by superprash2003 on 2008-05-02
hope this helps [http://prash-babu.blogspot.com/2008/05/how-to-configure-broadcom-wireless-in.html](http://prash-babu.blogspot.com/2008/05/how-to-configure-broadcom-wireless-in.html)

---

### Post by skipx on 2008-05-02
I have no internet at all on this machine, so i cannot really do dpkg, wget, apt-get or running deb files..

---

### Post by Ayuthia on 2008-05-02
> **skipx said:**
> For my wireless adapter (normally eth1): when i install b43-fwcutter I end up with the error that the installer cannot find the server where it wants to download 'wl_apsta-3.130.20.0.o'. I downloaded this file somewhere else, but cannot make the system understand i have it (where does the installer look, only online, or does it also check if it downloaded it earliar, and where??)

If you installed b43-fwcutter from the Ubuntu repositories or live CD, there is a script /usr/share/b43-fwuctter/install_bcm43xx_firmware.sh. 
```
#!/bin/sh

set -e

dir=$(mktemp -d)
cd "$dir"
wget http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
rm -rf "$dir"
chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy

```Make sure that you have both files listed under the wget.  Go to the directory where you downloaded the wl_apsta-3.130.20.0.o and do the following:```
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
```
Then go to the directory where you downloaded broadcom-wl-4.80.53.0.tar.bz2 and do the following:```
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
```That should complete your install.

---

### Post by skipx on 2008-05-02
Thanks a lot! That did it for wireless.. :D

If someone knows how to fix the wired part? 
(the audio part i'll try to solute later.. ;) )

---

### Post by MaindotC on 2008-05-02
> **skipx said:**
> I have no internet at all on this machine, so i cannot really do dpkg, wget, apt-get or running deb files..

If you had no "internet" at all, how did you post???

---

### Post by skipx on 2008-05-02
hehe, almost right. I had no internet on my asus laptop, on my old apple laptop i could still dowload/read (and post) things.

---

### Post by Ayuthia on 2008-05-02
> abortx@abortx:/usr/src/r8168-8.006.00$ sudo make clean
make -C src/ clean
make[1]: Entering directory `/usr/src/r8168-8.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/usr/src/r8168-8.006.00/src'
abortx@abortx:/usr/src/r8168-8.006.00$ sudo make install
make -C src/ install
make[1]: Entering directory `/usr/src/r8168-8.006.00/src'
install -m 744 -c r8168.ko /lib/modules/2.6.24-16-generic/kernel/drivers/net/
install: cannot stat `r8168.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/usr/src/r8168-8.006.00/src'
make: *** [install] Error 2
I think that you might have missed a step here.  You might try doing a make before the sudo make install.

---

### Post by skipx on 2008-05-02
I seem to get the same kind of problem when I also give a make:

abortx@abortx:/root/r8168-8.006.00$ **sudo make clean modules**
make -C src/ clean
make[1]: Entering directory `/root/r8168-8.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/root/r8168-8.006.00/src'
make -C src/ modules
make[1]: Entering directory `/root/r8168-8.006.00/src'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/root/r8168-8.006.00/src'
make: *** [modules] Error 2
abortx@abortx:/root/r8168-8.006.00$ **sudo make**
make -C src/ clean
make[1]: Entering directory `/root/r8168-8.006.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/root/r8168-8.006.00/src'
make -C src/ modules
make[1]: Entering directory `/root/r8168-8.006.00/src'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/root/r8168-8.006.00/src'
make: *** [modules] Error 2
abortx@abortx:/root/r8168-8.006.00$ **sudo make install**
make -C src/ install
make[1]: Entering directory `/root/r8168-8.006.00/src'
install -m 744 -c r8168.ko /lib/modules/2.6.24-16-generic/kernel/drivers/net/
install: cannot stat `r8168.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/root/r8168-8.006.00/src'
make: *** [install] Error 2
abortx@abortx:/root/r8168-8.006.00$

---

### Post by Ayuthia on 2008-05-02
Oops!
> make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-genericDo you have linux-headers-2.6.24-16-generic installed?

Do you also have build-essential installed?  That might be needed also.

---

### Post by skipx on 2008-05-02
Yes, i think it comes automatic with ubuntu 8.0.4 (?)

abortx@abortx:~$ uname -r
2.6.24-16-generic

EDIT:
It didn't help to install build-essential

---

### Post by Ayuthia on 2008-05-02
> **skipx said:**
> Yes, i think it comes automatic with ubuntu 8.0.4 (?)

abortx@abortx:~$ uname -r
2.6.24-16-generic

EDIT:
It didn't help to install build-essential
If you do:
```
aptitude search linux-headers
```you should see something like:
```
i A linux-headers-2.6.24-16-generic                                       - Linux kernel headers for version 2.6.24 on x86/x86_64
```
If there is an i at the beginning, it is installed.  If it is a v or p, it has not been installed.  The uname -r tells you your kernel version.  The linux-headers are the kernel files used for compiling kernel-related sources.

---

### Post by skipx on 2008-05-02
Ok, thnks.

I seem to have two versions of the headers installed.
i A linux-headers-2.6.24-16         - Header files related to Linux kernel versi
i A linux-headers-2.6.24-16-generic - Linux kernel headers for version 2.6.24 on




below full output


v   linux-headers                   -                                           
v   linux-headers-2.6               -                                           
i A linux-headers-2.6.24-16         - Header files related to Linux kernel versi
p   linux-headers-2.6.24-16-386     - Linux kernel headers for version 2.6.24 on
i A linux-headers-2.6.24-16-generic - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-16-openvz  - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-16-rt      - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-16-server  - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-16-virtual - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-16-xen     - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-17         - Header files related to Linux kernel versi
p   linux-headers-2.6.24-17-386     - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-17-generic - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-17-openvz  - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-17-rt      - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-17-server  - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-17-virtual - Linux kernel headers for version 2.6.24 on
p   linux-headers-2.6.24-17-xen     - Linux kernel headers for version 2.6.24 on
p   linux-headers-386               - Linux kernel headers on 386               
p   linux-headers-686               - Upgrade dummy package. Can be removed     
i   linux-headers-generic           - Generic Linux kernel headers              
p   linux-headers-k7                - Upgrade dummy package. Can be removed     
v   linux-headers-lbm               -                                           
v   linux-headers-lbm-2.6           -                                           
p   linux-headers-lbm-2.6.24-16-386 - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-16-gen - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-16-ope - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-16-rt  - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-16-ser - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-16-vir - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-16-xen - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-17-386 - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-17-gen - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-17-ope - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-17-rt  - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-17-ser - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-17-vir - Header files related to linux-backports-mo
p   linux-headers-lbm-2.6.24-17-xen - Header files related to linux-backports-mo
v   linux-headers-lum               -                                           
v   linux-headers-lum-2.6           -                                           
p   linux-headers-lum-2.6.24-16-386 - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-16-gen - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-16-ope - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-16-rt  - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-16-ser - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-16-vir - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-16-xen - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-17-386 - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-17-gen - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-17-ope - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-17-rt  - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-17-ser - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-17-vir - Header files related to linux-ubuntu-modul
p   linux-headers-lum-2.6.24-17-xen - Header files related to linux-ubuntu-modul
p   linux-headers-openvz            - rt Linux kernel headers                   
p   linux-headers-rt                - rt Linux kernel headers                   
p   linux-headers-server            - Linux kernel headers on Server Equipment. 
p   linux-headers-virtual           - Linux kernel headers for the virtual flavo
p   linux-headers-xen               - Xen Linux kernel headers

---

### Post by Ayuthia on 2008-05-02
Teach me for not believing you!!! :)
> scripts/Makefile.build:41: /src/Makefile: No such file or directoryI should try to read more carefully.  This is where the problem is located.  For some reason, it cannot find the /src/Makefile.  Is there a configure file in the directory that you are compiling?  You might need to ./configure before you do the make.  This is just a guess.  I can't figure out where /src/Makefile is supposed to come from.

---

### Post by skipx on 2008-05-02
This is de listing of the package i downloaded from realtek:
root@abortx:/root/r8168-8.006.00# ls
Makefile  readme  release_note.txt  src
root@abortx:/root/r8168-8.006.00# ls src/
Makefile  Makefile_linux24x  r8168.h  r8168_n.c  rtl_ioctl.c  rtl_ioctl.h

---

### Post by Ayuthia on 2008-05-02
Ok.  I am stumped.  I have downloaded the file and tried to compile it on my end.  I have fiddled with the Makefile so that it can find the src directory and it comes with other compile errors.  Sorry.  I am going to play around with it for a while.  If I come up with anything, I will reply back.

Another thing, you might want to create another post with a title that contains something like "need help with compiling Realtek driver".

---

### Post by Ayuthia on 2008-05-02
I did some digging and found this link:
[http://ubuntuforums.org/showthread.php?t=755002](http://ubuntuforums.org/showthread.php?t=755002)
One of the posters included a patch that helped the code compile.  You will need to get r8168-8.005.00 instead of 006.00.  I have not tried out his changes though.  Unfortunately even if it compiles for me, I will not be able to test it out because I do not have the hardware.

---

