---
title: "How to install drivers for network adapter ?"
date: 2005-09-14
forum: Networking &amp; Wireless
---

### Post by DarkRider on 2005-09-14
Hello,
First pls note that I am total newbie to Linux and UBUNTY. Unfortunately ubuntu does not recognize my integrated Network card (ASROCK 939DUAL SATA2 MOBO) , so I need to install drivers my self. How to do that ?  

M1695  Drivers are available from ULI site for Linux kernel 2.6.x . In instructions it is said that 
Copy uli526x.c to /usr/src/linux-2.6.x/drivers/net/tulip/, (This directory does not exists in UBUNTU !?) and modify the
following file in this directory.

1.Kconfig.in (This file does not exist in UBUNTU !)


They are saying that to install the driver, you should reconfigure and recompile your Linux kernel. How can I do that ? PLs help me !! There is only one driver file named uli526x.c where it should be put and compiled ? or is there another way to do it in UBUNTU ?



lspci and lspci -n results  here:
0000:00:00.0 Host bridge: ALi Corporation: Unknown device 1695 
0000:00:01.0 PCI bridge: ALi Corporation: Unknown device 524b 
0000:00:02.0 PCI bridge: ALi Corporation: Unknown device 524c 
0000:00:04.0 Host bridge: ALi Corporation: Unknown device 1689 
0000:00:05.0 PCI bridge: ALi Corporation: Unknown device 5246 
0000:00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge 
0000:00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70) 
0000:00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU] 
0000:00:08.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Cont roller Aud Device (rev 20) 
0000:00: 11.0 Ethernet controller: ALi Corporation: Unknown device 5263 (rev 40) 
0000:00: 12.0 IDE interface: ALi Corporation M5229 IDE (rev c7) 
0000:00:12.1 Unknown mass storage controller: ALi Corporation: Unknown device 5289 (rev 10)
OOOO:00:13.0-USB Controller: ALi Corporation USB 1.1 Controller (rev 03) 
0000:00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) 
0000:00:13.2 USB Controller: ALi Corporation USB 1.1 COI!troller (rev 03) 
0000:00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) 
0000:00: 18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
0000:00: 18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge 
0000:03:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0042 (rev a1) 

jan@ubuntu:-$lspci -n 
0000:00:00.00600: 10b9:1695 
0000;00;01.00604: 10b9:524b 
0000:00:02.00604: 10b9:524c 
0000:00:04.00600: 10b9:1689 
0000:00:05.00604: 10b9:5246
0000:00:06.00604: 10b9:5249 
0000:00:07.00601: 10b9:1563 (rev 70) 
0000:00:07.10680: 10b9:7101 
0000:00:08.00401: 10b9:5455 (rev 20) 
0000:00:11.00200: 10b9:5263 (rev 40) 
0000:00:12.00l0l: 10b9:5229 (rev c7) 
0000:00:12.10180: 10b9:5289 (rev 10) 
0000:00:13.00c03: 10b9:5237 (rev 03) 
0000:00:13.10c03: 10b9:5237 (rev 03) 
0000:00:13.20c03: 10b9:5237 (rev 03) 
0000:00:13.3Oc03: 10b9:5239 (rev 01) 
0000:00:18.00600: 1022:1100 
0000:00:18.10600: 1022:1101 
0000:00:18.20600: 1022:1102 
0000:00:18.30600: 1022:1103 
0000.03.00.00300: 10de:0042 (rev a1)

---

### Post by mlomker on 2005-09-14
I did a google search and it sounds like an SIS900 card.

Try this in a terminal window:

```

sudo modprobe sis900
dmesg | grep sis900

```

What does it say?  If it loads then this should bring it up:

```

sudo ifconfig eth0
sudo dhclient eth0

```

---

### Post by DarkRider on 2005-09-15
Unfortunately it didnt help  :???:  . I get following response. What to do next ? Pls. help !

jan@ubuntu:~$ sudo modprobe sis900
Password:
jan@ubuntu:~$ dmesg | grep sis900
[  167.933819] sis900.c: v1.08.08 Jan. 22 2005
jan@ubuntu:~$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:13:8F:29:69:91
          inet addr:192.168.255.6  Bcast:192.168.255.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe29:6991/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:2 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:804 (804.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe400

jan@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:13:8f:29:69:91
Sending on   LPF/eth0/00:13:8f:29:69:91
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
jan@ubuntu:~$

---

### Post by mlomker on 2005-09-16
I actually gave you the wrong command, but what I find interesting is that your card already has an IP address on it.  Is that a static address that you configured?

> 
          inet addr:192.168.255.6  Bcast:192.168.255.255  Mask:255.255.255.0


Post the output of:

```

cat /etc/network/interfaces
cat /etc/modules
ifconfig
route -n

```

You might want to look at the output of this, which is the dhcp client log:

```

cat /var/log/syslog | grep dhclient | more

```

---

### Post by DarkRider on 2005-09-18
No, I dont havent configured static ip, it is running DCHP. Here are all  the listings;

jan@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
        network 192.168.255.0
        broadcast 192.168.255.255

auto eth0

iface ppp0 inet ppp
provider ppp0
jan@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
rtc
jan@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:8F:29:69:91
          inet6 addr: fe80::213:8fff:fe29:6991/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:120 (120.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:58427 (57.0 KiB)  TX bytes:58427 (57.0 KiB)

jan@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
jan@ubuntu:~$ cat /var/log/syslog | grep dhclient | more
Sep 15 20:11:32 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port
 67 interval 7
Sep 15 20:11:39 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port
 67 interval 9
Sep 15 20:11:48 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port
 67 interval 11
Sep 15 20:11:59 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port
 67 interval 13
Sep 15 20:12:12 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port
 67 interval 18
Sep 15 20:12:30 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port
 67 interval 3
Sep 15 20:12:34 localhost dhclient: No DHCPOFFERS received.
Sep 15 20:12:34 localhost dhclient: No working leases in persistent database - s
leeping.
jan@ubuntu:~$

---

### Post by mlomker on 2005-09-18
> **DarkRider]No, I dont havent configured static ip, it is running DCHP. Here are all  the listings said:**
> 

Then it must have been working at the time of that post because it had an IP address.

[quote]
        network 192.168.255.0
        broadcast 192.168.255.255


Remove that if you're using dhcp.

What does this tell you?

```

dmesg | grep eth0

```

I'm not clear what driver it is using at this point.  It's also strange that it had an IP address in your first post.

---

### Post by DarkRider on 2005-09-19
[QUOTE=mlomker]Then it must have been working at the time of that post because it had an IP address. [/QUOTE]

It hasnt been working at all, 100% sure about that. I have tried to access web w. firefox every time and never succeeded.

dmesg gives following info:

jan@ubuntu:~$ dmesg | grep eth0
[   49.987954] eth0: ULi M5261/M5263 rev 64 at 000000000001e400, 00:13:8F:29:69:91, IRQ 17.
[   80.916223] eth0:  Invalid media table selection 128.
[   88.165735] eth0: no IPv6 routers present
jan@ubuntu:~$

BTW, THX for your help so far ! I really do hope that you can help me to fix this  :-)

---

### Post by mlomker on 2005-09-19
I found a [post](http://www.mail-archive.com/linux-kernel@vger.kernel.org/msg84683.html)  online that referred to the 'tulip' driver being used on that card.  Hoary has an older version of the kernel than the one mentioned in that post.

The poster did mention that upgrading his motherboard BIOS to the latest version helped.  Have you checked to see if you're on the latest?

---

### Post by DarkRider on 2005-09-20
I have the latest bios 1.20. I did upgrade as soon as I got this mobo. What comes to latest linux kernel  2.6.x  network drivers, those are available from [www.uli.com.tw](www.uli.com.tw)  , but I dont know how to install those. That was my question initially. How to install those network drivers for linux as I have already latest BIOS ?

---

### Post by mlomker on 2005-09-20
>  That was my question initially. How to install those network drivers for linux as I have already latest BIOS ?

okay, I downloaded the file and took a look.  Here's what you need to do to prepare the kernel source:

```

su
apt-get install linux-tree
cd /usr/src

```

Use the **ls** command to get the filename.  I'm going to use mine in this example:

```

tar jxvf linux-source-2.6.10.tar.bz2

```

That'll create the directory mentioned in the readme.  Then you'll need to copy the .config file from your kernel to that directory.  Use **ls /boot** to get the name, once again this is my filename.

```

cd /usr/src/linux-source-2.6.10
cp /boot/config-2.6.10-5-amd64-k8 .config

```

From there you can try their instructions.

---

### Post by PureW on 2007-02-23
> **mlomker said:**
> okay, I downloaded the file and took a look.  Here's what you need to do to prepare the kernel source:

```

su
apt-get install linux-tree
cd /usr/src

```


.....


From there you can try their instructions.

I have the same problem with my PC (ubuntu 6.10). Since I can't connect I can't use apt-get, what must I do instead? I have a laptop next to my computer with internet and a cd-burner (openSUSE and windows).

---

