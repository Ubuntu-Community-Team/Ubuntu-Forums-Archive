---
title: "Intrepid Ibex 8.10 on HP Pavilion dv6103nr Intel/PRO Wireless"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by GamerZFX on 2008-11-08
Ok, I'm using Ubuntu Intrepid Ibex 8.10 with ndiswrapper on a HP Pavilion dv6103nr With Windows wifi driver: netw4x32.inf

I have ran the following commands:
```
lspci
sudo lshw -C network
iwconfig
ifconfig
```

```
GamerZFX@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
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
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
```

```
GamerZFX@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:8b:be:6e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:af:6c:65
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.103 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:e2:2b:c5:70:5d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
luis@ubuntu:~$ sudo ls /lib/modules/`luis -r`/volatile
bash: luis: command not found
ls: cannot access /lib/modules//volatile: No such file or directory
luis@ubuntu:~$ sudo ls /lib/modules/`luis -r`volatile
bash: luis: command not found
ls: cannot access /lib/modules/volatile: No such file or directory
luis@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
```

```
GamerZFX@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"homesec"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

```
GamerZFX@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:af:6c:65  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:feaf:6c65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54046172 (54.0 MB)  TX bytes:2225883 (2.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6902 (6.9 KB)  TX bytes:6902 (6.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:8b:be:6e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39918 (39.9 KB)  TX bytes:6006 (6.0 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:18:de:8b:be:6e  
          inet addr:169.254.8.148  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-8B-BE-6E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Thanks in advanced for any help!

---

### Post by Laarmans on 2008-11-08
I have a similar problem on my Dell Latitude D820. Wifi worked fine but after upgrade to intrepid the wireless interface is DISABLED and I don't seem to know how to get it back on. 

results of lspci, lshw and iwconfig follows:

lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

 sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:79:fa:9f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:61:24:85
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5752-v3.19 ip=192.168.1.3 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ba:45:32:c7:8b:35
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Also did  sudo apt-get install linux-backports-modules-intrepid
based on a posting by Tim Gardner that I now can't find again. I didn't seem to make a difference though.

Laarmans

---

### Post by Laarmans on 2008-11-08
My problem seem to be solved - embarrassingly simple with 

sudo ifdown eth0
sudo ifup wlan0

And it just worked - still don't understand why it didn't show up in the Network manager.

Laarmans

---

### Post by GamerZFX on 2008-11-08
Ok well the sudo ifdown/ifup didn't fix my problem, however, I downgraded the driver from the net4x32.inf to the built in iwl3945 drivers and I really have no clue how it happened though. After I did that it still wasn't working so I tried a manual config on the device, then it said it was connected but didnt connect to a website, so then I set it back to automatic dhcp and then rebooted. Low and behold it says I'm connected and I try connecting to the internet and then I'm able to connect. The weirdest thing ever. So does anyone know what's going on with this magical phenomenon?

We have the same problem, yet I used the same method as Laarmans, yet it didn't work for me, yet I do something COMPLETELY different to yield the same results. Will this bug be fixed in the near future, or should I decide to return to Hardy 8.04 LTS??

---

### Post by openversus on 2009-02-11
Hi people... I have the same problem...

root@joda:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 19
       serial: 00:03:25:25:02:db
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.33 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:06:09.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:46:e5:be:dd:2b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


I tried a lot of solution but none's working for me....
help please :-)



PS: do not suggest me WICD... I had a lot of problems with it :-(

---

### Post by broomie on 2009-02-21
what worked for me was adding the line iwl3945 to /etc/modules and re booting

this was mentioned elsewhere on these forums

Dell m1330 intel3945 intrepid

---

### Post by openversus on 2009-02-23
Ok... that's your solution cause your driver's iwl3945. But mine's sky2 and I don't find it... so I really don't know waht to do...
Any suggestion?

---

### Post by Reiger on 2009-02-24
If your driver is sky2, why then add sky2 to /etc/modules after you have verified it works:
```

sudo modprobe sky2
sudo ifconfig
```
And you should see a device name for your Wireless card there (wlan something, typically).

---

### Post by openversus on 2009-02-28
Thank you for reply :-)
I do what you suggest me but nothing happnes and wireless still not working: That's what I got:

[I]versus@joda:~$ sudo modprobe sky2
versus@joda:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:25:02:db  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe25:2db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:295 errors:0 dropped:2 overruns:0 frame:0
          TX packets:336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:263009 (263.0 KB)  TX bytes:78956 (78.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1833075 (1.8 MB)  TX bytes:1833075 (1.8 MB)
[/I]

Any suggestion?

---

### Post by openversus on 2009-03-07
I'm still working on this problem \\:D/: I tried to install ipw3945 firmware but I obtain this:

[I]
root@joda:/home/ipw3945-1.2.2# make
Makefile:53: 
Makefile:54: WARNING: $SHELL not set to bash.
Makefile:55: If you experience build errors, try
Makefile:56: 'make SHELL=/bin/bash'.
Makefile:57: 
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

	IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1[/I]

so I tried to install ieee80211-1.2.18 but I get this:

[I]root@joda:/home/ieee80211-1.2.18# ./configure
-bash: ./configure: No such file or directory
root@joda:/home/ieee80211-1.2.18# make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.27-13-generic for ieee80211 components...
make -C /lib/modules/2.6.27-13-generic/build M=/home/versus/Desktop/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-13-generic'
/home/ieee80211-1.2.18/Makefile:17: 
/home/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/ieee80211-1.2.18/ieee80211_module.o
/home/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-13-generic'
make: *** [modules] Error 2
[/I]

please help ](*,)

---

### Post by openversus on 2009-03-23
In fact to use ubuntu 8.10 I choose to renounce to wireless :-(
No solution

---

