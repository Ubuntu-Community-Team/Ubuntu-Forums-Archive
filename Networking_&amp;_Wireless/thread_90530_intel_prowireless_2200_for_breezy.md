---
title: "intel pro/wireless 2200 for breezy"
date: 2005-11-15
forum: Networking &amp; Wireless
---

### Post by aum11 on 2005-11-15
Hello all,

can anyone please point me to the place for the instructions for setting up the 2200 under Breezy.  Is it the same as for Hoary?

Currently wireless seems to be okay...fell strength signal...but no downloads happening.

Any suggestions.  I am very new to all of this.
Thanks.

---

### Post by Lambert on 2005-11-15
When you type ifconfig, do you see an ip address assigned to the device? Should be second line under your wireless device inet address: xxx.xxx.x.x

Can you ping your router?
Can you ping an external site with their ip address
Can you ping an external site with their common name.

---

### Post by aum11 on 2005-11-15
ifconfig gives:
eth1      Link encap:Ethernet  HWaddr 00:12:F0:1E:B7:A1
          inet addr:192.168.15.100  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe1e:b7a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39 errors:0 dropped:11 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:632 (632.0 b)  TX bytes:1032 (1.0 KiB)
          Interrupt:17 Base address:0x6000 Memory:dfcfd000-dfcfdfff


:~$ ping 192.168.15.100
PING 192.168.15.100 (192.168.15.100) 56(84) bytes of data.
64 bytes from 192.168.15.100: icmp_seq=1 ttl=64 time=0.061 ms
64 bytes from 192.168.15.100: icmp_seq=2 ttl=64 time=0.063 ms
64 bytes from 192.168.15.100: icmp_seq=3 ttl=64 time=0.058 ms
64 bytes from 192.168.15.100: icmp_seq=4 ttl=64 time=0.060 ms
64 bytes from 192.168.15.100: icmp_seq=5 ttl=64 time=0.060 ms
64 bytes from 192.168.15.100:

:~$ ping [http://www.dailyrotation.com](http://www.dailyrotation.com)
ping: unknown host [http://www.dailyrotation.com](http://www.dailyrotation.com)

---

### Post by Lambert on 2005-11-15
192.168.15.100 is the ip address of the card and you pinged that ok.

Can you ping the router. usually something like 192.168.0.1

What does iwconfig show?

---

### Post by aum11 on 2005-11-16
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:4B:6B:B7
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=-27 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:19   Missed beacon:0

sit0      no wireless extensions.

---

### Post by aum11 on 2005-11-16
Wireless is now working perfectly.

All I did was to make sure ethernet was turned off, and that the wireless button ( fn f2) was turned on under Windows, and left on.

Thank You all.

---

