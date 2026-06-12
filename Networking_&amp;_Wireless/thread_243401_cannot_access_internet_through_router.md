---
title: "cannot access internet through router"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by trixma on 2006-08-25
hey guys,
I have been using wireless at university for ages now using my ubuntu dell 6000 laptop and just decided to create my how wireless network at home. I brought a elements wireless G router and connected my desktop computer via ethernet cable and connected my optusnet adsl modem to the router. I am having problems with my laptop it is only able to connect to the router but not the internet. My desktop can access the router and the internet. When I use the ethernet cable to connect my laptop with the router I have internet, but when I go back to wireless it doesnt work. I am able to see the router web GUI settings from my router. The settings I have are shown below

resolve.conf
nameserver 192.168.1.254

ifconfig
eth1      Link encap:Ethernet  HWaddr 00:12:F0:8F:5B:BE
          inet6 addr: fe80::212:f0ff:fe8f:5bbe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1238 errors:0 dropped:10 overruns:0 frame:0
          TX packets:2585 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:200992 (196.2 KiB)  TX bytes:37020 (36.1 KiB)
          Interrupt:17 Base address:0x2000 Memory:dfdfd000-dfdfdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8463 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:767361 (749.3 KiB)  TX bytes:767361 (749.3 KiB)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"HAWKER"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:08:A1:A0:FD:EA
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/100  Signal level=-29 dBm  Noise level=-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:10

sit0      no wireless extensions.


Does anyone have any ideas, why I cannot access the internet wirelessly thanks.
Trixma

---

### Post by trixma on 2006-08-25
I have worked out whats wrong, but it still gets me no where. I have set my windows XP desktop to obtain the ip address automatically and I have set my laptop wireless to do the same (DHCP), but some how both are using the same ip address, which i thought was impossible as they get one auto assigned. Can someone tell me how i can get around this? Or how to give my computers an ip address (i.e static)

---

### Post by peanut butter on 2006-08-25
giving a computer a static address is not too hard. all you must do is go to System>Administration>Networking
hignlight the wireless or ethernet interface and click properties, and fill in the values.

---

