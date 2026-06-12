---
title: "wireless not regognized"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by Taoman420 on 2008-04-11
I recently installed Ubuntu on my macbook, and it refuses to recognize the internet in any way, but right now I care about the wireless. When I click on the network manager icon, it only gives me the 'wired connection' option. I have a linksys connection, that I know is working. 

Im also new to linux, btw.

---

### Post by Taoman420 on 2008-04-12
I tried downloading NDISwrapper, and the intructions were to type these commands
make distclean
make
make install

This is what I got on the last command

taoman@taoman-laptop:~/Desktop/ndiswrapper$ sudo make install
make -C driver install
make[1]: Entering directory `/home/taoman/Desktop/ndiswrapper/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/taoman/Desktop/ndiswrapper/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
echo /lib/modules/2.6.22-14-generic/misc
/lib/modules/2.6.22-14-generic/misc
mkdir -p /lib/modules/2.6.22-14-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.22-14-generic/misc
/sbin/depmod -a 2.6.22-14-generic -b /
make[1]: Leaving directory `/home/taoman/Desktop/ndiswrapper/driver'
make -C utils install
make[1]: Entering directory `/home/taoman/Desktop/ndiswrapper/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/x86_64-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.1.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/x86_64-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
loadndisdriver.c: In function &#8216;load_file&#8217;:
loadndisdriver.c:67: error: &#8216;size_t&#8217; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected &#8216;;&#8217; before &#8216;size&#8217;
loadndisdriver.c:68: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:71: warning: implicit declaration of function &#8216;basename&#8217;
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function &#8216;open&#8217;
loadndisdriver.c:73: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;syslog&#8217;
loadndisdriver.c:75: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:75: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;strerror&#8217;
loadndisdriver.c:75: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:76: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function &#8216;fstat&#8217;
loadndisdriver.c:81: warning: implicit declaration of function &#8216;close&#8217;
loadndisdriver.c:84: error: &#8216;size&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function &#8216;mmap&#8217;
loadndisdriver.c:86: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
loadndisdriver.c:86: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: &#8216;MAP_FAILED&#8217; undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function &#8216;strncpy&#8217;
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:95: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:96: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:69: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;parse_setting_line&#8217;:
loadndisdriver.c:109: warning: implicit declaration of function &#8216;isspace&#8217;
loadndisdriver.c:115: warning: implicit declaration of function &#8216;strchr&#8217;
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
loadndisdriver.c:115: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:118: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function &#8216;strlen&#8217;
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c: In function &#8216;read_conf_file&#8217;:
loadndisdriver.c:150: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:151: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:151: error: &#8216;config&#8217; undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function &#8216;lstat&#8217;
loadndisdriver.c:158: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:160: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function &#8216;sscanf&#8217;
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:178: warning: implicit declaration of function &#8216;fopen&#8217;
loadndisdriver.c:178: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function &#8216;fgets&#8217;
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:205: warning: implicit declaration of function &#8216;fclose&#8217;
loadndisdriver.c:150: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_bin_file&#8217;:
loadndisdriver.c:217: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:217: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function &#8216;tolower&#8217;
loadndisdriver.c:221: warning: implicit declaration of function &#8216;chdir&#8217;
loadndisdriver.c:222: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:224: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:232: warning: implicit declaration of function &#8216;ioctl&#8217;
loadndisdriver.c:232: warning: implicit declaration of function &#8216;_IOW&#8217;
loadndisdriver.c:232: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;load_driver&#8217;:
loadndisdriver.c:249: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:249: error: &#8216;driver_dir&#8217; undeclared (first use in this function)
loadndisdriver.c:251: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:255: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:255: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:257: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:259: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function &#8216;opendir&#8217;
loadndisdriver.c:267: warning: implicit declaration of function &#8216;malloc&#8217;
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
loadndisdriver.c:271: warning: implicit declaration of function &#8216;memset&#8217;
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:280: warning: implicit declaration of function &#8216;readdir&#8217;
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function &#8216;stat&#8217;
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function &#8216;S_ISREG&#8217;
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function &#8216;strcasecmp&#8217;
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function &#8216;strcpy&#8217;
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:318: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c:344: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c:346: warning: implicit declaration of function &#8216;closedir&#8217;
loadndisdriver.c:348: warning: implicit declaration of function &#8216;free&#8217;
loadndisdriver.c:355: warning: implicit declaration of function &#8216;munmap&#8217;
loadndisdriver.c:355: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:355: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:357: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:357: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c: In function &#8216;get_device&#8217;:
loadndisdriver.c:367: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:370: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:370: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:373: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:374: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function &#8216;snprintf&#8217;
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function &#8216;snprintf&#8217;
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:367: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_device&#8217;:
loadndisdriver.c:419: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:419: error: &#8216;dir&#8217; undeclared (first use in this function)
loadndisdriver.c:423: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:423: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:426: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:427: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:429: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;get_ioctl_device&#8217;:
loadndisdriver.c:464: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:464: error: &#8216;proc_misc&#8217; undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function &#8216;strstr&#8217;
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function &#8216;strstr&#8217;
loadndisdriver.c:473: warning: implicit declaration of function &#8216;strtol&#8217;
loadndisdriver.c:473: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:483: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:483: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function &#8216;unlink&#8217;
loadndisdriver.c:489: warning: implicit declaration of function &#8216;mknod&#8217;
loadndisdriver.c:489: error: &#8216;S_IFCHR&#8217; undeclared (first use in this function)
loadndisdriver.c:489: error: &#8216;MISC_MAJOR&#8217; undeclared (first use in this function)
loadndisdriver.c:490: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:495: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c: In function &#8216;main&#8217;:
loadndisdriver.c:511: warning: implicit declaration of function &#8216;openlog&#8217;
loadndisdriver.c:511: error: &#8216;LOG_PERROR&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_CONS&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_DEBUG&#8217; undeclared (first use in this function)
loadndisdriver.c:513: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function &#8216;strncmp&#8217;
loadndisdriver.c:517: warning: implicit declaration of function &#8216;printf&#8217;
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
loadndisdriver.c:527: warning: implicit declaration of function &#8216;atoi&#8217;
loadndisdriver.c:542: warning: implicit declaration of function &#8216;atof&#8217;
loadndisdriver.c:549: warning: implicit declaration of function &#8216;strcmp&#8217;
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:590: warning: implicit declaration of function &#8216;closelog&#8217;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/taoman/Desktop/ndiswrapper/utils'
make: *** [install] Error 2
taoman@taoman-laptop:~/Desktop/ndiswrapper$ 




Can someone please decypher this for me?

---

### Post by New2Linux0319 on 2008-04-12
i think we have same problem.

i have the Lynksis USB wireless G network adapter and it is not recognized on he network manager window.

i had to restart in windows xp using this same device in order to get online and find a solution.

---

### Post by dstew on 2008-04-12
> Can someone please decypher this for me?It looks like you are trying to compile ndiswrapper from source. Have you installed the linux-headers package for your kernel? You can get your kernel version by```
uname -r
```You might not need the latest ndiswrapper version, maybe the one packaged with Ubuntu will work for you. Or, there might be a restricted driver for your hardware. Check in System --> Administration -->  Restricted Drivers Manager to see.

To see where you are at currently, do these commands and post the output on the forum:```
lspci
iwconfig
```The MacBook is an Intel-based system, right?

---

### Post by Lori700698 on 2008-04-12
I'm having the same problem, the liksys is working i have the laptop hard wired to it now and everybody else is using the wireless system.  seems that we need some kind of driver.

---

### Post by Taoman420 on 2008-04-17
taoman@taoman-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 22
       serial: 00:19:e3:62:35:f1
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Network controller
       product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0




taoman@taoman-laptop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:19:e3:62:35:f1
Sending on   LPF/eth0/00:19:e3:62:35:f1
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
taoman@taoman-laptop:~$ ipconfig
bash: ipconfig: command not found
taoman@taoman-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:E3:62:35:F1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth0:avah Link encap:Ethernet  HWaddr 00:19:E3:62:35:F1  
          inet addr:169.254.8.143  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4568 (4.4 KB)  TX bytes:4568 (4.4 KB)


taoman@taoman-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

taoman@taoman-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

taoman@taoman-laptop:~/Desktop/ndiswrapper$ ndiswrapper -v
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
taoman@taoman-laptop:~/Desktop/ndiswrapper$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/19.2kB of archives.
After unpacking 106kB of additional disk space will be used.
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
taoman@taoman-laptop:~/Desktop/ndiswrapper$

---

### Post by dstew on 2008-04-17
You need a driver for your Atheros card. One thing to check before proceeding more with ndiswrapper is the Restricted Drivers Manager in System --> Administation. See if they have a driver or HAL for your card. If so, install it. That might be all you need to do.

Do you have a wired internet connection? If so, install the package ndisgtk, which is a graphical front-end for ndiswrapper that will make the process easier. If you don't have an internet connection, you can still install packages off-line with [nonetdebs]("http://nonetdebs.homeip.net/").

---

