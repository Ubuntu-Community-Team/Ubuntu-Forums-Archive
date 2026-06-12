---
title: "Early Wireless problem, hardware not present"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by Eberulf on 2007-12-20
I have searched the forums but have not found an answer to this problem.  I have loaded the driver for the Airlink wl4130 on a desktop, but get the following:

jane@jane:~$ ndiswrapper -l
netwl4130 : driver installed

It is not showing the hardware as present.  It is present.  When I run lspci, I get the following.

01:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

By the way, this card is supposed to work out the box with the restricted drivers that come with Ubuntu, but it did not so I disabled them and loaded the driver with ndiswrapper.

Any suggestions?  I have spent probably 5 hours on this already and reloaded once from scratch, to no avail,

---

### Post by madking on 2007-12-20
ok, you need to install the firmware. Ndiswrapper will not do this for you. Also i believe that option you disabled is the firmware. try re-enabling it. it migt work after that.
I had this issue with my broadcom, so i know how frustrating this can be.

---

### Post by rustybronco on 2007-12-20
[http://ubuntuforums.org/showpost.php?p=3781765&postcount=3](http://ubuntuforums.org/showpost.php?p=3781765&postcount=3)

[http://madwifi.org/](http://madwifi.org/) and compile from source was his answer to the problem.
or see kevdogs finest in my signature on how to connect/trouble shoot from the command line.

***edit***
or I would try to enable the restricted drivers for the card (again)  and use wicd (add/remove, synaptic, apt-get ect.).
or one could try to install just wicd.

but before you do...

please post the output of lspci 
and    lshw -C network    (commands entered in the terminal, cut-n-paste)

***additional info*** it won't hurt to give this thread a spin, you don't even have to mess with your install  [http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

### Post by Eberulf on 2007-12-22
OK, but a bit of an update first.  I noticed the desktop was running slower and had random problems on bootup.  I figured out it is an Intel Pentium 4 and therefore should get the 64bit version (it is my girlfriend's computer).  I reloaded it with the 686 version and have the same problem, although I have not loaded ndiswrapper and the 4130 driver.  The HAL restricted driver is enabled and I do not see wireless networks.

Commands and output:
jane@jane-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=12 mingnt=10
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:13:8f:ee:11:b6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.2 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes

jane@jane-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Eberulf on 2008-01-09
I couldn't install madwifi.  It gives me the following error very early in the process.

jane@jane-desktop:~/madwifi-0.9.3.3$ ifconfig ath0 down
ath0: ERROR while getting interface flags: No such device
jane@jane-desktop:~/madwifi-0.9.3.3$ ifconfig wifi0 down
wifi0: ERROR while getting interface flags: No such device
jane@jane-desktop:~/madwifi-0.9.3.3/scripts$ sudo ./madwifi-unload.bash
FATAL: Module wlan is in use.

I have to say, this is very, very frustrating.  Nothing seems to work on this PC like it does for most people I read on these forums.

---

### Post by Eberulf on 2008-01-09
Also, I am pretty sure that installing Madwifi is just going to be a time-wasting effort.  I read that the restricted driver that is currently installed, enabled and impotent on my computer is just Madwifi anyway that gets installed in Ubuntu by default.

Here is a piece of advice for someone relatively new to Ubunutu.  Do not attempt to troubleshoot close to bedtime.  You get ticked off, the adrenaline starts pumping and then you have trouble sleeping.

---

### Post by Junglizer on 2008-01-10
> **Eberulf said:**
> Also, I am pretty sure that installing Madwifi is just going to be a time-wasting effort.  I read that the restricted driver that is currently installed, enabled and impotent on my computer is just Madwifi anyway that gets installed in Ubuntu by default.

Here is a piece of advice for someone relatively new to Ubunutu.  Do not attempt to troubleshoot close to bedtime.  You get ticked off, the adrenaline starts pumping and then you have trouble sleeping.

Did you compile from source, or use the restricted drivers? It can make a large difference. I do not know if they're are non-restricted drivers located within the package manager.

---

### Post by Junglizer on 2008-01-10
Also, you've got the AR5212 chipset, which works flawlessly with the Madwifi drivers, it may be the restricted drivers that are giving you the trouble.

---

### Post by Eberulf on 2008-01-10
I tried compiling from source and had a ton of errors.  I don't see a "how-to' on the madwifi site on how to compile from source.  I tried to follow a post which I cannot find now, but it was on this forum and worked on someone else's computer.  

Is there a different madwifi for a 64 bit computer?

---

### Post by Eberulf on 2008-01-17
OK, here is the output of the errors.  Any ideas??

----------------------------------
jane@jane-desktop:~/madwifi-0.9.3.3$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/jane/madwifi-0.9.3.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  HOSTCC  /home/jane/madwifi-0.9.3.3/ath_hal/uudecode
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c: At top level:
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c: In function 'main':
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/jane/madwifi-0.9.3.3/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/jane/madwifi-0.9.3.3/ath_hal/uudecode] Error 1
make[2]: *** [/home/jane/madwifi-0.9.3.3/ath_hal] Error 2
make[1]: *** [_module_/home/jane/madwifi-0.9.3.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

---

### Post by wiijii on 2008-01-18
I just had this problem. 

Although I haven't managed to get my wireless card working (it's a slightly different one to yours) I think I know how you can solve the compilation problem for madwifi. 

Just install 'build-essential' package. 

And make sure you also have your kernel-header-[kernel version] package installed. 

Thom

---

### Post by Eberulf on 2008-01-18
Where would I get the "build-essential" package?  I looked under the "Add/Remove" option under Applications, and I do not see that option.

---

### Post by rustybronco on 2008-01-19
open a terminal, then...   sudo aptitude install build-essential

---

### Post by Eberulf on 2008-01-20
I get the following message:

 Media Change: Please insert the disc labeled 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)' in the drive '/cdrom/' and press [Enter].

Is this the install disk?  I have it in the cd rom drive, although it is just one file ubuntu-7.10-desktop-amd64.iso.  Or is it looking for something else?  I press enter and the error message repeats itself.  I will look up this error.

---

### Post by kevdog on 2008-01-20
Ok do the following

Edit your /etc/apt/sources.list

gksu gedit /etc/apt/sources.list

Remove the line referring to your cd rom (there might be 2 lines)

Then save the file and exit

Then, stick in your disk into the cd rom and type
sudo apt-cdrom add
sudo aptitude update

Then 
sudo aptitude install build-essential

---

### Post by Eberulf on 2008-01-21
I think something didn't work correctly.  It appears it could not find package files.

----------------------------------

jane@jane-desktop:/etc/apt$ gksu gedit /etc/apt/sources.list
jane@jane-desktop:/etc/apt$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [546d181720b57c229bff2f670e466c7d-2]
Scanning disc for index files..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
E: Unable to locate any package files, perhaps this is not a Debian Disc
jane@jane-desktop:/etc/apt$ sudo aptitude update
Reading package lists... Done
jane@jane-desktop:/etc/apt$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "build-essential"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
jane@jane-desktop:/etc/apt$

---

