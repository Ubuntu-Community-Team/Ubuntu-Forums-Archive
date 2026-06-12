---
title: "Wlan and Lan"
date: 2005-07-09
forum: Networking &amp; Wireless
---

### Post by rathel on 2005-07-09
I have a WLAN card and a LAN card, I can't access the computers on the switch that's conencted to the LAN card but the Wireless card works fine.
Any Suggestions on how to get connected to the computers on the LAN one?

---

### Post by kleeman on 2005-07-09
Bring the wireless interface down with ifconfig and then bring the lan interface up with ifconfig and then dhclient. Let us assume your wireless interface is called wlan0 and your lan interface is called eth0 then do the following:

sudo ifconfig wlan0 down
sudo ifconfig eth0 up
sudo dhclient eth0

Of course this assumes you know what your interfaces are called and also that you are using dhcp for your lan.....

---

### Post by rathel on 2005-07-09
Okay I tried that didn't work, and I'm not using DHCP

---

### Post by arosct on 2005-07-09
Try network-admin.

---

### Post by kleeman on 2005-07-09
OK we need more information: What do the following commands give?

ifconfig

dmesg | grep eth

dmesg | grep wlan

---

### Post by rathel on 2005-07-09
ifconfig:

ath0      Link encap:Ethernet  HWaddr 00:0E:9B:24:6E:B6
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:9bff:fe24:6eb6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1307096 errors:772 dropped:0 overruns:0 frame:772
          TX packets:1658588 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:511198688 (487.5 MiB)  TX bytes:692145468 (660.0 MiB)
          Interrupt:11 Memory:dcb80000-dcb90000

eth0      Link encap:Ethernet  HWaddr 08:00:46:E8:3A:BB
          inet addr:10.0.0.102  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::a00:46ff:fee8:3abb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:29770 (29.0 KiB)  TX bytes:4446 (4.3 KiB)
          Interrupt:3 Base address:0x9000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:744085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:744085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:120365064 (114.7 MiB)  TX bytes:120365064 (114.7 MiB)

dmesg | grep eth:

displays nothing

dmesg | grep ath:

Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=62.117.187.232 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=106 ID=16951 PROTO=UDP SPT=9882 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=83.43.71.201 DST=192.168.0.102 LEN=48 TOS=0x00 PREC=0x20 TTL=100 ID=31148 DF PROTO=TCP SPT=1339 DPT=3120 WINDOW=65535 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=83.135.88.246 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=109 ID=65109 PROTO=UDP SPT=4662 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=85.53.94.155 DST=192.168.0.102 LEN=48 TOS=0x00 PREC=0x20 TTL=108 ID=8686 DF PROTO=TCP SPT=3914 DPT=3120 WINDOW=65535 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=80.203.59.164 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=104 ID=15678 PROTO=UDP SPT=5391 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=212.183.248.161 DST=192.168.0.102 LEN=48 TOS=0x00 PREC=0x20 TTL=106 ID=12068 DF PROTO=TCP SPT=4104 DPT=3120 WINDOW=16384 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.235.120.245 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=109 ID=61899 PROTO=UDP SPT=4043 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=80.182.19.114 DST=192.168.0.102 LEN=48 TOS=0x00 PREC=0x20 TTL=104 ID=44527 DF PROTO=TCP SPT=1238 DPT=3120 WINDOW=65535 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.141.247.75 DST=192.168.0.102 LEN=52 TOS=0x00 PREC=0x20 TTL=113 ID=63781 DF PROTO=TCP SPT=1285 DPT=3120 WINDOW=32767 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=172.187.42.115 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=106 ID=11755 PROTO=UDP SPT=5429 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=82.66.88.51 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=107 ID=35755 PROTO=UDP SPT=4395 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=219.74.235.51 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=109 ID=64101 PROTO=UDP SPT=6093 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=220.80.85.26 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=106 ID=55832 PROTO=UDP SPT=5978 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=80.102.118.254 DST=192.168.0.102 LEN=48 TOS=0x00 PREC=0x20 TTL=109 ID=45776 DF PROTO=TCP SPT=3926 DPT=3120 WINDOW=65535 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.136.228.11 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=112 ID=13719 PROTO=UDP SPT=5099 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=81.173.160.178 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=44 ID=39762 DF PROTO=UDP SPT=42785 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=71.106.114.239 DST=192.168.0.102 LEN=86 TOS=0x00 PREC=0x20 TTL=107 ID=18631 PROTO=UDP SPT=45452 DPT=8602 LEN=66
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=83.32.36.43 DST=192.168.0.102 LEN=52 TOS=0x00 PREC=0x20 TTL=39 ID=21926 DF PROTO=TCP SPT=19969 DPT=3120 WINDOW=32768 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=82.217.175.206 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=24 ID=5167 PROTO=UDP SPT=7907 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.174.113.9 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=48 ID=65412 PROTO=UDP SPT=4662 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=221.149.162.1 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=109 ID=2165 PROTO=UDP SPT=12431 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.120.208.143 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=41 ID=49855 PROTO=UDP SPT=5050 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.148.5.208 DST=192.168.0.102 LEN=48 TOS=0x00 PREC=0x20 TTL=111 ID=30486 DF PROTO=TCP SPT=1610 DPT=3120 WINDOW=16384 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=222.238.197.190 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=109 ID=38115 PROTO=UDP SPT=11179 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=172.176.9.249 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=107 ID=21774 PROTO=UDP SPT=3272 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=81.51.131.149 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=108 ID=13664 PROTO=UDP SPT=8363 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=80.182.63.205 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=39 ID=43595 DF PROTO=UDP SPT=10091 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=200.127.63.8 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=105 ID=53716 PROTO=UDP SPT=10128 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=66.130.253.77 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=107 ID=13122 PROTO=UDP SPT=9805 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=80.146.75.119 DST=192.168.0.102 LEN=48 TOS=0x00 PREC=0x20 TTL=113 ID=47352 DF PROTO=TCP SPT=3521 DPT=3120 WINDOW=16384 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=65.100.213.30 DST=192.168.0.102 LEN=48 TOS=0x00 PREC=0x20 TTL=110 ID=48531 DF PROTO=TCP SPT=4701 DPT=3120 WINDOW=65535 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=82.224.180.144 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=42 ID=48962 DF PROTO=UDP SPT=10712 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=82.159.20.252 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=105 ID=26003 PROTO=UDP SPT=7450 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=81.211.212.156 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=107 ID=514 PROTO=UDP SPT=4877 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=71.99.156.99 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=108 ID=33979 PROTO=UDP SPT=3010 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=81.154.153.235 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=101 ID=57587 PROTO=UDP SPT=27879 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=81.38.129.165 DST=192.168.0.102 LEN=52 TOS=0x00 PREC=0x20 TTL=103 ID=18181 DF PROTO=TCP SPT=28774 DPT=3120 WINDOW=32767 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=67.164.172.34 DST=192.168.0.102 LEN=44 TOS=0x00 PREC=0x00 TTL=63 ID=55646 DF PROTO=TCP SPT=61723 DPT=3120 WINDOW=5840 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=220.245.216.9 DST=192.168.0.102 LEN=86 TOS=0x00 PREC=0x20 TTL=113 ID=58077 PROTO=UDP SPT=6881 DPT=8602 LEN=66
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=24.28.5.160 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=108 ID=8341 PROTO=UDP SPT=7892 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=71.99.191.97 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=108 ID=18875 PROTO=UDP SPT=3014 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=172.177.225.130 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=107 ID=42587 PROTO=UDP SPT=6452 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=80.170.26.22 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=109 ID=1983 PROTO=UDP SPT=8999 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=80.132.152.114 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=112 ID=42819 PROTO=UDP SPT=60125 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=193.171.130.187 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=104 ID=1653 PROTO=UDP SPT=63953 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=69.134.27.162 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=106 ID=3471 PROTO=UDP SPT=8381 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=81.251.193.81 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=109 ID=37315 PROTO=UDP SPT=8616 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=200.97.102.82 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=110 ID=6413 PROTO=UDP SPT=8747 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.81.230.115 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=106 ID=34288 PROTO=UDP SPT=49086 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=81.202.175.13 DST=192.168.0.102 LEN=65 TOS=0x00 PREC=0x20 TTL=106 ID=22503 PROTO=UDP SPT=6881 DPT=8602 LEN=45
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=81.202.175.13 DST=192.168.0.102 LEN=86 TOS=0x00 PREC=0x20 TTL=106 ID=22515 PROTO=UDP SPT=6881 DPT=8602 LEN=66
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=220.74.115.82 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=111 ID=3266 PROTO=UDP SPT=10946 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=82.238.25.44 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=44 ID=51609 PROTO=UDP SPT=6260 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=24.20.54.50 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=113 ID=34359 PROTO=UDP SPT=8769 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=195.5.61.66 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=43 ID=37705 PROTO=UDP SPT=5425 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=195.150.64.2 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=103 ID=20514 PROTO=UDP SPT=5272 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.163.11.97 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=48 ID=2879 DF PROTO=UDP SPT=61001 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=62.0.100.148 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=108 ID=13207 PROTO=UDP SPT=11249 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.100.174.214 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=103 ID=36209 PROTO=UDP SPT=3210 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=80.41.221.160 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=107 ID=28653 PROTO=UDP SPT=5491 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=219.84.12.116 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=107 ID=8041 PROTO=UDP SPT=11581 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=216.6.159.215 DST=192.168.0.102 LEN=86 TOS=0x00 PREC=0x20 TTL=14 ID=45950 PROTO=UDP SPT=6881 DPT=8602 LEN=66
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=82.57.132.34 DST=192.168.0.102 LEN=86 TOS=0x00 PREC=0x20 TTL=102 ID=50265 PROTO=UDP SPT=6881 DPT=8602 LEN=66
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=62.168.109.2 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=42 ID=18397 DF PROTO=UDP SPT=19825 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=24.50.168.152 DST=192.168.0.102 LEN=48 TOS=0x00 PREC=0x20 TTL=107 ID=7007 PROTO=TCP SPT=2623 DPT=3120 WINDOW=8192 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.183.199.206 DST=192.168.0.102 LEN=52 TOS=0x00 PREC=0x20 TTL=111 ID=56322 PROTO=TCP SPT=32813 DPT=3120 WINDOW=65535 RES=0x00 SYN URGP=0
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=222.101.189.59 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=105 ID=57516 PROTO=UDP SPT=10988 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=81.215.192.231 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=109 ID=5588 PROTO=UDP SPT=5936 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=213.60.144.29 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=45 ID=18229 PROTO=UDP SPT=53483 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.157.59.89 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=112 ID=18611 PROTO=UDP SPT=11404 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=211.195.168.213 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=105 ID=47733 PROTO=UDP SPT=3101 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=195.22.168.153 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=102 ID=64707 PROTO=UDP SPT=4642 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=193.253.235.238 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=109 ID=17132 PROTO=UDP SPT=5803 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.122.214.95 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=104 ID=56693 PROTO=UDP SPT=8885 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=83.65.246.11 DST=192.168.0.102 LEN=86 TOS=0x00 PREC=0x20 TTL=107 ID=22642 PROTO=UDP SPT=58881 DPT=8602 LEN=66
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=211.193.33.74 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=108 ID=51808 PROTO=UDP SPT=4817 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=82.64.242.250 DST=192.168.0.102 LEN=53 TOS=0x00 PREC=0x20 TTL=109 ID=16518 PROTO=UDP SPT=7630 DPT=3130 LEN=33
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=80.59.79.97 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=102 ID=49581 PROTO=UDP SPT=3814 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=83.177.254.93 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=109 ID=52217 PROTO=UDP SPT=8642 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=140.116.164.222 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=39 ID=0 DF PROTO=UDP SPT=2188 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=200.165.232.165 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=112 ID=12713 PROTO=UDP SPT=12570 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=213.60.62.248 DST=192.168.0.102 LEN=47 TOS=0x02 PREC=0x20 TTL=111 ID=35970 PROTO=UDP SPT=5624 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.146.71.93 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=112 ID=2787 PROTO=UDP SPT=5332 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=219.253.180.34 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=105 ID=41042 PROTO=UDP SPT=4495 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=84.10.166.173 DST=192.168.0.102 LEN=47 TOS=0x00 PREC=0x20 TTL=107 ID=33781 PROTO=UDP SPT=9105 DPT=3130 LEN=27
Inbound IN=ath0 OUT= MAC=00:0e:9b:24:6e:b6:00:0d:88:86:7a:db:08:00 SRC=66.222.37.63 DST=192.168.0.102 LEN=86 TOS=0x00 PREC=0x20 TTL=108 ID=23010 PROTO=UDP SPT=6881 DPT=8602 LEN=66

---

### Post by kleeman on 2005-07-09
OK so your wireless interface is ath0 (madwifi driver) and your wired interface appears to have been recognized by ubuntu and is eth0. So to bring down the wireless interface to stop it interfering with eth0 execute

sudo ifconfig ath0 down

Now if you are not using dhcp what is your ip address and gateway address? If you don't know tell us how you are connected to the internet... 

Once you know this goto the gui for networking (system-administration-network) and enter the details for the eth0 interface and then activate it....

---

### Post by rathel on 2005-07-09
my lan ip is 10.0.0.102 and how I connect to the internet is via wireless. the lan is connected to a switch in my room and the wireless router is in another room. I've tried setting it up in the network-admin tool, but I still can't get connected to the other computers on the lan.

---

### Post by kleeman on 2005-07-09
I'm still a bit confused by your setup: Your wired ethernet card is connected to a switch and this switch is then connected (by cable?) to the wireless router. Correct? And then the wireless router is connected to a cable modem? How do you know that your wired ip should be 10.0.0.102?

---

### Post by t2kburl on 2005-07-09
thats a whole different ballgame ...
accessing other compuers on the network is done with samba (to connect to w$ systems) or NFS to connect to other Linux systems
If these are all ultimately connected to the same router as your wireless AP, then you need to search for the proper configs for NFS and/or samba

unless I'm completely misunderstanding what you are trying to do .....   I've had a long day

---

### Post by rathel on 2005-07-09
Let me try to explain better.

My laptop has cable comming out to a switch, which is connected to other computers, then my Wireless Card is connecting to a Wireless Router in another room. No wires going to router.
Where I'm having my problem is trying to see the computers on the wired end.

---

### Post by kleeman on 2005-07-09
OK so how do you know what your ip address is? One way to find out the other details you need (the gateway address and also the mask) is to look on one of the other computers on your lan. Are these running Windows? btw you need to provide all these  details (ip address, gateway address, mask) to get any connection at all nfs and samba can be set up AFTER this is done not before....

---

### Post by rathel on 2005-07-09
Okay, my ip address can be anything I want I just chose 10.*.*.* because it's simple. My subnet mask is 255.0.0.0 and the gateway? I didn't think I needed one, and what's going to be the gateway? it's not going out to the internet or anything. And the other computers are Windows. It all worked fine when I'm on Windows.

---

### Post by kleeman on 2005-07-09
The gateway is the lan ip address of the router that connects your lan to the cable modem (or dsl router). Maybe it is right already I don't know but you should check to make sure on your windows machines. You need it to tell your Ubuntu box how to get out to the internet. BTW can you ping your windows machines? 

ping 10.*.*.* (windows ip address)

---

### Post by rathel on 2005-07-09
```
rathel@ubuntu:~$ ping -I eth0 10.0.0.100
PING 10.0.0.100 (10.0.0.100) from 10.0.0.102 eth0: 56(84) bytes of data.
ping: sendmsg: Operation not permitted
```

Nope can't Ping. Ubuntu is already on the inernet through the ath0 Wireless.

---

### Post by kleeman on 2005-07-09
What happens with the ping if you bring down the ath0 (wireless) connection with
sudo ifconfig ath0 down

---

### Post by rathel on 2005-07-09
hmm... samething happens

---

### Post by kleeman on 2005-07-10
It sounds like you have a fairly basic networking problem (the driver looks fine and eth0 is coming up apparently fine as well). To fix it edit /etc/network/interfaces and comment out  

auto ath0

(change it to #auto ath0)

reboot and if that doesn't help

then follow this troubleshooter:

[http://www.ubuntuforums.org/showthread.php?t=25557](http://www.ubuntuforums.org/showthread.php?t=25557)

It's a bit hard to help remotely on problems like this as they are usually very specific to your setup. Also this guide should get you up to speed with linux networking which I find is a very useful skill.

---

### Post by rathel on 2005-07-10
That didn't work, I also just recently tried, pluging the NIC into the router and let it configure dhcp with my wireless disabled, and that only got me an ip and such, but I couldn't ping anything... Maybe Ubuntu isn't loading my NIC correctly or something?

---

### Post by kleeman on 2005-07-10
OK lets go through the troubleshooter:
First disable the wireless card and connect via dhcp to the router
Now post the output of the following:

1)   arp -a

2)   netstat -nr

3) ping 127.0.0.1

4) ping localhost

Also what is your wired nic and what is the driver?

---

### Post by rathel on 2005-07-10
thanks for taking the time to help me :)

root@ubuntu:/home/rathel # dhclient eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/08:00:46:e8:3a:bb
Sending on   LPF/eth0/08:00:46:e8:3a:bb
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.100 -- renewal in 297124 seconds.

root@ubuntu:/home/rathel # arp -a
? (192.168.0.1) at <incomplete> on ath0

root@ubuntu:/home/rathel # netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 ath0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 ath0

root@ubuntu:/home/rathel # ping -c 1 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.088 ms

--- 127.0.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.088/0.088/0.088/0.000 ms
root@ubuntu:/home/rathel # ping -c 1 localhost
PING localhost.localdomain (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=1 ttl=64 time=0.146 ms
--- localhost.localdomain ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.146/0.146/0.146/0.000 ms

0000:00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by kleeman on 2005-07-10
Well that's strange it appears as if the wireless interface ath0 is still operational. Did you bring it down using
sudo ifconfig ath0 down
before doing the tests?

---

### Post by rathel on 2005-07-11
yeah, when I tried arp -a again a little after that, nothing showed up.

---

### Post by kleeman on 2005-07-11
If nothing is showing up for eth0 in arp -a then the driver has not registered the interface with the kernel properly possibly due to interference from the wireless hardware which seems to be getting preference. What does
sudo lsmod | grep 8139

give? (this is trying to see if the wired driver is really loaded or not)

---

### Post by rathel on 2005-07-11
8139cp                 19200  0
8139too                24320  0
mii                     4736  2 8139cp,8139too

---

### Post by kleeman on 2005-07-11
So your wired modules/drivers are 8139cp and 8139too
Try taking them down and bring them up and see what happens in dmesg

check demsg first then
sudo rmmod 8139cp
sudo rmmod 8139too
sudo modprobe 8139cp
sudo modprobe 8139too

check dmesg again and also see whether arp -a is showing anything

---

### Post by rathel on 2005-07-11
dmesg before:
```

known OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.225.155.151 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38206 DF PROTO=UDP SPT=3130 DPT=19028 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=85.84.49.248 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38207 DF PROTO=UDP SPT=3130 DPT=7712 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.225.155.151 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38208 DF PROTO=UDP SPT=3130 DPT=19028 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=85.84.49.248 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38209 DF PROTO=UDP SPT=3130 DPT=7712 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.225.155.151 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38210 DF PROTO=UDP SPT=3130 DPT=19028 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=85.84.49.248 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38211 DF PROTO=UDP SPT=3130 DPT=7712 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.139.30.121 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38212 DF PROTO=UDP SPT=3130 DPT=3518 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=83.156.58.96 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38213 DF PROTO=UDP SPT=3130 DPT=12767 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=80.141.252.144 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38214 DF PROTO=UDP SPT=3130 DPT=9961 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=142.167.99.178 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38215 DF PROTO=UDP SPT=3130 DPT=12723 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=218.253.173.101 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38216 DF PROTO=UDP SPT=3130 DPT=12602 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=221.166.96.69 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38217 DF PROTO=UDP SPT=3130 DPT=11061 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.1.85.189 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38218 DF PROTO=UDP SPT=3130 DPT=11554 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=83.202.15.164 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38219 DF PROTO=UDP SPT=3130 DPT=4085 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=62.175.34.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38220 DF PROTO=UDP SPT=3130 DPT=6805 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=69.251.11.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38221 DF PROTO=UDP SPT=3130 DPT=12128 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=62.175.34.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38222 DF PROTO=UDP SPT=3130 DPT=6805 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=69.251.11.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38223 DF PROTO=UDP SPT=3130 DPT=12128 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=62.175.34.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38224 DF PROTO=UDP SPT=3130 DPT=6805 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=69.251.11.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38225 DF PROTO=UDP SPT=3130 DPT=12128 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=62.175.34.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38226 DF PROTO=UDP SPT=3130 DPT=6805 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=69.251.11.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38227 DF PROTO=UDP SPT=3130 DPT=12128 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=62.175.34.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38228 DF PROTO=UDP SPT=3130 DPT=6805 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=69.251.11.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38229 DF PROTO=UDP SPT=3130 DPT=12128 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=62.175.34.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38230 DF PROTO=UDP SPT=3130 DPT=6805 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=69.251.11.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38231 DF PROTO=UDP SPT=3130 DPT=12128 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=62.175.34.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38232 DF PROTO=UDP SPT=3130 DPT=6805 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=69.251.11.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38233 DF PROTO=UDP SPT=3130 DPT=12128 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=62.175.34.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38234 DF PROTO=UDP SPT=3130 DPT=6805 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=69.251.11.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38235 DF PROTO=UDP SPT=3130 DPT=12128 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=62.175.34.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38236 DF PROTO=UDP SPT=3130 DPT=6805 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=69.251.11.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38237 DF PROTO=UDP SPT=3130 DPT=12128 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=62.175.34.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38238 DF PROTO=UDP SPT=3130 DPT=6805 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=69.251.11.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38239 DF PROTO=UDP SPT=3130 DPT=12128 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=62.175.34.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38240 DF PROTO=UDP SPT=3130 DPT=6805 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=69.251.11.93 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38241 DF PROTO=UDP SPT=3130 DPT=12128 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=62.175.102.233 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38242 DF PROTO=UDP SPT=3130 DPT=9780 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=80.14.132.170 LEN=47 TOS=0x00 PREC=0x00 TTL=64 ID=38243 DF PROTO=UDP SPT=3130 DPT=4536 LEN=27 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=69.251.188.54 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=25634 DF PROTO=TCP SPT=38452 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.80.44.98 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=23300 DF PROTO=TCP SPT=38453 DPT=6662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.237.253.87 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=46890 DF PROTO=TCP SPT=38454 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.67.143.162 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=12833 DF PROTO=TCP SPT=38455 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=213.156.52.124 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=34510 DF PROTO=TCP SPT=38456 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=81.33.201.34 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=65125 DF PROTO=TCP SPT=38457 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=195.210.247.30 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=26200 DF PROTO=TCP SPT=38458 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=201.129.44.163 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=43443 DF PROTO=TCP SPT=38459 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=151.47.18.201 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=1710 DF PROTO=TCP SPT=38460 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=83.154.15.49 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=34850 DF PROTO=TCP SPT=38461 DPT=8089 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=80.174.88.89 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=21701 DF PROTO=TCP SPT=38515 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=195.116.67.2 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=37816 DF PROTO=TCP SPT=38516 DPT=40003 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=172.188.133.116 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=24813 DF PROTO=TCP SPT=38517 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=80.117.54.212 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=23764 DF PROTO=TCP SPT=38518 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.235.71.38 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=45462 DF PROTO=TCP SPT=38519 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=172.181.106.139 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=2773 DF PROTO=TCP SPT=38520 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=81.34.53.112 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=56261 DF PROTO=TCP SPT=38521 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=201.8.42.56 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=57816 DF PROTO=TCP SPT=38522 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=193.95.239.182 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=32898 DF PROTO=TCP SPT=38523 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.35.110.135 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=50848 DF PROTO=TCP SPT=38524 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.72.45.204 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=5030 DF PROTO=UDP SPT=13209 DPT=6346 LEN=32 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=85.137.19.182 LEN=53 TOS=0x00 PREC=0x00 TTL=64 ID=38244 DF PROTO=UDP SPT=3130 DPT=4885 LEN=33 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=212.179.185.232 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=22266 DF PROTO=TCP SPT=38339 DPT=5662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.51.17.87 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=12171 DF PROTO=TCP SPT=38340 DPT=70 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=83.76.60.183 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=36489 DF PROTO=TCP SPT=38341 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=80.178.194.86 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=19162 DF PROTO=TCP SPT=38342 DPT=6662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=70.104.56.138 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=56360 DF PROTO=TCP SPT=38343 DPT=4661 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=24.232.85.233 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=40970 DF PROTO=TCP SPT=38344 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=84.58.160.80 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=15429 DF PROTO=TCP SPT=38345 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=84.59.69.166 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=56012 DF PROTO=TCP SPT=38346 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=24.56.28.72 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=64163 DF PROTO=TCP SPT=38347 DPT=6555 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=84.222.160.94 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=62666 DF PROTO=TCP SPT=38348 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.169.133.89 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=11301 DF PROTO=TCP SPT=38462 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=84.24.132.58 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=4035 DF PROTO=TCP SPT=38463 DPT=15810 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=200.121.209.183 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=43084 DF PROTO=TCP SPT=38464 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=80.170.72.229 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=5368 DF PROTO=TCP SPT=38465 DPT=4661 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=80.132.178.6 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=8964 DF PROTO=TCP SPT=38466 DPT=5662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=85.64.115.25 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=27077 DF PROTO=TCP SPT=38467 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=193.77.50.145 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=55111 DF PROTO=TCP SPT=38468 DPT=4646 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.52.39.46 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=36575 DF PROTO=TCP SPT=38469 DPT=6346 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=83.196.206.26 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=50067 DF PROTO=TCP SPT=38470 DPT=6346 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=62.57.44.19 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=9414 DF PROTO=TCP SPT=38471 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=84.166.189.92 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=27439 DF PROTO=TCP SPT=38525 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=172.181.226.225 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=41805 DF PROTO=TCP SPT=38526 DPT=1584 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=69.233.214.86 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=52423 DF PROTO=TCP SPT=38527 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=172.182.114.84 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=37109 DF PROTO=TCP SPT=38528 DPT=6346 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=80.229.164.201 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=12250 DF PROTO=TCP SPT=38529 DPT=6346 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=212.235.5.22 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=36977 DF PROTO=TCP SPT=38530 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=84.133.79.155 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=18390 DF PROTO=TCP SPT=38531 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=84.136.246.169 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=4502 DF PROTO=TCP SPT=38532 DPT=4200 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=84.142.220.236 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=52253 DF PROTO=TCP SPT=38533 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=151.47.69.117 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=9881 DF PROTO=TCP SPT=38534 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=203.228.143.238 LEN=53 TOS=0x00 PREC=0x00 TTL=64 ID=38245 DF PROTO=UDP SPT=3130 DPT=10757 LEN=33 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=84.222.63.245 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=46094 DF PROTO=TCP SPT=38349 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=83.192.227.70 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=28682 DF PROTO=TCP SPT=38350 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=83.193.35.203 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=7972 DF PROTO=TCP SPT=38351 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=80.180.81.45 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=28221 DF PROTO=TCP SPT=38352 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.36.27.165 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=30336 DF PROTO=TCP SPT=38353 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.48.228.10 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=29894 DF PROTO=TCP SPT=38354 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=81.249.163.78 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=42303 DF PROTO=TCP SPT=38355 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=201.243.108.86 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=25034 DF PROTO=TCP SPT=38356 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=83.153.91.68 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=62095 DF PROTO=TCP SPT=38357 DPT=4662 WINDOW=5840 RES=0x00 SYN URGP=0 
Unknown OutputIN= OUT=eth0 SRC=192.168.0.100 DST=82.39.168.145 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=30615 DF PROTO=TCP SPT=38358 DPT=4660 WINDOW=5840 RES=0x00 SYN URGP=0 

```

dmesg after:
It was to long to post both so I created this:
[http://pastebin.com/311515](http://pastebin.com/311515)

arp -a:
again nothing.

---

### Post by kleeman on 2005-07-11
The last few lines of dmesg show the driver (8139too) apparently loading OK but the arp -a doesn't look good.  Do you have anything like /proc/net/8139too/eth0 If so
what does 

cat /proc/net/8139too/eth0
show?

What about
sudo ifconfig eth0 up

any output from this?

---

### Post by rathel on 2005-07-11
/proc/net/8139too/eth0
does not exist.

sudo ifconfig eth0 up
no output.

---

### Post by kleeman on 2005-07-12
It sounds awfully like you have either a driver or hardware problem. One thing you could try is another driver:

[http://www.scyld.com/rtl8139.html](http://www.scyld.com/rtl8139.html)

I noticed on this page that there are a number of negative comments made about the driver you are using.

---

### Post by rathel on 2005-07-12
I get errors while compiling:
```

$ gcc -DMODULE -D__KERNEL__ -DEXPORT_SYMTAB -Wall -Wstrict-prototypes -O6 -c pci-scan.c
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/module.h:10,
                 from pci-scan.c:61:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/module.h:10,
                 from pci-scan.c:61:
/usr/include/asm/mpspec.h:8: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:9: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:10: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:12: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:19: error: `MAX_APICS' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: conflicting types for `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:8: error: previous declaration of `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:22: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: conflicting types for `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:12: error: previous declaration of `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:54: error: `MAX_APICS' undeclared here (not in a function)
In file included from /usr/include/asm/smp.h:20,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/module.h:10,
                 from pci-scan.c:61:
/usr/include/asm/io_apic.h:120: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/io_apic.h:120: error: conflicting types for `mp_irqs'
/usr/include/asm/mpspec.h:22: error: previous declaration of `mp_irqs'
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/module.h:10,
                 from pci-scan.c:61:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
pci-scan.c: In function `pci_drv_register':
pci-scan.c:224: warning: `check_region' is deprecated (declared at /usr/include/linux/ioport.h:118)
pci-scan.c:278: warning: `MOD_INC_USE_COUNT' is deprecated (declared at /usr/include/linux/module.h:482)
pci-scan.c: In function `pci_drv_unregister':
pci-scan.c:441: warning: `MOD_DEC_USE_COUNT' is deprecated (declared at /usr/include/linux/module.h:494)

```

---

### Post by kleeman on 2005-07-12
Sorry I goofed, that driver is no longer in the 2.6 kernel (it was in the old 2.4 kernel).
I am a bit stuck for advice at this point. It looks like this problem may have occured previously

[http://kerneltrap.org/node/2292](http://kerneltrap.org/node/2292)

I suggest two possibilities:

1) Install the 2.6.11 kernel and see whether this helps (a bug might have been fixed)
2) Report this problem on Ubuntu Bugzilla and see what the devs say 

Sorry I can't suggest anything else, driver problems like this are hard to sort out...

---

### Post by rathel on 2005-07-12
It's okay. Thanks for helping though.

---

