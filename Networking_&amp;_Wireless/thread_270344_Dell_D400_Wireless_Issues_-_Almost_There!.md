---
title: "Dell D400 Wireless Issues - Almost There!"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by iantjones on 2006-10-03
Thanks to several posts here I am almost up and running but I am having trouble completing the install.

I used the Dell drivers and ndiswrapper and when I run ndiswrapper -l I get:
bcmwl5          driver present, hardware present

I added ndiswrapper to /etc/modules and my wireless connection is detected by network manager. FYI - my hardwired connection works fine.

**Here is ifconfig:**
eth0      Link encap:Ethernet  HWaddr 00:0D:56:6E:33:BC
          inet addr:192.168.10.104  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe6e:33bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2065883 (1.9 MiB)  TX bytes:374464 (365.6 KiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:6C:5E:A2
          inet6 addr: fe80::290:4bff:fe6c:5ea2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:fcfec000-fcfee000

When I attempt to add my access point using "connect to other wireless network..." it won't connect. I turned off security and enabled broadcast so those are not issues.

I don't know much about Linux - I am a semi-noob - but there must be a configuration issue somewhere that I am missing.

**Here is /etc/network/interfaces/:**
auto lo
iface lo inet loopback

I took everything else out based on instructions I found here.

**Here is iwconfig:**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11a  ESSID:off/any  Nickname:"Michigan"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Encryption key:off
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

That is what I know and where I am at...any suggestions are appreciated. If you need more configuration information please let me know.

Many thanks,
Ian

---

