---
title: "Netgear Wireless Help - Going Insane Here...."
date: 2005-07-07
forum: Networking &amp; Wireless
---

### Post by debaser13 on 2005-07-07
Hello everyone,

Well, I have spend just too much damn time trying to figure this out...I have gone through nearly every motion mentioned on this forum about ndiswrapper and wireless connections.  Nothing seems to help.  Whenever I put in:

*ndiswrapper -l*

I get:* Invalid Driver!*

However, my wlan0 using Netgear WG311v2 PCI card will connect using a static IP address with a local free company.  I can get signal strength (using KwifiManager or Gnome Network Connection) and a transfer rate.  However, when I turn off my eth1, Firefox will just sit there and then say, "www.yahoo.com cannot be found, please check connection" or whatever...could this be because the local company uses software called "NoCatAuth" which "uses your web browser to authenticate to the node."  When I used XP on a friend's laptop, it would just redirect my browser to their terms and conditions, I would click yes and surf.

Here is my iwconfig output:

[I]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g/b+  ESSID:"www.personaltelco.net"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.[/I]

Here is my ifconfig output:

[I]eth1      Link encap:Ethernet  HWaddr 00:05:5D:52:E3:AE
          inet addr:67.168.199.85  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::205:5dff:fe52:e3ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:206782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:39207306 (37.3 MiB)  TX bytes:2127381 (2.0 MiB)
          Interrupt:19 Base address:0x9000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2737088 (2.6 MiB)  TX bytes:2737088 (2.6 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:4E:D8:5E
          inet addr:10.11.38.206  Bcast:10.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe4e:d85e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1134 (1.1 KiB)
          Interrupt:18
[/I]

Anyway, I am going nuts here...just can't seem to get this to work...I am fairly new to all this and although I can honestly say most everything else I have been able to work out, this one has stumped me.  Any help would be greatly appreciated.  Thanks.

Carl

 ](*,)

---

