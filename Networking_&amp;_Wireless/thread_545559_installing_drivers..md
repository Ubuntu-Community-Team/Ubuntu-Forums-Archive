---
title: "installing drivers."
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by chrisruls00 on 2007-09-07
Im using a certain wireless card (a Hawking HWC54D) and the list of compatible cards says it works if you download a certain driver of the realtech website. The direct link was broken so i went to the root of the realtech website and went to support->Linux and found the driver and downloaded it then I extracted it. But I am VERY new to Ubuntu and any kind of Linux, so I dont know how to install this driver. Can anyone help?

---

### Post by chrisruls00 on 2007-09-07
Can anyone help me?

---

### Post by chrisruls00 on 2007-09-07
ok I found a .txt File with this in it:

How to compile

----------------------

     This Configuration Utility Application was developed by Qt/X11 Free Edition.

You can install the Qt/X11 Free Edition development when install the Linux OS by 

selecting the Qt/X11 development package or you can find it on Trolltech's website.



	[http://www.trolltech.com/](http://www.trolltech.com/)

	[ftp://ftp.trolltech.com/qt/source/qt-x11-free-3.2.1.tar.gz](ftp://ftp.trolltech.com/qt/source/qt-x11-free-3.2.1.tar.gz)



After install the package then follow the steps.



1.) qmake -o Makefile raconfig2500.pro

2.) make 



So I'm downloading this app now. I hope this solves it.

---

### Post by chrisruls00 on 2007-09-08
dran it! now i cant install that app! im really confused now...

---

### Post by chrisruls00 on 2007-09-08
ok, when i run this program it tells me to type ./configure but when i do it says make:g++ : E: no such command

---

### Post by unisol on 2007-09-08
do you have build-essentials installed?

---

### Post by chrisruls00 on 2007-09-08
whats build-essentials? Is it something I need?

---

### Post by kevdog on 2007-09-08
Can you post 

lspci -nn
lshw -C network

If its truly a realtech chipset in your wireless card I would recommend ndiswrapper + Win98 version of your wireless driver.  The info you supply will provide the answer.

---

### Post by chrisruls00 on 2007-09-08
I already tried ndiswraiper with my XP driver, sould I try it with my 98 driver?

lspci -nn:

00:00.0 Host bridge [0600]: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge [8086:1a30] (rev 11)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge [8086:1a31] (rev 11)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 420 Go] [10de:0175] (rev a3)
02:07.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
02:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:0b.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 32)
02:0b.1 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 32)
02:0d.0 System peripheral [0880]: Toshiba America Info Systems SD TypA Controller [1179:0805] (rev 03)
05:00.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)

lshw -C network:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@02:09.0
       logical name: eth0
       version: 10
       serial: 00:08:0d:06:e5:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.4 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:ce00-ceff iomemory:fcefff00-fcefffff irq:11
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@05:00.0
       logical name: ra0
       version: 01
       serial: 00:0e:3b:07:0a:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:70000000-70001fff irq:11

---

### Post by kevdog on 2007-09-08
Is this your wireless device??

05:00.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)


Its actually a ra chipset with a rt2500 driver. Which is totally different.

Anyway I want you to look at this thread.  Its for installing rt73 drivers, however the process is exactly the same for you, EXCEPT use some common sense, when rt73 is mentioned, I want you to use rt2500 instead.  I know it will work for you as it has for many other users:

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by chrisruls00 on 2007-09-08
I've looked at that thread but it doesn't seem to work. I get a bunch of errors when i type "sudo make" in the directory.

---

### Post by kevdog on 2007-09-08
Thats b/c you didnt install either the build-essential package or linux headers.

---

### Post by chrisruls00 on 2007-09-08
i ran

sudo aptitude install build-essential linux-headers-`uname -r`

and the ran

sudo make

and still got errors:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
chrisruls00@chrisruls00-laptop:/usr/src/rt2500-1.1.0-b4/Module$ sudo makemake[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/rt2500-1.1.0-b4/Module/rtmp_main.o
In file included from /usr/src/rt2500-1.1.0-b4/Module/rtmp_main.c:50:
/usr/src/rt2500-1.1.0-b4/Module/rt_config.h:58:40: error: linux/config.h: No such file or directory
/usr/src/rt2500-1.1.0-b4/Module/rtmp_main.c: In function ‘RT2500_open’:
/usr/src/rt2500-1.1.0-b4/Module/rtmp_main.c:343: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/usr/src/rt2500-1.1.0-b4/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/usr/src/rt2500-1.1.0-b4/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
rt2500.ko failed to build!
make: *** [module] Error 1

---

### Post by kevdog on 2007-09-08
Wow

Got me on that one.  Post those errors in the other rt73 thread and see if anyone has any insights for you.  Visit the website, and rather than doing the cvs release try the latest beta release on the download page.  Maybe there is a problem with the CVS version:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

---

### Post by chrisruls00 on 2007-09-08
i think i did do the beta version.

---

### Post by kevdog on 2007-09-08
Then do the cvs version.

---

### Post by chrisruls00 on 2007-09-08
yay the other version is working so far!

---

### Post by chrisruls00 on 2007-09-08
never mind... It worked further but when I was told to type ifconfig -a it told me to look for wlan but there wasn't any wlan entry

---

### Post by chrisruls00 on 2007-09-08
the weird thing is if i click the network icon at the top my houses wireless network shows up, even if I cant get it to connect.

---

### Post by kevdog on 2007-09-08
Post the following (you are close)

lshw -C network
/etc/iftab

---

### Post by chrisruls00 on 2007-09-08
ok, when i type sudo /etc/iftab it says command not found. the lshw -C network makes this:


  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@02:09.0
       logical name: eth0
       version: 10
       serial: 00:08:0d:06:e5:50
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.4 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:ce00-ceff iomemory:fcefff00-fcefffff irq:11
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@05:00.0
       logical name: ra0
       version: 01
       serial: 00:0e:3b:07:0a:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 link=yes multicast=yes wireless=RT2500 Wireless
       resources: iomemory:70000000-70001fff irq:11
chrisruls00@chrisruls00-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@02:09.0
       logical name: eth0
       version: 10
       serial: 00:08:0d:06:e5:50
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.4 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:ce00-ceff iomemory:fcefff00-fcefffff irq:11
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@05:00.0
       logical name: ra0
       version: 01
       serial: 00:0e:3b:07:0a:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 link=yes multicast=yes wireless=RT2500 Wireless
       resources: iomemory:70000000-70001fff irq:11

---

### Post by chrisruls00 on 2007-09-08
not much changed except when i type ifconfig -a I now have:

eth0      Link encap:Ethernet  HWaddr 00:08:0D:06:E5:50  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:dff:fe06:e550/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:183650 errors:265 dropped:0 overruns:0 frame:0
          TX packets:122723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:266437582 (254.0 MiB)  TX bytes:9941498 (9.4 MiB)
          Interrupt:11 Base address:0x4f00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:954 (954.0 b)  TX bytes:954 (954.0 b)

ra0       Link encap:Ethernet  HWaddr 00:0E:3B:07:0A:AC  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:263034 errors:85 dropped:85 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:10608315 (10.1 MiB)
          Interrupt:11 

ra0:avahi Link encap:Ethernet  HWaddr 00:0E:3B:07:0A:AC  
          inet addr:169.254.4.30  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11

---

### Post by kevdog on 2007-09-08
Can you do the following:

sudo ifconfig ra0 down
sudo modprobe -r rt2500sta
echo "blacklist rt2500sta" | sudo tee -a /etc/modprobe.d/blacklist
sudo modprobe rt2500
sudo /etc/init.d/dbus restart

Please then repost
lshw -C network

---

### Post by chrisruls00 on 2007-09-08
ok. here is the results:

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@02:09.0
       logical name: eth0
       version: 10
       serial: 00:08:0d:06:e5:50
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.4 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:ce00-ceff iomemory:fcefff00-fcefffff irq:11
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@05:00.0
       logical name: ra0
       version: 01
       serial: 00:0e:3b:07:0a:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 link=yes multicast=yes wireless=RT2500 Wireless
       resources: iomemory:70000000-70001fff irq:11

---

### Post by chrisruls00 on 2007-09-08
also on sudo modprobe -r rt2500sta i get:

FATAL: Module rt2500sta not found

---

### Post by chrisruls00 on 2007-09-08
ok now it changed again:

 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@02:09.0
       logical name: eth0
       version: 10
       serial: 00:08:0d:06:e5:50
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.4 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:ce00-ceff iomemory:fcefff00-fcefffff irq:11
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@03:00.0
       logical name: ra0
       version: 01
       serial: 00:0e:3b:07:0a:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Hawking Technologies, Inc.,10/2 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:6c000000-6c001fff irq:11

it says ndiswrapper now. I installed it earlier today but then it didnt seem to work. Well i just now unppluged my card from the top slot and pluged it in the the bottom one.

---

### Post by kevdog on 2007-09-08
Do this, and then reboot

sudo ifconfig ra0 down
sudo modprobe -r ndiswrapper
sudo modprobe rt2500

Basically I think youve caught on that you want the driver statement to say rt2500
Make sure you have the module in the kernel

modinfo rt2500
Should tell you that its from serial monkey.

Also its
cat /etc/iiftab

---

