---
title: "trouble accessing wireless network using wep"
date: 2005-05-31
forum: Networking &amp; Wireless
---

### Post by ssck on 2005-05-31
hi all,

i have the following settings on the various checks that i did on my wireless card.i am using wep in the office.however, i am not able to ping the office access point.

ifconfig settings:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:168 (168.0 b)  TX bytes:168 (168.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0E:9B:9B:C5:13
          inet addr:192.168.2.242  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:9bff:fe9b:c513/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:48901 (47.7 KiB)  TX bytes:3876 (3.7 KiB)
          Memory:e0203000-e02037ff


iwconfig settings :

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Hex3"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:04:E2:66:C7:70
          Bit Rate:11 Mb/s
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-48 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:2   Missed beacon:0

sit0      no wireless extensions.


dhclient settings :

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/wlan0/00:0e:9b:9b:c5:13
Sending on   LPF/wlan0/00:0e:9b:9b:c5:13
Listening on LPF/eth0/00:c0:9f:81:a4:4f
Sending on   LPF/eth0/00:c0:9f:81:a4:4f
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 3
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.242 -- renewal in 1749 seconds.


ping settings :

PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.2.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3998ms

what could be the problem ? is there a problem with wep using ndiswrapper ? i am using ipn2220 windows driver provided by acer for my acer travelmate 2300 notebook.

anyone can help ?

---

### Post by toddncl on 2005-05-31
I had a rouge pipe in my ndiswrapper setup, i followed these instructions and it worked right away:

(from [http://ubuntuforums.org/showthread.php?t=30680&highlight=prism54](http://ubuntuforums.org/showthread.php?t=30680&highlight=prism54))

ndiswrapper conf generation problem: This was the main problem I had. Apparently ndiswrapper has an error in compiling the conf files required to use the wireless card. To solve this you need to edit the conf file and remove the line with a single | symbol on it as this causes problems when you try to modprobe ndiswrapper. Just look through the conf files in the directory:
Code:
/etc/ndiswrapper/<drivername>


REMOVE THE ROGUE PIPE AND THEN:
Code:
modprobe ndiswrapper


and the drivers should work fine. Then you can use whatever wireless configuration method you need (Gnome GUI or iwconfig in a terminal) and you should be okay.

---

### Post by ssck on 2005-05-31
[QUOTE=toddncl]I had a rouge pipe in my ndiswrapper setup, i followed these instructions and it worked right away:

(from [http://ubuntuforums.org/showthread.php?t=30680&highlight=prism54](http://ubuntuforums.org/showthread.php?t=30680&highlight=prism54))

ndiswrapper conf generation problem: This was the main problem I had. Apparently ndiswrapper has an error in compiling the conf files required to use the wireless card. To solve this you need to edit the conf file and remove the line with a single | symbol on it as this causes problems when you try to modprobe ndiswrapper. Just look through the conf files in the directory:
Code:
/etc/ndiswrapper/<drivername>


REMOVE THE ROGUE PIPE AND THEN:
Code:
modprobe ndiswrapper


and the drivers should work fine. Then you can use whatever wireless configuration method you need (Gnome GUI or iwconfig in a terminal) and you should be okay.[/QUOTE]


Actually the wireless works fine if it does not have WEP.I can get connected with no problems at all.Is this solution related to WEP ?

---

