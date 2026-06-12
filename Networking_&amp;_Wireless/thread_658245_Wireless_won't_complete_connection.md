---
title: "Wireless won't complete connection"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by pedersencato on 2008-01-04
Hi,
     I'm having trouble get my laptop to connect wirelessly to our home network. I'm running Kubuntu 7.10, and the wireless card is a DWL-G650 with an Atheros chip. KNetworkManager will detect the network, it will try to connect, but when at "Activation Stage: IP Configuration started" it fails. I've reset to defaults on the router, removed encryption, and tried just about everything I can find on the forums.

     My '/etc/network/interfaces' reads 

```
auto lo
iface lo inet loopback
```

     The output of iwconfig reads
```
lo     no wireless connections

wifi0     no wireless connections

ath0       IEEE 802.11g  ESSID:""   Nickname:""
           Mode:Managed   Frequency:2.437Ghz   Access Point: Not Associated
           Bitrate:0kb/s    Tx-Power:18 dBm    Sensitivity=1/1
           Retry:off    RTS thr:off    Fragment thr:off
           Power Management:off
           Link Quality=0/70    Signal Level=-94dBm    Noise level=-94dBm
           Rx invalid nwid:8039    Rx invalid crypt:0    Rx invalid frag:0
           Tx excessive retries:0    Invalid misc:0    Missed beacon:0

```

     The output of ifconfig reads
```
elin@elin:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:8039  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

elin@elin:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:13:46:A0:18:6F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:28 (28.0 b)  TX bytes:19266 (18.8 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-A0-18-6F-00-00-00-00-00-00-00-00-00                                                              -00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20200 errors:0 dropped:0 overruns:0 frame:667
          TX packets:738 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:1755792 (1.6 MB)  TX bytes:50852 (49.6 KB)
          Interrupt:11

```

     When I try "sudo dhclient ath0" I get
```
elin@elin:~$ sudo dhclient ath0
[sudo] password for elin:
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:13:46:a0:18:6f
Sending on   LPF/ath0/00:13:46:a0:18:6f
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

      Any help is much appreciated.

---

### Post by Predator[23rd] on 2008-01-04
try to add the following lines to */etc/network/interfaces*

[I]auto ath0
iface ath0 inet dhcp[/I]

and restart your network with **sudo /etc/init.d/networking restart**

---

### Post by pedersencato on 2008-01-04
I got this output when I restarted:

```
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:13:46:a0:18:6f
Sending on   LPF/ath0/00:13:46:a0:18:6f
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Still no connection. Looking at it that 'wifi0' interface seems odd to me, the MAC address alone makes it suspicious, could that have anything to do with it?

---

### Post by Predator[23rd] on 2008-01-04
is your router running a DHCP server in the first place?

---

### Post by pedersencato on 2008-01-04
Yes, most definitely. I've been fiddling with it and I can access the router configuration page(192.168.2.1) if I use manual configuration for KNetworkManager if I get the settings right, but can't figure out how to expand that into full on internet access.

---

### Post by rustybronco on 2008-01-04
please post the output of **lspci -nn**, **lshw -C network**, **iwlist scan** you find in a terminal

mac address filtering is off also? 
you can connect by wireless and access the router configuration page?

kevdog's trouble shooting guide is in my signature

---

### Post by pedersencato on 2008-01-04
Okay, I've got it working now through a messy compilation static IPs, DNS Servers, and lucky gusses, so I think I'm going to take advantage of the availability of the apt-get function and switch to wicd. Thanks for your help.

---

### Post by Predator[23rd] on 2008-01-04
sorry but I am still not convinced that your router has an active DHCP server and that this is the reason why network configuration fails ...

---

### Post by pedersencato on 2008-01-04
It does and is working fine now with KWifiManager.

---

### Post by Takagami on 2008-01-15
I have been having the same problem. This has just recently started after I switched to a P.O.S. Belkin wireless N router. Windows wireless, OSX86 wireless, and ANY rpm based distro works fine.

I am using ubuntu 7.10 Gnome. Everything is default from install (no updates, changes or otherwise) other then bcm43xx-fwcutter and firmware. Terminal output is the exact same regardless of network manager or WM.

I have had 7.10 installed many times prior and bcm43xx-fwcutter with the "fetch and extract" function has ALWAYS worked without problems until around the same time I switched the router.

Is there some incompatibility with the belkin brand router(s) that anyone is aware of?

If I use 7.04 and manually extract the wl_apsta.o file to /lib/firmware and /lib/firmware/"uname -r" all is well.

Have there been any changes in 7.10 (before updating) that could be causing problems? I am using the latest CD/DVD images from the osuosl mirror.

I am at a complete loss here.

---

