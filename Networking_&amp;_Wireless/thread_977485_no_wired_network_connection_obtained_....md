---
title: "no wired network connection obtained ..."
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by sidm on 2008-11-10
Hi,

I just installed 8.10 on a Pentium 4 with a Asus P4P800 motherboard
and a Marvell Yukon Gigabit Ethernet 10/100/1000Base-T Adapter,
behind a SMC Barricade ADSL modem annex 4-port ADSL router with
built-in DHCP server.
Everything seemed OK, but I can't get a network connection:
"Requesting a network address for the wired network ..." yields
"The network connection has been disconnected" after a minute or so.

My ethernet controller seems to be recognized (see lspci output below,
and the HWaddr in ifconfig output - also below - is correct).
However, in Network Tools | Devices, the eth0 device is listed without
information ("Hardware address: not available") and no network address
was obtained.

Up until a few hours ago, this box was running fine with Fedora 8, and
my laptop (also running Fedora 8) still does ...

I don't really see what went wrong, could anyone please give a hint?

Thanks in advance!


```
$lspci | grep ther

02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

```

```
$ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:2f:7f:07:b1  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14496 (14.4 KB)  TX bytes:14496 (14.4 KB)

```

---

### Post by rpaco on 2008-11-10
Yeah 8.10 Tells me that I have no wireless card (although it is actually connected via wireless ATM ), but that I have a wired connection which I do not. It also wiped all my fixed addresses and dns addresses, which is very annoying.

---

### Post by sidm on 2008-11-10
Thanks, but I have neither a wired nor a wireless connection; very disappointing.

Could there be a problem with the skge driver?  From dmesg:

```
Nov 10 16:48:32 arthur kernel: [   33.881493] skge eth0: enabling interface
Nov 10 16:48:34 arthur kernel: [   35.568474] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
Nov 10 16:48:34 arthur kernel: [   35.633987] NET: Registered protocol family 17
Nov 10 16:48:42 arthur pulseaudio[5491]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 10 16:48:42 arthur pulseaudio[5493]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 10 16:48:42 arthur pulseaudio[5493]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 10 16:48:57 arthur kernel: [   58.248918] skge eth0: disabling interface
Nov 10 16:48:57 arthur kernel: [   58.251286] skge eth0: enabling interface
Nov 10 16:48:59 arthur kernel: [   60.118165] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
```

eth0 is enabled, up, disabled, enabled and up again?

I would greatly appreciate any help!

---

### Post by oferfrid on 2008-11-10
try this (I personally downgraded to 8.04, on Asus m2n-e)
[http://ubuntuforums.org/showthread.php?t=963335](http://ubuntuforums.org/showthread.php?t=963335)

---

### Post by sidm on 2008-11-10
Thank you!  I missed that thread.  After reading it, I did

```
sudo update-rc.d -f NetworkManager remove
```

Added the following to /etc/network/interface:
```
auto eth0
iface eth0 inet dhcp
```

Added the IP address of my router to /etc/resolv.conf:
```
nameserver 192.168.1.1
```

After rebooting I typed
```
sudo dhclient eth0
```

And now I am running apt-get upgrade ...

---

### Post by capran on 2008-12-25
Hi, I'm trying to setup Kubuntu 8.10 on my Shuttle SN95G5 which has a Marvell 88E8001 Gigabit adapter built-in. This ethernet works in Windows and Ubuntu 8.10, but under Kubuntu for some reason, it does not.

I'm trying Kubuntu because I'd like to use Linux MCE [www.linuxmce.com](www.linuxmce.com), which says it requires this distro. I use this PC as a HTPC on my HDTV.

Specifically what happens is, if I open up terminal, and type ifconfig, I see that eth0 has an IP acquired by DHCP from my router. I see that with route the default gateway is my router's IP.

However, no network connections of any type seem to be able to work. I cannot even ping the router (Destination Host Unreachable.)

I've tried the tricks above, but they don't work. I also tried installing the driver from Marvell. Both skge and sk98lin won't work. Under Ubuntu, skge does work.

I can't figure out what's going on. Kubuntu is running the same kernel version, and the /lib/modules seems to be the same too.

Help? (or, if someone knows if LinuxMCE can be made to work with Ubuntu, that'd be good too.)

---

