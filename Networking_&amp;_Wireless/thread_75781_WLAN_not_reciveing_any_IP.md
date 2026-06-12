---
title: "WLAN not reciveing any IP"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by hamil on 2005-10-14
Hello!

I had a similar problem in Hoary, but it dissapered when I installed Breezy Colony 4.
2 days ago, when i did an upgrade, I got disconnected from the net on my Ubuntu machine. I thought it may be a minor bug, that would be fixed, whith the final release of Breezy.
I did a fresh install yesterday, looking forward to surf with my Netgear WLAN adapter card again... But no..

During the installation process, my card is detected, and I entered the correct ESSID, and key. It also downloaded some languagefiles from the net during the installation, so it should work in X also??
After logging in, i tried to open firefox and surf, but network server is not found.
I opened the network administration, and could see that the ESSID was correct, and that the password was correct. I tried to disable, and enable a couple of times, but no help doing that.
A friend of me recommended the Netapplet, so I installed that one. But the netapplet can not see any of the available networks. I have 4 diffrent ones, which I can see in Network admin, 3 of those which I have the key for.
I have set it to DHCP, and not Static IP, since I do not know any other information but the DNS..

sudo iwlist scan gives, amongst other results, this result:
```
wlan0 Scan completed : Cell 02 - Address: 00:0F:3D:DF:EB:89
ESSID:"Etasje 3" Mode:Master Frequency:2.462 GHz (Channel 6) 
Quality=39/100 Signal level=15/100 Noise level=0/100 Encryption key:on Bit 
Rate:54 Mb/s

```Which is the network I am supposed to connect to. (And which I gave the ESSID, and key to during the installlation process.)

sudo iwgetid, gives no respone at all in the terminal.

sudo iwevent, gives this output:
```
Waiting for Wireless Events from interfaces... 06:40:24.463747 wlan0 
New Access Point/Cell address:00:00:00:00:00:00

```

sudo ifconfig has this output:
```
lo Link encap:Local Loopback inet addr:127.0.0.1 Mask:255.0.0.0 inet6 
addr: ::1/128 Scope:Host UP LOOPBACK RUNNING MTU:16436 Metric:1 RX 
packets:1538 errors:0 dropped:0 overruns:0 frame:0 TX packets:1538 
errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0 RX 
bytes:134881 (131.7 KiB) TX bytes:134881 (131.7 KiB) wlan0 Link 
encap:Ethernet HWaddr 00:0F:B5:80:B6:D9 inet6 addr: 
fe80::20f:b5ff:fe80:b6d9/64 Scope:Link UP BROADCAST MULTICAST 
MTU:1500 Metric:1 RX packets:0 errors:0 dropped:0 overruns:0 frame:0 TX 
packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 
txqueuelen:1000 RX bytes:0 (0.0 b) TX bytes:0 (0.0 b) Interrupt:18 Base 
address:0xe000

```

When i ran the sudo ifdown wlan0 command, I got an errormessage? It outputed like this:
```
There is already a pid file /var/run/dhclient.wlan0.pid with pid 9168 
killed old client process, removed PID file Internet Systems Consortium DHCP 
Client V3.0.2 Copyright 2004 Internet Systems Consortium. All rights reserved.
 For info, please visit http://www.isc.org/products/DHCP sit0: unknown 
hardware address type 776 sit0: unknown hardware address type 776 
Listening on LPF/wlan0/00:0f:b5:80:b6:d9 Sending on 
LPF/wlan0/00:0f:b5:80:b6:d9 Sending on Socket/fallback

```

While the command sudo ifup wlan0 has this output:
```
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0 
Internet Systems Consortium DHCP Client V3.0.2 Copyright 2004 Internet 
Systems Consortium. All rights reserved. For info, please visit 
http://www.isc.org/products/DHCP sit0: unknown hardware address type 776 
sit0: unknown hardware address type 776 Listening on 
LPF/wlan0/00:0f:b5:80:b6:d9 Sending on LPF/wlan0/00:0f:b5:80:b6:d9 
Sending on Socket/fallback DHCPDISCOVER on wlan0 to 255.255.255.255 port 
67 interval 5 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1 No 
DHCPOFFERS received. No working leases in persistent database - sleeping.

```

I also tried to manually configure with the commands:
sudo iwconfig wlan0 ESSID "Etasje 3"
sudo iwconfig wlan0 key open nnnnnnnnnn
sudo iwconfig up
sudo /etc/init.d/networking restart
But none of the above got me any closer to get online...

Hope that some of the information above is useful to get me online again?

Any ideas to what I can do to get connected on my Ubuntu machine again?

Thank you in advance for any help.
Brgds
Lasse

---

### Post by Skid on 2005-10-14
I am having the same problem also, with a Cisco Aironet 350.  my WLAN card, also shows up ast eth1, not wlan0, etc..  I'd also be interested to see any advice regarding this. (PS not trying to jack your post!)

---

### Post by i-x on 2005-10-14
This is what I do to get my wlan card to connect.


[FONT="Lucida Console"]su
iwlist wlan0 scan
iwconfig wlan0 essid "Whatever"
ifconfig eth0 down
ifconfig wlan0 up
dhclient wlan0
ping -c 2 [www.google.com](www.google.com)[/FONT]

Does this work for you? 
ifup/down don't work at all for me, so I just don't use them.

---

### Post by hamil on 2005-10-14
I have no clue about what just happened...
I rebooted into Ubuntu to try what i-x just suggested..
When starting up X, I saw that the weather aplet just loaded the weather...

JIIIPIII I'm back online with my Ubuntu! (But I do not have any clue whatsoever what just happened....)

Going to surf all day long!

Brgds
Lasse

---

### Post by i-x on 2005-10-14
Congratulations Lasse!

I have the same problem as you from time to time. For mysterical reasons iwconfig refuse to sign on a wlan. 

What driver do you use? I have a **Broadcom** card running on nsdiswrapper with driver **bcmwl5a**.

---

### Post by hamil on 2005-10-14
I have a NetGear WG311, PCI adapter, which works out of the box.
It uses the acx_pci driver. It is recognised as an ACX 111 54 Mbps, Texas Instrument.

It just dropped the connection, so I had to retart the machine to get online again...

---

### Post by trubblemaker on 2006-01-25
one fix that worked for me with my broadcom native driver was
```
iwconfig 
```
see if you have an essid if you don't or if the access point is set to repeated 00 or FF
if you don't have an essid:
[INDENT]```
iwlist wlan0
```
find the network you want find it's essid
```
sudo iwconfig wlan0 essid my-fave-essid
```[/INDENT]
if you do have an essid:
[INDENT]
```
sudo iwconfig wlan0 rate 11M
```
[/INDENT]
either use network manager to get an id or use:
```
sudo dhclient wlan0
```
this should help, but it suck's to transfer data at 11Mb, hey it worked for me.

---

