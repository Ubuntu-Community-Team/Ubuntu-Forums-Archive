---
title: "Internet is slower in Linux than in Windows"
date: 2014-01-18
forum: Networking &amp; Wireless
---

### Post by lavini557 on 2014-01-18
Sigh...why is this happening to me?
So, basically I have a thread here about my internet issue here: [http://ubuntuforums.org/showthread.php?t=2188499](http://ubuntuforums.org/showthread.php?t=2188499)

BUT
things have not been working out lately.
I mean, my internet is...ok. I can surf the web, even if I have to wait for some time (sometimes for a really long time) for the web page to appear, but I tend to disconnect to my network at random times. I dismissed this because it didn't really bother me when I was trying to troubleshoot in my previous thread, but now it happens every single day. This happens even though the rest of the computers in my house (my parents have a Windows 7 laptop, and my brother has a Windows 8 laptop and an iMac) can connect to the internet just fine. I even try to use a "Connect to hidden wireless network" option to try to connect to it, but that doesn't work.

The funny thing is, I have no internet problems in Windows 7. I actually set up a dual-boot recently to run a program for school that wouldn't run on Wine (well, Wine has never worked for me so far anyway so I expected that to happen), and Windows 7's internet was SO FAST compared to Linux. In Linux, I can't play online games as comfortably. I lag in games like Awesomenauts, and turn-based online games (like Dofus, for example - which I tried recently) take way too long to input my moves that the time runs out before my move can even be carried out. :( This barely happens in Windows. The only time it really happens is when I play League of Legends (because of peer pressure and boredom - I stopped playing now) and my parents happen to be watching a TV show on their computer using the internet. *sigh* But I don't want to go to Windows.
Does anyone have any idea what I could do to fix this problem? I'm assuming it's a driver issue for the speed issue, but what's with the disconnect from the network and being unable to connect to the network again? I have no idea what's going on.

Oh, and if it helps, I didn't touch anything network related after my previous thread was "solved".

---

### Post by slooksterpsv on 2014-01-18
What are your ping times if you try to ping a site like google or that?

What version of Linux? 12.04, 13.10, Ubuntu, Kubuntu, etc. Also if you can get us the kernel version that would be great - uname -a

What about your networking information as well, that way we can start to try things to trouble shoot.

---

### Post by lavini557 on 2014-01-19
lavinia@Pavilion:~$ uname -a
Linux Pavilion 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


lavinia@Pavilion:~$ ping google.com
PING google.com (173.194.43.41) 56(84) bytes of data.
64 bytes from lga15s35-in-f9.1e100.net (173.194.43.41): icmp_seq=1 ttl=53 time=102 ms
64 bytes from lga15s35-in-f9.1e100.net (173.194.43.41): icmp_seq=2 ttl=53 time=85.3 ms
64 bytes from lga15s35-in-f9.1e100.net (173.194.43.41): icmp_seq=3 ttl=53 time=60.3 ms
64 bytes from lga15s35-in-f9.1e100.net (173.194.43.41): icmp_seq=4 ttl=53 time=96.0 ms
64 bytes from lga15s35-in-f9.1e100.net (173.194.43.41): icmp_seq=5 ttl=53 time=176 ms
64 bytes from lga15s35-in-f9.1e100.net (173.194.43.41): icmp_seq=6 ttl=53 time=146 ms
64 bytes from lga15s35-in-f9.1e100.net (173.194.43.41): icmp_seq=14 ttl=53 time=60.6 ms
^Z
[2]+  Stopped                 ping google.com

Here's the kernel name and pinging google. google.com takes a little long takes a little long to start but then it works fine.
Oh, and are there any commands that you want me to input to troubleshoot?

---

### Post by slooksterpsv on 2014-01-20
Hmm.. are you connecting via WiFi (I'm going to assume so). What wireless card do you have in your system? Do you know how strong the signal strength is to the router?

---

### Post by lavini557 on 2014-01-20
Yes I do use WiFi. I don't know what my card is. This is my laptop model (if it helps):
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03188483&cc=us&dlc=en&lc=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03188483&cc=us&dlc=en&lc=en)
And signal power seems to vary from very high to very low on Linux, while signal power seems to constantly be high on Windows 7. Is this a issue in my Linux driver? That's what it seems like. And why do you think I get disconnected from my internet connection and can't connect to it for a period of time/after I reboot the laptop?

---

### Post by SlidingHorn on 2014-01-21
Please post the output of the following commands (one at a time) in CODE tags:

lspci

lsusb

ifconfig

iwconfig

sudo lshw -C network

This should give everyone the majority of the info they'll need to help.

---

### Post by lavini557 on 2014-01-26
I have no idea if I'm doing the code thing right while I'm typing, but...here it goes...
```

lavinia@Pavilion:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6620G]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD] FCH IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
03:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)

```
```

lavinia@Pavilion:~$ lsusb
Bus 002 Device 002: ID 064e:d281 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 138a:0018 Validity Sensors, Inc. Fingerprint scanner
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```

lavinia@Pavilion:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:2e:5f:98:ba:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)


wlan0     Link encap:Ethernet  HWaddr 20:10:7a:4a:96:26  
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2210:7aff:fe4a:9626/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1565832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:600754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2203197132 (2.2 GB)  TX bytes:75401225 (75.4 MB)

```
```

lavinia@Pavilion:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"WLAN-DC5B"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:22:2D:7B:DC:5D   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:327   Missed beacon:0

```
```

lavinia@Pavilion:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 08:2e:5f:98:ba:6f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:51 ioport:3000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 20:10:7a:4a:96:26
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.11.0-15-generic firmware=N/A ip=192.168.0.24 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0200000-f0203fff

```

---

### Post by slooksterpsv on 2014-01-26
What we should do is find a wireless scanner see what networks are around and what channel's they're using, as this can cause a problem. I can't find a good one for Ubuntu though, any thoughts others?

EDIT: What does a speedtest show you're getting? Or how is it slower exactly?

---

### Post by lavini557 on 2014-01-28
It's slow most of the time. Like sometimes it's slow, and sometimes it's normal speed. The power of the signal seems to change a lot while I'm using my laptop (shown by the icon in the notifications area), so I don't know what's going on there. Sometimes, I can't connect to my network at all (as mentioned before). When that happens, I have to either restart the laptop or wait a few hours before I can connect again. It's probably not a problem with the network because the rest of my family can connect to our network just fine. The slowness is mostly noticeable when buffering videos or playing online games. On Windows, I can watch videos just fine without having to wait like 5 minutes for a 5 minute video, or 20 minutes for a 20 minute video, and so on. I also can't play online games comfortably because I "disconnect", making my game have internet lag and then my team yelling at me at the end of the game for being a noob. Windows? I don't get yelled at unless I make a legitimate mistake.
It's the exact same hardware, yet I get different results...

---

### Post by slooksterpsv on 2014-01-29
Sometimes the drivers, where they're open source, aren't as strong or thoroughly developed vs Windows, which is where the issue may come in with network speed. You could check the channels of the wifi or see if you can find a driver on Realtek's website for your specific wireless card. That may be the best thing to do as you may get better results.

---

### Post by lavini557 on 2014-01-29
Ok, so I found the driver here (RTL8188CE, for kernel 2.6.23):
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)
However, there's a problem. It won't install. :(
I tried to follow the readme, and here's the terminal stuff:
```

root@Pavilion:/home/lavinia/Desktop/driver# make
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
gcc: error: /lib/modules/3.11.0-15-generic/build/include/linux/autoconf.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/lavinia/Desktop/driver/HAL/rtl8192/Makefile". Fix it to use ccflags-y.  Stop.
make[1]: *** [_module_/home/lavinia/Desktop/driver/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
make: *** [all] Error 2

```
```

root@Pavilion:/home/lavinia/Desktop/driver# make install
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
gcc: error: /lib/modules/3.11.0-15-generic/build/include/linux/autoconf.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/lavinia/Desktop/driver/HAL/rtl8192/Makefile". Fix it to use ccflags-y.  Stop.
make[1]: *** [_module_/home/lavinia/Desktop/driver/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
make: *** [all] Error 2

```

What's ccflags-y? And why can't it compile/install the driver? Any ideas?

---

### Post by lavini557 on 2014-01-30
bump

---

### Post by slooksterpsv on 2014-01-31
Do you have the linux kernel headers installed? If not do sudo apt-get install linux-headers-generic (I believe) and that will install them, then try again.

---

### Post by lavini557 on 2014-02-02
It says that I've already installed it.
```

lavinia@Pavilion:~$ sudo apt-get install linux-headers-generic
[sudo] password for lavinia: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

---

### Post by slooksterpsv on 2014-02-03
Is there a file called: configure  in the folder where you're running make in? If so try running it first.

---

### Post by lavini557 on 2014-02-03
There is no "configure" file :(.

---

### Post by slooksterpsv on 2014-02-04
One thing I failed to mention is you can try to load the driver and see if that helps via: sudo modprobe rtl8192 - I believe that module is included in the system. You could also pull the driver from Windows and use NDISWRAPPER to use the Windows driver (I haven't done it, but it may help). That's the only suggestions I have for now.

---

