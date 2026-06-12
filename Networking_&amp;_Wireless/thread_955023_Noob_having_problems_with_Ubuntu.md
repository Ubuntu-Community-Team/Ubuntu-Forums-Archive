---
title: "Noob having problems with Ubuntu"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by Omerta_X on 2008-10-21
Let me preface this again by saying I'm a total Noob when it comes to Linux; I just stared using it about a week and a half ago and am having some major problems.

Pretty much what happens is (as far as I can tell) when I open up a web page, and try to navigate it my system locks up.  What I mean by lock up is, my keyboard starts flashing at me and my cursor is unresponsive as well.  I have to do a hard reboot.  It only seems to happen when there is some sort of file transfers going on; because come to think of it, it crashed when I was trying to download some files on Frostwire as well.

I'm running a wireless network here at home.

Any suggestions or tips would be a big help.

---

### Post by pytheas22 on 2008-10-21
That's a strange problem, but very frustrating.  Please open a terminal (Applications>Accessories menu) and post the output of the following commands so that we can figure this out:
```

lshw -C Network
lspci -nn
lsusb
```

---

### Post by Omerta_X on 2008-10-22
omerta@Omerta-X:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:05:06.0
       logical name: wmaster0
       version: 00
       serial: 00:1a:70:a3:84:d6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.101 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: ULi 1689,1573 integrated ethernet.
       vendor: ALi Corporation
       physical id: 11
       bus info: pci@0000:00:11.0
       logical name: eth0
       version: 40
       serial: 00:13:8f:a6:9e:93
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=uli526x driverversion=0.9.3 latency=32 maxlatency=40 mingnt=20 module=uli526x multicast=yes
omerta@Omerta-X:~$ lspci -nn
00:00.0 Host bridge [0600]: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport] [10b9:1695]
00:01.0 PCI bridge [0604]: ALi Corporation PCI Express Root Port [10b9:524b]
00:02.0 PCI bridge [0604]: ALi Corporation PCI Express Root Port [10b9:524c]
00:03.0 PCI bridge [0604]: ALi Corporation PCI Express Root Port [10b9:524d]
00:04.0 Host bridge [0600]: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip] [10b9:1689]
00:05.0 PCI bridge [0604]: ALi Corporation AGP8X Controller [10b9:5246]
00:06.0 PCI bridge [0604]: ALi Corporation M5249 HTT to PCI Bridge [10b9:5249]
00:07.0 ISA bridge [0601]: ALi Corporation M1563 HyperTransport South Bridge [10b9:1563] (rev 70)
00:07.1 Bridge [0680]: ALi Corporation M7101 Power Management Controller [PMU] [10b9:7101]
00:08.0 Multimedia audio controller [0401]: ALi Corporation M5455 PCI AC-Link Controller Audio Device [10b9:5455] (rev 20)
00:11.0 Ethernet controller [0200]: ALi Corporation ULi 1689,1573 integrated ethernet. [10b9:5263] (rev 40)
00:12.0 IDE interface [0101]: ALi Corporation M5229 IDE [10b9:5229] (rev c7)
00:13.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:13.1 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:13.2 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:13.3 USB Controller [0c03]: ALi Corporation USB 2.0 Controller [10b9:5239] (rev 01)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 SATA controller [0106]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2360] (rev 02)
04:00.0 VGA compatible controller [0300]: nVidia Corporation NV40 [GeForce 6800 GT] [10de:0045] (rev a1)
05:06.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
omerta@Omerta-X:~$ lsusb


omerta@Omerta-X:~$ lspci -nn
00:00.0 Host bridge [0600]: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport] [10b9:1695]
00:01.0 PCI bridge [0604]: ALi Corporation PCI Express Root Port [10b9:524b]
00:02.0 PCI bridge [0604]: ALi Corporation PCI Express Root Port [10b9:524c]
00:03.0 PCI bridge [0604]: ALi Corporation PCI Express Root Port [10b9:524d]
00:04.0 Host bridge [0600]: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip] [10b9:1689]
00:05.0 PCI bridge [0604]: ALi Corporation AGP8X Controller [10b9:5246]
00:06.0 PCI bridge [0604]: ALi Corporation M5249 HTT to PCI Bridge [10b9:5249]
00:07.0 ISA bridge [0601]: ALi Corporation M1563 HyperTransport South Bridge [10b9:1563] (rev 70)
00:07.1 Bridge [0680]: ALi Corporation M7101 Power Management Controller [PMU] [10b9:7101]
00:08.0 Multimedia audio controller [0401]: ALi Corporation M5455 PCI AC-Link Controller Audio Device [10b9:5455] (rev 20)
00:11.0 Ethernet controller [0200]: ALi Corporation ULi 1689,1573 integrated ethernet. [10b9:5263] (rev 40)
00:12.0 IDE interface [0101]: ALi Corporation M5229 IDE [10b9:5229] (rev c7)
00:13.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:13.1 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:13.2 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:13.3 USB Controller [0c03]: ALi Corporation USB 2.0 Controller [10b9:5239] (rev 01)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 SATA controller [0106]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2360] (rev 02)
04:00.0 VGA compatible controller [0300]: nVidia Corporation NV40 [GeForce 6800 GT] [10de:0045] (rev a1)
05:06.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
omerta@Omerta-X:~$ 


omerta@Omerta-X:~$ lsusb
Bus 004 Device 002: ID 0402:5635 ALi Corp. USB 2.0 Flash Card Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
omerta@Omerta-X:~$ 


the onboard ethernet on my PC doesn't work at all, so I'm using a PCI wireless ethernet card.  Hope I got everything right.

---

### Post by mandrill on 2008-10-22
I believe your ethernet adaptor has to work.

---

### Post by bobpur on 2008-10-22
What are your computers specs? It sounds like you're asking too much from too little computer. :) I've had some older PII and PIII machines that used to lock up like you describe if you asked them to do too much at once. Or right after booting up and before everything loaded you tried to do something they'd lock up every time. Sometimes, they'd straighten out after a few minutes (or not) then you'd have to do a hard reboot.

My 2 cents :)

---

### Post by Omerta_X on 2008-10-22
My Specs:

Mobo:  ASRock 939 Dual
CPU:  AMD ATHLON 64 4000+ - SAN DIEGO
Mem:  KINGSTON 1GB DDR400=(512MBX2)
HD:  WESTERN DIGITAL 160GB 1600JS SATA300 8MB 7200RPM
Vid:  GeForce 6800GT AGP8X

---

### Post by pytheas22 on 2008-10-22
Omerta_X: thanks for the information.  You're using the rt61pci driver for your wireless card, and you don't seem to be the only one who experiences this problem--others report the exact same behavior (system freezes while trying to use Firefox); see this  [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194650").

The problem is supposed to have been fixed, but not recently enough to be included by default in Ubuntu 8.04.  So you have a few options for resolving the issue: 1) upgrade to Ubuntu 8.10, where the card *should* "just work"; 2) patch and recompile the driver on your 8.04 system, which should solve the problem but would take a bit of work; or 3) install an alternative driver for your card on Ubuntu 8.04 that should be more stable.

Please let me know which way you want to go, and I'll give you instructions on how to do it.  The simplest option is probably just to wipe your system and install Ubuntu 8.10, but I'm not sure what your needs are so maybe you don't want to use 8.10, or maybe you don't want to wipe your currently existing system.

---

### Post by Omerta_X on 2008-10-22
Well, I really would like to get my hands dirty and learn all about this bad boy, but I also understand you've probably got better things to do than to walk me through it.  I'd say either option 2 or 3, I'll leave it up to you.

Thanks so much for helping me out thus far!

---

### Post by pytheas22 on 2008-10-22
Please try running the following commands; they should get an alternative driver installed that should work better.  If you get error messages any point, please post them.  Also, if you can plug into ethernet before running these commands, that's best, as you will need to be online for part of them.  If ethernet isn't available, hopefully the wireless will last long enough to be able to download the file that you need (if not, there are ways around it, but they take more work)...

```
sudo apt-get install build-essential rutilt
wget http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz
tar -xzvf rt61*
cd rt61*
cd Module
make
sudo make install
sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
```

If this all runs without error messages, reboot.  After you reboot, go to System>Administration>Rutilt WLAN Manager, and try to connect (note that this driver probably won't work with Network Manager, the default connection manager with an icon in the top-right of your screen; you have to use Rutilt).  If you can't connect, please post the output of:

```
lshw -C Network
sudo iwlist scan
```

---

### Post by Omerta_X on 2008-10-22
this is what I got in my terminal.  Didn't see any errors, except for one saying that something was too big, and that I should check my kernel settings and use "strip".  Anyway, I'm about to reboot and see if everything works out.

omerta@Omerta-X:~$ sudo apt-get install build-essential rutilt
[sudo] password for omerta: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libraptor1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev patch rutilt
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 8472kB of archives.
After this operation, 34.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-21.42 [698kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libc6-dev 2.7-10ubuntu4 [2538kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7 [1217kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main g++-4.2 4.2.3-2ubuntu7 [3035kB]  
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1450B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main patch 2.5.9-4 [97.8kB]           
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1 [7070B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe rutilt 0.16-0ubuntu1 [288kB]
Fetched 8472kB in 17s (485kB/s)                                                
Selecting previously deselected package linux-libc-dev.
(Reading database ... 143356 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-21.42_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu4_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_amd64.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_amd64.deb) ...
Selecting previously deselected package rutilt.
Unpacking rutilt (from .../rutilt_0.16-0ubuntu1_amd64.deb) ...
Setting up linux-libc-dev (2.6.24-21.42) ...
Setting up libc6-dev (2.7-10ubuntu4) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up rutilt (0.16-0ubuntu1) ...

Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

Setting up build-essential (11.3ubuntu1) ...
omerta@Omerta-X:~$ wget [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)
--15:46:30--  [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)
           => `rt61-cvs-daily.tar.gz'
Resolving rt2x00.serialmonkey.com... 208.100.15.174
Connecting to rt2x00.serialmonkey.com|208.100.15.174|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 334,302 (326K) [application/x-gzip]

100%[====================================>] 334,302      273.40K/s             

15:46:31 (272.89 KB/s) - `rt61-cvs-daily.tar.gz' saved [334302/334302]

omerta@Omerta-X:~$ tar -xzvf rt61*
rt61-cvs-2008102214/
rt61-cvs-2008102214/FAQ
rt61-cvs-2008102214/THANKS
rt61-cvs-2008102214/CHANGELOG
rt61-cvs-2008102214/CVS/
rt61-cvs-2008102214/CVS/Root
rt61-cvs-2008102214/CVS/Repository
rt61-cvs-2008102214/CVS/Entries.Log
rt61-cvs-2008102214/CVS/Entries
rt61-cvs-2008102214/WPA_Supplicant/
rt61-cvs-2008102214/WPA_Supplicant/drivers.c
rt61-cvs-2008102214/WPA_Supplicant/CVS/
rt61-cvs-2008102214/WPA_Supplicant/CVS/Root
rt61-cvs-2008102214/WPA_Supplicant/CVS/Repository
rt61-cvs-2008102214/WPA_Supplicant/CVS/Entries
rt61-cvs-2008102214/WPA_Supplicant/driver_ralink.c
rt61-cvs-2008102214/WPA_Supplicant/wpa_supplicant_example.conf
rt61-cvs-2008102214/WPA_Supplicant/readme
rt61-cvs-2008102214/WPA_Supplicant/defconfig
rt61-cvs-2008102214/WPA_Supplicant/driver_ralink.h
rt61-cvs-2008102214/WPA_Supplicant/Makefile
rt61-cvs-2008102214/LICENSE
rt61-cvs-2008102214/Module/
rt61-cvs-2008102214/Module/auth.c
rt61-cvs-2008102214/Module/rt2561.bin
rt61-cvs-2008102214/Module/rt2x00debug.h
rt61-cvs-2008102214/Module/md5.c
rt61-cvs-2008102214/Module/rtmp_main.c
rt61-cvs-2008102214/Module/rt_config.h
rt61-cvs-2008102214/Module/assoc.c
rt61-cvs-2008102214/Module/CVS/
rt61-cvs-2008102214/Module/CVS/Root
rt61-cvs-2008102214/Module/CVS/Repository
rt61-cvs-2008102214/Module/CVS/Entries
rt61-cvs-2008102214/Module/STA_iwpriv_ATE_usage.txt
rt61-cvs-2008102214/Module/wpa.c
rt61-cvs-2008102214/Module/rt2561s.bin
rt61-cvs-2008102214/Module/sync.c
rt61-cvs-2008102214/Module/rtmp_data.c
rt61-cvs-2008102214/Module/rtmp_info.c
rt61-cvs-2008102214/Module/iwpriv_usage.txt
rt61-cvs-2008102214/Module/mlme.h
rt61-cvs-2008102214/Module/connect.c
rt61-cvs-2008102214/Module/rtmp_tkip.c
rt61-cvs-2008102214/Module/rt2661.bin
rt61-cvs-2008102214/Module/auth_rsp.c
rt61-cvs-2008102214/Module/oid.h
rt61-cvs-2008102214/Module/rt2661.h
rt61-cvs-2008102214/Module/rtmp_init.c
rt61-cvs-2008102214/Module/TESTING
rt61-cvs-2008102214/Module/rtmp.h
rt61-cvs-2008102214/Module/mlme.c
rt61-cvs-2008102214/Module/md5.h
rt61-cvs-2008102214/Module/wpa.h
rt61-cvs-2008102214/Module/eeprom.c
rt61-cvs-2008102214/Module/rtmp_wep.c
rt61-cvs-2008102214/Module/README
rt61-cvs-2008102214/Module/rtmp_def.h
rt61-cvs-2008102214/Module/Makefile
rt61-cvs-2008102214/Module/rtmp_type.h
rt61-cvs-2008102214/Module/rt2x00debug.c
rt61-cvs-2008102214/Module/ReleaseNote
rt61-cvs-2008102214/Module/sanity.c
omerta@Omerta-X:~$ cd rt61*
omerta@Omerta-X:~/rt61-cvs-2008102214$ cd Module
omerta@Omerta-X:~/rt61-cvs-2008102214/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/rtmp_main.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/mlme.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/connect.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/sync.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/assoc.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/auth.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/auth_rsp.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/rtmp_data.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/rtmp_init.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/sanity.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/rtmp_wep.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/wpa.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/md5.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/rtmp_tkip.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/rtmp_info.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/eeprom.o
  CC [M]  /home/omerta/rt61-cvs-2008102214/Module/rt2x00debug.o
  LD [M]  /home/omerta/rt61-cvs-2008102214/Module/rt61.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/omerta/rt61-cvs-2008102214/Module/rt61.mod.o
  LD [M]  /home/omerta/rt61-cvs-2008102214/Module/rt61.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
*** Module rt61.ko built successfully
omerta@Omerta-X:~/rt61-cvs-2008102214/Module$ sudo make install
*** Install module in /lib/modules/2.6.24-21-generic/extra ...
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  INSTALL /home/omerta/rt61-cvs-2008102214/Module/rt61.ko
  DEPMOD  2.6.24-21-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check old config ...
omerta@Omerta-X:~/rt61-cvs-2008102214/Module$ sudo -s
root@Omerta-X:~/rt61-cvs-2008102214/Module# echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
root@Omerta-X:~/rt61-cvs-2008102214/Module# echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
root@Omerta-X:~/rt61-cvs-2008102214/Module# echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
root@Omerta-X:~/rt61-cvs-2008102214/Module# echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
root@Omerta-X:~/rt61-cvs-2008102214/Module# echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
root@Omerta-X:~/rt61-cvs-2008102214/Module# echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
root@Omerta-X:~/rt61-cvs-2008102214/Module# echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
root@Omerta-X:~/rt61-cvs-2008102214/Module#

---

### Post by Omerta_X on 2008-10-22
Well, you were right, I couldnt connect with the manager, but it did connect with RutiltWLAN.  So far so good, I'll keep surfing, and try some massive downloading, ya know, really put it through the ringer.  Hopefully this fixed the problem though.  Thank you so much for your help, you're a real life saver!

---

### Post by pytheas22 on 2008-10-22
Glad to hear that it worked.  I suspect that it will remain alright now even under heavy load.

One thing to remember is that whenever you upgrade your kernel (usually happens about once a month if you apply Ubuntu updates regularly), you will need to run those steps again to get the wireless driver installed, because if the kernel changes, the driver needs to be recompiled to match.

---

### Post by Omerta_X on 2008-10-22
Sweet, yeah, I have the regular updates enabled, and I'll certainly keep that in mind!  Thanks again for all your help, life is now much less stressful now!

---

### Post by StephenG on 2008-10-24
"If ethernet isn't available, hopefully the wireless will last long enough to be able to download the file that you need (if not, there are ways around it, but they take more work)..."

Pytheas, in fact I do not have any connection on the Ubuntu machine, so your download instructions above are unworkable.  Please give me instructions on getting the files I need to try to get it running.  I've been working on it all week and am no closer than I was at the start.

The bottom line is that the system seems to recognize the card (WMP54G) and finds the router and finds the RT61PCI driver.  It just can't seem to make them all shake hands and play together nicely.  Command results are available if you want to see them.

---

### Post by pytheas22 on 2008-10-24
> Pytheas, in fact I do not have any connection on the Ubuntu machine, so your download instructions above are unworkable. Please give me instructions on getting the files I need to try to get it running. I've been working on it all week and am no closer than I was at the start.


No problem; just follow these steps and you can get the same driver installed that worked for Omerta:

1. download [this file]("http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz") and [this file]("http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/r/rutilt/rutilt_0.16-0ubuntu1_i386.deb") and save them to a USB drive or CD.  Then transfer them to your Ubuntu computer, and save them to the desktop there.

2. put your Ubuntu installation CD in the drive, then go to System>Administration>Software Sources.  Under the 'Ubuntu Software' tab, make sure that the box under the 'Installable from CD-ROM/DVD' is checked.  Then close the window; if you're asked about reloading the sources list, say yes.

3. on Ubuntu, run these commands:

```
sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xzvf rt61*
cd rt61*
cd Module
make
sudo make install
sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
```

4. on your desktop on Ubuntu, you should have an icon with a name that looks like 'rutilt_0.16...deb'.  Double-click the icon and an installer should open; use it to install the package.

If all this works, reboot, and you should be able to connect by going to System>Administration>Rutilt WLAN Manager (you have to use this program; you can't use Network Manager to connect).

If you get error messages at any point, please copy them and post them here.  It would also be useful, if things don't work, to see the output of:

```
lspci -nn
lshw -C Network
sudo iwlist scan
```

---

### Post by StephenG on 2008-10-24
Will I need to uninstall or deactivate Network Manager?  I've seen several references involving that action during my seemingly endless hours of research on these forums.

---

### Post by pytheas22 on 2008-10-24
No, don't worry about uninstalling Network Manager.  It won't work if you try to connect with it using this new driver, but it won't interfere with anything.  The references you saw to uninstalling NM probably involved wicd, another connection manager, which does require NM to be uninstalled in order to work.  But wicd won't help in your case, so don't worry about this.

---

### Post by StephenG on 2008-10-24
Whoa, midstrem error message:

Module file way too big.  Check kernel settings or use 'strip'.
Module rt61.ko built successfully.

Am I still heading in the right direction?  What to do about the 'strip' suggestion?  I hate working on the computer in the buff ... it seems so, well, unseemly.

***update: I located the 'strip' command info and everything's back on track.  Disregard the panic, please.

Except for the "Module too big" error, everything went swimmingly.  Except ... I still have no connection.

(Since I don't know how one gets those fancy insert boxes, I'll just paste it here)  The results of the requested output:

Me@My-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT82C598 [Apollo MVP3] [1106:0598] (rev 04)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP] [1106:8598]
00:07.0 ISA bridge [0601]: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] [1106:0586] (rev 41)
00:07.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:07.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 02)
00:07.3 Non-VGA unclassified device [0000]: VIA Technologies, Inc. VT82C586B ACPI [1106:3040] (rev 10)
00:08.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
01:00.0 VGA compatible controller [0300]: Trident Microsystems 3DImage 9750 [1023:9750] (rev f3)


Me@My-desktop:~$ sudo lshw -C network 
  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: wlan0
       version: 00
       serial: 00:1d:7e:95:11:36
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61 latency=64 module=rt61 multicast=yes wireless=RT61 Wireless


Me@My-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:2B:FA:37
                    ESSID:"linksys"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Bit Rates:0 kb/s
                    Quality:0/100  Signal level:-70 dBm  Noise level:0 dBm
          Cell 02 - Address: 00:18:F8:66:A3:58
                    ESSID:"[My Correct Router Name]"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Bit Rates:0 kb/s
                    Quality:0/100  Signal level:-76 dBm  Noise level:0 dBm
          Cell 03 - Address: 00:E0:98:FA:D5:7D
                    ESSID:"05B403723058"
                    Mode:Managed
                    Channel:6
                    Encryption key:off
                    Bit Rates:0 kb/s
                    Quality:0/100  Signal level:-62 dBm  Noise level:0 dBm


Except for the fact that the card is now using the RutilT instead of the Netowrk Manager, all the returns seem to ba the same or very similar to those I had prior to this install.

Since I had two separate old boxes that I wanted to put together for my kids to use as their school computers and not hog mine, I bought two of these wireless cards.  Having just spent the entire last week trying to figure this out (see above posts, Pytheas) I decided, for no reason at all, to simply swap out the cards.  Voila.  The damn thing works like a champ.

Thank you so much for your help and very explicit, simple-to-use guide.  I'll be using it on the second box when I get to putting it back together.  I had no idea that a brand new card would have (obviously) a broken transmit section.  Hence, the positive results to the command line tests.  After RutilT was installed, it indicated that the card was receiving packets all the time but not transmitting any.  Aha, says I.

You should have this guide posted permanently for all with an RT61 driver.  It is the simplest one i've found -- and I might have found them all by now.  Thanks again.

Pytheas, do you have any solution for getting the network to stick around following power-down or reboot?  Every time, I have to enter the RutilT control panel and re-enter the WEP key and set up a new profile.  I can do it easily enough (though it is an exasperation), but I built this box for my 10-year-olds to do their school work and they are too young to do it every time.

---

### Post by pytheas22 on 2008-10-25
Sorry for not responding sooner; yesterday was a busy day.  I'm glad to hear that you got a working card, however.

If you want to make Rutilt connect automatically, first, make a profile and save it (if you can't figure out how to save one, let me know and I'll post screenshots of where to click).  Then go to System>Preferences>Sessions and under the 'Startup Programs' tab, add a new one.  In the 'command' field, enter a command like this:
```

gksudo rutilt --hide --profile PROFILE_NAME --dhcp
```

Obviously, replace 'PROFILE_NAME' with the name of the profile that you create.

This should work, and you should get automatically connected each time you log into Gnome.  The only catch is that a box will pop up each time asking you for your password (because Rutilt needs to be run as root).  If your kids can't enter the password, there may be some tricks that you can use to get around that, so let me know if it's a problem.

If that command doesn't seem to work for you, let me know; it may take some experimenting to get it going.

---

### Post by StephenG on 2008-10-25
By password, do you mean the encryption key or the regular log-on password for the desktop?

That didn't work.  I did find that if I went to the RutilT options page, the Interface was marked as "Down" and by pushing that radio button it activated the interface and brought up the connection.  However, it wasn't connecting to my router.  It connected to someone's unsecure router in the area, and RutilT hadn't retained my profile.  It did find my router, but not as the preferred profile.

I also added lines to the /etc/network/interfaces file:

auto wlan1
iface wlan1 inet dhcp

but that doesn't seem to make any difference after reboot.

And I didn't get any pop-up asking for a password.

---

### Post by pytheas22 on 2008-10-25
Is your network only encrypted with WEP?  If so, please post the output of:
```

sudo iwlist scan
```

and tell me the name of the network you're trying to connect to.  If it's only WEP, there may be an easier way to do this.

---

### Post by StephenG on 2008-10-25
lo        Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:18:F8:66:A3:58
                    ESSID:"Nichols"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Bit Rates:0 kb/s
                    Quality:27/100  Signal level:-60 dBm  Noise level:0 dBm
          Cell 02 - Address: 00:13:10:2B:FA:37
                    ESSID:"linksys"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Bit Rates:0 kb/s
                    Quality:0/100  Signal level:-72 dBm  Noise level:0 dBm
          Cell 03 - Address: 00:1C:10:32:69:B6
                    ESSID:"tenderloin"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s
                    Quality:0/100  Signal level:-82 dBm  Noise level:0 dBm

My router is "Nichols" and due to another computer using the router, which only has WEP ability, I'm limited to that encryption.

---

### Post by pytheas22 on 2008-10-25
Thanks for the information.  Please reboot your computer, then open up a terminal and run these commands:
```

sudo iwconfig wlan1 mode managed channel 6 essid "Nichols" key YOURWEPKEY
sudo dhclient wlan1
```

(enter your WEP key without colons, and don't put it in quotes or anything)

That should get you connected, provided that you use a normal WEP key (i.e. not an ASCII key; if you use an ASCII key the command needs to be a little different).  If it doesn't work the first time, try it a couple more times.

If you can connect this way, then we can write a boot script to connect you automatically each time the machine is turned on, without having to worry about passwords or anything else.  This would be simpler than trying to deal with Rutilt, although we can go back to Rutilt if the manual connection doesn't work.

FYI: for a longer discussion of negotiating a WEP connection using the command line, see [this thread]("http://ubuntuforums.org/showthread.php?t=571188").

---

### Post by StephenG on 2008-10-26
Thanks for the link but I'd already been through that one (and about a dozen others) several times and gotten some suggestions from Kevdog, that didn't work at the time (the faulty card issues, of course).  I'm going to see what happens with the RutilT for a few days ro so before I dive back in again.

---

