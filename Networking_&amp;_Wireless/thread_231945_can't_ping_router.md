---
title: "can't ping router"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by malcmacdod on 2006-08-08
****Hi, I've installed a Linksys WPC54GX (Airgo Networks chipset) card with ndiswrapper using its native driver no probs.  Using kwifimanager i cand see that I've got full signal strength but the card can't ping the router - it doesn't find the ip address using DHCP, now i'm stumped!!  Anyone got any ideas as to how i can get my card to talk to my router using DHCP?....been up all night with this and it ain'y good for my beauty sleep :D

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     Auto  ESSID:"calum"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:61:EE:4B
          Bit Rate:108 Mb/s
          Power Management:off
          Link Quality:100/100  Signal level:-58 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

calum@calum-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:F5:39:06:70
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe39:670/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31809 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26080668 (24.8 MiB)  TX bytes:1951439 (1.8 MiB)
          Interrupt:11 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1824 (1.7 KiB)  TX bytes:1824 (1.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:13:10:AE:DF:01
          inet6 addr: fe80::213:10ff:feae:df01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7066 (6.9 KiB)  TX bytes:30852 (30.1 KiB)
          Interrupt:5 Memory:42000000-42080000

---

### Post by malcmacdod on 2006-08-08
shameless bump

---

### Post by alecjw on 2006-08-08
Check that the router doesn't have ping blocking swiched off.

---

### Post by malcmacdod on 2006-08-08
yeh checked router and found MAC filter was on changed that to "any" but still having no joy. The problem seems to be that the card can't pick up an ip address although its powered up and recieving 100% signal.  I'm a noob to linux and really want to give this a go but i am truely stumped!! Any help appreciated ;)

---

