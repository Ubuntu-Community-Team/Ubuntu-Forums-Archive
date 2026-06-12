---
title: "wireless trouble: WUSB54GC not working in Hardy"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by kkram13 on 2008-06-16
Dear All,

After several very frustrating days... here's my story.
1. Upgraded from 7.10 to 8.04, with CD. Insert Linksys WUSB54GC (usb wireless dongle), it seems to work, I can connect to the router. But connection is shaky, frequently dropping and reconnecting. Initially this seemed due to the wife's (XP) computer having trouble without a proper driver for her (pcmcia) card. Fixed this, her wireless connection is now rock-solid, mine still shaky.

2. Decide to install ndiswrapper (via synaptic) and use the rt73 drivers from the CD that came with the Linksys. This seems to work: blue light is flashing. A lot. But the internet connection is very shaky. Sometimes it works, usually for a few minutes. Then it will cut out. Often I still have an IP address, sometimes I can even ping, both the router and google. After a while it cuts out again. Uninstalling ndiswrapper to try to revert to before does not work: 8.04 will not now recognise the Linksys!

3. In short, I have no reliable connection! Ran several commands to try and find out what's happening (see below). It seems I am connected to the network, with an ip address, but it seem not to be a working connection. Sometimes a second wireless adapter appears, and then disappears. Is there a conflict with drivers, perhaps?

Question: what do I do next? Any suggestions? Many thanks for any help!!

Mark

---
Other threads haven't helped me much (may be my lack of experience too!). But I did pull some commands and here is the output. They seem to suggest I have an IP address. ping sometimes works, sometimes doesn't, but is quite slow with high packet loss.

**lsusb**
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0457:0151 Silicon Integrated Systems Corp. Super Flash 1GB Flash Drive
Bus 001 Device 002: ID 13b1:0020 Linksys 
Bus 001 Device 001: ID 0000:0000 

**ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62040 (60.5 KB)  TX bytes:62040 (60.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:bf:73:5c:23  
          inet6 addr: fe80::214:bfff:fe73:5c23/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6888 (6.7 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:14:bf:73:5c:23  
          inet addr:169.254.5.11  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

*After a few minutes this changed to:*
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63940 (62.4 KB)  TX bytes:63940 (62.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:bf:73:5c:23  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bfff:fe73:5c23/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1633 (1.5 KB)  TX bytes:35375 (34.5 KB)

**iwconfig**
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"megerman"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:09:5B:47:EA:7E   
          Bit Rate=11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management: off
          Link Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**sudo dhclient wlan0**
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:bf:73:5c:23
Sending on   LPF/wlan0/00:14:bf:73:5c:23
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.7 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.7 from 192.168.0.1
bound to 192.168.0.7 -- renewal in 277049 seconds.

**sudo lshw -C network**
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:bf:73:5c:23
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt73 driverversion=1.52+Linksys, A Division of Cisc ip=192.168.0.7 link=yes multicast=yes wireless=IEEE 802.11g

**ping 192.168.0.1**
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

(no response, press Ctrl+C)

--- 192.168.0.1 ping statistics ---
31 packets transmitted, 0 received, 100% packet loss, time 30074ms

**ping [www.google.com](www.google.com)**
nothing shows up at all, so after a while I Ctrl+C it. Sometimes I do get a response, if slow.

---

### Post by kkram13 on 2008-06-17
Hm. So I followed the 'sticky' instructions on how to manually configure the card. That seems to work - at the end of the process I have an ip address as revealed by ifconfig. Doing a ping reveals nothing, however: 100% packet loss. Very much bummed by this. Any thoughts would be much appreciated.

Mark

---

### Post by kkram13 on 2008-06-18
Well, in case anyone is reading this...

Decided to boot using the live-CD and then the linksys dongle worked. So I looked at /etc/network/interfaces, /etc/rc.local and /etc/modprobe.d/blacklist and compared those to what they were when I booted off my hard drive. Reboot using the hard drive, uninstalled ndiswrapper and reverted the three files. Reboot again - now the linksys wasn't recognised at all. I then played around with modprobe and saw there was an "rt73usb" module. Then when I typed sudo modprobe rt73usb to load it - the lights came on, the swirly balls starting doing their thing and hey presto, I'm connected!

Now I need to figure out how to make this module load automatically at boot (and if I could find out why it disappeared, that would be even better). Tried editing /etc/modules, we'll see if that works.

Mark

---

