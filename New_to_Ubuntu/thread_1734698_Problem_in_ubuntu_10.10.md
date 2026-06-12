---
title: "Problem in ubuntu 10.10"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by sandy0594 on 2011-04-20
Hi all,i am very new to Linux operating system.I installed ubuntu 10.10 through **wubi**..Whenever ubuntu updates it's packages,in the ubuntu start-up..I am getting several choices,i mean the choices are increasing whenever a major update is happening and today when it updated the packages it asked for reboot,I did so.So,the choices increased and moreover when I logged in,it couldn't establish my n/w connection..I had to install the necessary things for the network connections to function..

Can anyone explain me the cause of the problem?

Below is what happened today:

```

sandy@ubuntu:~$ sudo lshw -C network
[sudo] password for sandy: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:febc0000-febfffff ioport:ec00(size=128)
sandy@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:724 errors:0 dropped:0 overruns:0 frame:0
          TX packets:724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56504 (56.5 KB)  TX bytes:56504 (56.5 KB)

sandy@ubuntu:~$ cd ~/Desktop/AR
sandy@ubuntu:~/Desktop/AR$ tar xvvf AR81Family-linux-v1.0.1.14.tar.gz
drwxrwxrwx root/root         0 2010-09-14 13:04 ./
-r-xr-Sr-x root/root      4402 2010-07-22 08:10 ./atl1e.7
-rwxrwSrwx root/root     11502 2010-06-25 14:24 ./atl1e.spec
-rwxrwSrwx root/root      2648 2010-06-25 14:24 ./at_osdep.h
-rwxrwSrwx root/root     18671 2010-06-25 14:24 ./copying
-rwxrwSrwx root/root       198 2010-06-25 14:24 ./dkms.conf
-rwxrwSrwx root/root      4596 2010-06-25 14:24 ./ldistrib.txt
-r-xr-Sr-x root/root       977 2010-08-06 14:18 ./Makefile
-rwxrwSrwx root/root       673 2010-06-25 14:24 ./pci.updates
-rwxrwSrwx root/root      7525 2010-06-25 14:24 ./readme
-r-xr-Sr-x root/root      1729 2010-09-14 12:58 ./release_note.txt
drwxrwxrwx root/root         0 2010-09-14 12:51 ./src/
-rwxrwSrwx root/root     20480 2010-08-19 17:06 ./src/.atl1c_main.c.swo
-r-xr-Sr-x root/root     22306 2010-07-21 12:02 ./src/atl1c.h
-r-xr-Sr-x root/root     10893 2010-06-25 10:12 ./src/atl1c_ethtool.c
-r-xr-Sr-x root/root     19417 2010-06-25 10:12 ./src/atl1c_hw.c
-r-xr-Sr-x root/root     33678 2010-08-06 14:18 ./src/atl1c_hw.h
-rwxrwSrwx root/root     91461 2010-09-14 12:51 ./src/atl1c_main.c
-r-xr-Sr-x root/root      7041 2010-06-25 10:12 ./src/atl1c_param.c
-r-xr-Sr-x root/root      4826 2010-06-25 10:12 ./src/atl1e.h
-r-xr-Sr-x root/root     15949 2010-06-25 10:12 ./src/atl1e_ethtool.c
-r-xr-Sr-x root/root     24225 2010-06-25 10:12 ./src/atl1e_hw.c
-r-xr-Sr-x root/root     52924 2010-06-25 10:12 ./src/atl1e_hw.h
-r-xr-Sr-x root/root    101017 2010-06-25 10:12 ./src/atl1e_main.c
-r-xr-Sr-x root/root      7981 2010-06-25 10:12 ./src/atl1e_param.c
-r-xr-Sr-x root/root      4075 2010-06-25 10:12 ./src/at_common.h
-rwxrwSrwx root/root      7092 2010-09-14 12:50 ./src/at_common_main.c
-r-xr-Sr-x root/root      2732 2010-06-25 10:12 ./src/at_osdep.h
-r-xr-Sr-x root/root      5997 2010-06-25 10:12 ./src/kcompat.c
-rwxrwSrwx root/root     50085 2010-09-14 12:46 ./src/kcompat.h
-r-xr-Sr-x root/root     30563 2010-06-25 10:12 ./src/kcompat_ethtool.c

gzip: stdin: decompression OK, trailing garbage ignored
-r-xr-Sr-x root/root     10858 2010-06-25 10:12 ./src/Makefile
-rwxrwSrwx root/root         0 2010-08-06 11:35 ./src/Module.markers
-r-xr-Sr-x root/root         0 2010-06-25 10:12 ./src/Module.symvers
-rwxrwSrwx root/root        63 2010-09-14 08:08 ./src/modules.order
tar: Child returned status 2
tar: Error is not recoverable: exiting now
sandy@ubuntu:~/Desktop/AR$ cd src
sandy@ubuntu:~/Desktop/AR/src$ patch -p1 < ~/Desktop/AR81Family-linux-v1-1.0.1.14.patch
patching file atl1c_main.c
patching file atl1e_main.c
patching file Makefile
sandy@ubuntu:~/Desktop/AR/src$ cd ~/Desktop/AR
sandy@ubuntu:~/Desktop/AR$ sudo make install
make -C ./src/ install
make[1]: Entering directory `/home/sandy/Desktop/AR/src'
make -C /lib/modules/2.6.35-29-generic/build SUBDIRS=/home/sandy/Desktop/AR/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-29-generic'
  CC [M]  /home/sandy/Desktop/AR/src/at_common_main.o
  CC [M]  /home/sandy/Desktop/AR/src/atl1e_main.o
  CC [M]  /home/sandy/Desktop/AR/src/atl1c_main.o
  CC [M]  /home/sandy/Desktop/AR/src/atl1c_hw.o
  CC [M]  /home/sandy/Desktop/AR/src/atl1e_hw.o
  CC [M]  /home/sandy/Desktop/AR/src/atl1e_param.o
  CC [M]  /home/sandy/Desktop/AR/src/atl1c_param.o
  CC [M]  /home/sandy/Desktop/AR/src/atl1e_ethtool.o
  CC [M]  /home/sandy/Desktop/AR/src/atl1c_ethtool.o
  CC [M]  /home/sandy/Desktop/AR/src/kcompat.o
  LD [M]  /home/sandy/Desktop/AR/src/atl1e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/sandy/Desktop/AR/src/atl1e.mod.o
  LD [M]  /home/sandy/Desktop/AR/src/atl1e.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-29-generic'
gzip -c ../atl1e.7 > atl1e.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.35-29-generic -name atl1e.ko -exec rm -f {} \; || true
find /lib/modules/2.6.35-29-generic -name atl1e.ko.gz -exec rm -f {} \; || true
install -D -m 644 atl1e.ko /lib/modules/2.6.35-29-generic/kernel/drivers/net/atl1e/atl1e.ko
/sbin/depmod -a || true
install -D -m 644 atl1e.7.gz /usr/share/man/man7/atl1e.7.gz
man -c -P'cat > /dev/null' atl1e || true
atl1e.
make[1]: Leaving directory `/home/sandy/Desktop/AR/src'
sandy@ubuntu:~/Desktop/AR$ sudo modprobe atl1e
sandy@ubuntu:~/Desktop/AR$ sudo dpkg -s patch
Package: patch
Status: install ok installed
Priority: standard
Section: vcs
Installed-Size: 248
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 2.6-2ubuntu1
Depends: libc6 (>= 2.4)
Suggests: ed, diffutils-doc
Description: Apply a diff file to an original
 Patch will take a patch file containing any of the four forms
 of difference listing produced by the diff program and apply
 those differences to an original file, producing a patched
 version.
Original-Maintainer: Christoph Berg <myon@debian.org>
sandy@ubuntu:~/Desktop/AR$ cd
sandy@ubuntu:~$ sudo lshw -C network
[sudo] password for sandy: 
  *-network               
       description: Ethernet interface
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: bc:ae:c5:50:83:1f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1C driverversion=1.0.1.14 duplex=full firmware=L1e latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:febc0000-febfffff ioport:ec00(size=128)


```

---

### Post by Foxheadz on 2011-04-20
If all the options just have a different string of numbers after them then follow [this]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/") guide.

---

### Post by sandy0594 on 2011-04-20
Yeah,the kernels are increasing every time I am updating..
thanks for the reply..
I thought no one would reply with my not so good English language
Can i know why is that every time when the Linux headers get updated,the n/w connection gets undetected..Is there any solution so as to make the n/w connections making detected even after these updates

---

### Post by 3rdalbum on 2011-04-20
Drivers are linked to the version of the kernel that they were compiled for. If you update the kernel, the driver might not understand the new kernel. If this happens, you need to reinstall the driver so it can link to the new kernel.

If the driver came with Ubuntu, or in the Additional Drivers program, it should automatically rebuild itself when a new kernel is installed. For any other drivers, they need to be rebuilt manually, like you just did.

---

### Post by sandy0594 on 2011-04-21
Oh! So,u mean to say that every time the Linux headers get updated I need to install my n/w driver....
Does ubuntu doesn't have any alternate thing for this?

---

