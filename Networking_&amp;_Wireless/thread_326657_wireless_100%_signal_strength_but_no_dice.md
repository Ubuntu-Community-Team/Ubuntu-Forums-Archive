---
title: "wireless 100% signal strength but no dice"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by poadshaw on 2006-12-27
hi all, love ubuntu!

I was using 6.06 on my laptop, and tried to upgrade to 6.10 screwed up, so i made a live cd of 6.10 and all is well... except wirless is not working. I have signal strength but cannot ping or visit web pages.

I'm using PRO/Wireless 2200BG Network device. default driver with 6.10

here's some info I pulled off the terminal:

$ iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

eth1 Scan completed :
Cell 01 - Address: 00:12:880:1C:E1
ESSID:"<hidden>"
Protocol:IEEE 802.11bg
Mode:Master
Channel:6
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
22 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s; 24 Mb/s
36 Mb/s; 48 Mb/s; 54 Mb/s
Quality=96/100 Signal level=-29 dBm
Extra: Last beacon: 1824ms ago

sit0 Interface doesn't support scanning.


$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:0F:B0:A6:2B:F5
inet addr:192.168.1.64 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::20f:b0ff:fea6:2bf5/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:122997 errors:0 dropped:0 overruns:0 frame:0
TX packets:67399 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:173518359 (165.4 MiB) TX bytes:5526789 (5.2 MiB)
Interrupt:177

eth1 Link encap:Ethernet HWaddr 00:13:CE:A3:3E:CF
inet addr:192.168.1.67 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::213:ceff:fea3:3ecf/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:883 errors:24 dropped:24 overruns:0 frame:0
TX packets:103 errors:0 dropped:0 overruns:0 carrier:1
collisions:0 txqueuelen:1000
RX bytes:72680 (70.9 KiB) TX bytes:13416 (13.1 KiB)
Interrupt:50 Base address:0x2000 Memory:b8006000-b8006fff

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:270 errors:0 dropped:0 overruns:0 frame:0
TX packets:270 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:26877 (26.2 KiB) TX bytes:26877 (26.2 KiB)



under General tab in my Connection Properties: eth1 (my wireless connection) I have:
Name: eth1
Status: Idle / Receiving / Sending (switches between these)
Activity
Recieved: 1148 packets (82.5 Kb) (always increasing in value)
Sent: 133 packets (14.1 Kb) (also increasing in value)
Signal Strength (100%)


I am not able to ping anything or visit websites. If i don't have my essid or my webkey in correctly I get a signal strength of 0%, but then I change it back and it jumps to 100% but still no internet.](*,) 

I have been using Linux for 1 month so feel free to explain things as if i'm a 3 year old
Thanks in advance for any suggestions.

---

### Post by Floppyjoe on 2006-12-28
What happens when you take down the wep encryption on the router and enter:
```
sudo dhclient eth1
```

---

