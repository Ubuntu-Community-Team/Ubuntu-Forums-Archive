---
title: "dmesg polluted with internet packets"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by ashrack on 2006-08-03
I connect thru PPPOE! And I've set up my INET connection with 'pppoeconf'
But now whilst surfing internet all that I get in DMESG is this:
```
[17181159.676000] Inbound IN=ppp0 OUT= MAC= SRC=221.209.110.45 DST=193.95.194.241 LEN=486 TOS=0x00 PREC=0x00 TTL=40 ID=0 DF PROTO=UDP SPT=49308 DPT=1027 LEN=466
[17181165.412000] Inbound IN=ppp0 OUT= MAC= SRC=200.88.50.148 DST=193.95.194.241 LEN=90 TOS=0x00 PREC=0x00 TTL=108 ID=21511 PROTO=UDP SPT=16988 DPT=32768 LEN=70
[17181186.240000] Inbound IN=ppp0 OUT= MAC= SRC=193.95.200.216 DST=193.95.194.241 LEN=48 TOS=0x00 PREC=0x00 TTL=126 ID=12455 DF PROTO=TCP SPT=4075 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
[17181189.232000] Inbound IN=ppp0 OUT= MAC= SRC=193.95.200.216 DST=193.95.194.241 LEN=48 TOS=0x00 PREC=0x00 TTL=126 ID=12727 DF PROTO=TCP SPT=4075 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0

```
How to I disable PPP writting to DMESG?
Its very annyoing since I cant view the messeages now anymore!!

---

### Post by ashrack on 2006-08-04
bump

---

### Post by eXisor on 2006-08-04
Do an 'ifconfig' and show us the results.

---

### Post by ashrack on 2006-08-04
```

##4 my lan
eth0      Link encap:Ethernet  HWaddr 00:08:A1:75:1C:87
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::208:a1ff:fe75:1c87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:23144 (22.6 KiB)  TX bytes:22295 (21.7 KiB)
          Interrupt:10 Base address:0xe400

##4 PPPOE connetion
eth1      Link encap:Ethernet  HWaddr 00:08:A1:0E:0A:F9
          inet6 addr: fe80::208:a1ff:fe0e:af9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:25787865 (24.5 MiB)  TX bytes:2887201 (2.7 MiB)
          Interrupt:3 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3636 (3.5 KiB)  TX bytes:3636 (3.5 KiB)

### The PPPOE connection
ppp0      Link encap:Point-to-Point Protocol
          inet addr:193.77.18.15  P-t-P:213.250.19.90  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:27803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:25102751 (23.9 MiB)  TX bytes:2396808 (2.2 MiB)


```

---

### Post by ashrack on 2006-08-05
bump

---

