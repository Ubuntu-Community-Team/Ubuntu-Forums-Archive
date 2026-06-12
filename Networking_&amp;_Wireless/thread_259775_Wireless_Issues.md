---
title: "Wireless Issues"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by Echo35 on 2006-09-17
I just recently custom built myself a rig and ran into a problem in Linux. I can't seem to be able to use my WiFi card! It's a Linksys WMP54G, and I know it works because I've tested it on Winsuck just fine. Ubuntu detects it, but it won't connect to my Wireless Network, nor will it stay on once I hit ok in the network manager (this is on Dapper Drake 6.06.1 X64 by the way). Does anyone know what to do?

---

### Post by djillucid on 2006-09-17
I am having problems with my linksys wireless card as well and running the x64 ubuntu. If you find aything out let me know. I am on the card win windows right now, but when I switch to ubuntu, I get nothing. Did you go through all the ndiswapper steps??

---

### Post by Echo35 on 2006-09-17
Yeah. But I'll try it again.

---

### Post by Echo35 on 2006-09-20
[EMAIL="echo35@Dream-Blade:~$"]echo35@Dream-Blade:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11b/g  ESSID: "Trace"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
sit0      no wireless extensions.
[EMAIL="echo35@Dream-Blade:~$"]echo35@Dream-Blade:~$[/EMAIL] sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:06:25:3b:fd:f8
Sending on   LPF/eth1/00:06:25:3b:fd:f8
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

 
Sorry if that's broken up, but that's the output I got. It seems as if my card can't detect the Access Point. Does anyone have a suggestion?

---

### Post by romedog on 2006-09-20
Have you attempted to use the mac address filter on the linksys and hard code an ip on the ubuntu server since dhcp broadcast could possibly be a security issue.  If you prefer to do the broadcast that is fine, but I would enable mac filter.

---

### Post by Echo35 on 2006-09-20
No. I havent tried that yet. For some more information, the Ubuntu server is a Desktop PC running Dapper Drake 6.06 in an adjacent room that is connected to a high speed connection, with a D-Link router broadcasting the signal. I'll try your suggestion now.

---

### Post by Echo35 on 2006-09-20
Nope, that didn't work either. I checked the logs of the AP after enabling the WiFi card on the remote machine, and the AP didn't even detect the remote machine! It seems as if they arent even talking to each other. What the heck is going on? ](*,)

---

### Post by Echo35 on 2006-09-21
Maybe if I install windows and try connecting on that to get the mac address, that might work...

---

### Post by NetworkGuy on 2006-09-21
Have you searched for a howto on setting up a Broadcom 4306 wifi card in the forums?  I believe the default kernel does not work 100% and creates problems like you are seeing.

I believe you need to use NDISWrapper to get the card working correctly in 6.06

---

### Post by Echo35 on 2006-09-21
That's the weird thing though. I did use ndiswrapper and it's working correctly. I found a how-to that did a slightly different procedure than the other one I tried, so I'm going to attempt that one.

---

### Post by Echo35 on 2006-09-22
](*,) :: Sigh :: This is really starting to annoy me. I might just try returning it to New Egg, but I'm not sure if you can return *working* products.

---

