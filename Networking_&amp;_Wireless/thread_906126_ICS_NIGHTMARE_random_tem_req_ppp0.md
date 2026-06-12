---
title: "ICS NIGHTMARE random tem_req ppp0"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by p1ruj3 on 2008-08-31
This has been an ongoing issue for over 7 months now and i cannot figure it out for the life of me.

I have ics working just fine from a usb720

ppp0 is my internet connect, etho is my outgoing to my wireless router.

The ppp connection is solid, ics works but randomly drops the connection. I have tried everything from setting it up from ubuntu's ics page, to using guarddog to using firestarter.

I cannot figure out why the connection is dropping when i do a tcpdump -i ppp0 i notice that 7 out of 10 times when it drops its showing my 10.10.0.10 as outgoing.... my understanding is it should ever show a reserved internal address there...

 ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:09:6b:5f:34:88  
          inet addr:10.10.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::209:6bff:fe5f:3488/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:55 txqueuelen:1000 
          RX bytes:4649608 (4.4 MB)  TX bytes:101744297 (97.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105430 (102.9 KB)  TX bytes:105430 (102.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:70.209.208.142  P-t-P:66.174.66.4  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2040 (1.9 KB)  TX bytes:859 (859.0 B)
Linux ibm 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

```
if i unplug the eth0 cord and browse on the machine the internet is stable as can be.

talking to my isp they say my machine is dropping the connection.
```

Aug 31 01:10:18 ibm pppd[6091]: LCP terminated by peer
Aug 31 00:23:18 ibm pppd[6091]: rcvd [LCP TermReq id=0x53]

```
this id number changes 





tcpdump -i ppp0
```
 
01:05:50.337659 IP 10.10.0.10.60726 > unknown.nscnap.net.www: F 0:0(0) ack 1 win 65535

```

i have tried 4 different wireless routers, turned off the wireless, tried just connecting it to a machine and no matter what it randomly drops the connection once i start using the connection out side of the ics machine

as you see everything connects just fine
```

Aug 31 01:12:57 ibm chat[2078]: send (ATZ^M)
Aug 31 01:12:57 ibm chat[2078]: expect (OK)
Aug 31 01:12:57 ibm chat[2078]: ATZ^M^M
Aug 31 01:12:57 ibm chat[2078]: OK
Aug 31 01:12:57 ibm chat[2078]:  -- got it 
Aug 31 01:12:57 ibm chat[2078]: send (ATDT#777^M)
Aug 31 01:12:57 ibm chat[2078]: expect (CONNECT)
Aug 31 01:12:57 ibm chat[2078]: ^M
Aug 31 01:12:59 ibm chat[2078]: ATDT#777^M^M
Aug 31 01:12:59 ibm chat[2078]: CONNECT
Aug 31 01:12:59 ibm chat[2078]:  -- got it 
Aug 31 01:12:59 ibm chat[2078]: send (\d)
Aug 31 01:13:00 ibm pppd[6091]: Serial connection established.
Aug 31 01:13:00 ibm pppd[6091]: Using interface ppp0
Aug 31 01:13:00 ibm pppd[6091]: Connect: ppp0 <--> /dev/ttyUSB0
Aug 31 01:13:01 ibm pppd[6091]: local  IP address 70.219.61.224
Aug 31 01:13:01 ibm pppd[6091]: remote IP address 66.174.66.4
Aug 31 01:13:01 ibm pppd[6091]: primary   DNS address 66.174.92.14
Aug 31 01:13:01 ibm pppd[6091]: secondary DNS address 66.174.95.44

```
i have struggled to figure out what is going on to the point of massive frustration please any suggestions welcome. is there a better linux platform i should use? i have tried several different machines as well running ubuntu and kubuntu. ubuntu seems more stable.
```

 lsusb 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1410:2110  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

dmesg
[ 9681.461761] device ppp0 entered promiscuous mode
[ 9681.461794] audit(1220166146.029:10): dev=ppp0 prom=256 old_prom=0 auid=4294967295
[ 9752.678485] Inbound IN=ppp0 OUT= MAC= SRC=68.103.58.142 DST=70.209.149.143 LEN=134 TOS=0x00 PREC=0x20 TTL=102 ID=15391 PROTO=UDP SPT=2575 DPT=62017 LEN=114 
[ 9754.864007] Inbound IN=ppp0 OUT= MAC= SRC=68.103.58.142 DST=70.209.149.143 LEN=134 TOS=0x00 PREC=0x20 TTL=102 ID=15396 PROTO=UDP SPT=2575 DPT=62017 LEN=114 
[ 4504.579514] Inbound IN=ppp0 OUT= MAC= SRC=68.103.58.142 DST=70.209.149.143 LEN=134 TOS=0x00 PREC=0x20 TTL=102 ID=15402 PROTO=UDP SPT=2575 DPT=62017 LEN=114 
[ 9782.367201] device ppp0 left promiscuous mode
[ 9782.367227] audit(1220166212.497:11): dev=ppp0 prom=0 old_prom=256 auid=4294967295
[ 4537.992925] Unknown ForwardIN=eth0 OUT=ppp0 SRC=10.10.0.10 DST=209.85.133.189 LEN=40 TOS=0x00 PREC=0x00 TTL=126 ID=7855 DF PROTO=TCP SPT=60669 DPT=80 WINDOW=16890 RES=0x00 ACK FIN URGP=0 
[ 9842.978430] device ppp0 entered promiscuous mode
[ 9842.978457] audit(1220166263.413:12): dev=ppp0 prom=256 old_prom=0 auid=4294967295
[ 9985.540735] device ppp0 left promiscuous mode
[ 9985.540758] audit(1220166353.501:13): dev=ppp0 prom=0 old_prom=256 auid=4294967295
[10401.993876] Inbound IN=ppp0 OUT= MAC= SRC=24.64.10.157 DST=70.219.102.145 LEN=516 TOS=0x00 PREC=0x00 TTL=63 ID=10434 PROTO=UDP SPT=15608 DPT=1028 LEN=496 

cat /etc/chatscripts/vzw
# This chatfile was generated by pppconfig 2.3.15.
# Please do not delete any of the comments.  Pppconfig needs them.
# 
# ispauth PAP
# abortstring
ABORT BUSY ABORT 'NO CARRIER' ABORT VOICE ABORT 'NO DIALTONE' ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT DELAYED
# modeminit
'' ATZ
# ispnumber
OK-AT-OK "ATDT#777"
# ispconnect
CONNECT \d\c
# prelogin

# ispname
# isppassword
# postlogin

# end of pppconfig stuff

cat /etc/ppp/peers/vzw
# This optionfile was generated by pppconfig 2.3.15. 
# 
#
hide-password 
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/vzw"
debug
/dev/ttyUSB0
115200
defaultroute
noipdefault 
user "3039688370@myvzw.com"
remotename vzw
ipparam vzw
persist
maxfail 0
usepeerdns
noproxyarp

```

---

### Post by p1ruj3 on 2008-09-01
another tcpdump right when connection drops..
```

23:36:34.179407 IP mail.fpsn.net.smtp > 177.sub-70-219-2.myvzw.com.60256: . ack 2886862 win 65534
23:36:34.838462 IP fg-in-f136.google.com.www > 177.sub-70-219-2.myvzw.com.60266: F 61946:61946(0) ack 801 win 7200
23:36:34.840684 IP 177.sub-70-219-2.myvzw.com.60266 > fg-in-f136.google.com.www: . ack 61947 win 16705
23:36:44.551946 IP 177.sub-70-219-2.myvzw.com.60266 > fg-in-f136.google.com.www: F 801:801(0) ack 61947 win 16705
23:36:45.384443 IP fg-in-f136.google.com.www > 177.sub-70-219-2.myvzw.com.60266: . ack 802 win 7200
23:36:49.990356 IP 10.10.0.10.60236 > l1.ycs.vip.a2s.yahoo.com.www: F 0:0(0) ack 1 win 17106
23:36:50.931938 IP 74.125.1.39.www > 177.sub-70-219-2.myvzw.com.60270: F 6120:6120(0) ack 8245 win 17325
23:36:50.933966 IP 177.sub-70-219-2.myvzw.com.60270 > 74.125.1.39.www: . ack 6121 win 17520
23:36:51.677039 IP 177.sub-70-219-2.myvzw.com.60271 > 192.168.0.90.snmp:  GetRequest(63)  25.3.2.1.5.1 [|snmp]
23:36:57.548974 IP 177.sub-70-219-2.myvzw.com.60270 > 74.125.1.39.www: F 8245:8245(0) ack 6121 win 17520
23:36:57.774522 IP 74.125.1.39.www > 177.sub-70-219-2.myvzw.com.60270: . ack 8246 win 17325
23:36:58.024652 IP 177.sub-70-219-2.myvzw.com.60271 > 192.168.0.90.snmp:  GetRequest(63)  25.3.2.1.5.1 [|snmp]
23:36:59.961029 IP 10.10.0.10.60272 > 96.7.152.216.www: F 2908067486:2908067486(0) ack 4178192497 win 64838
tcpdump: pcap_loop: recvfrom: Network is down
3602 packets captured
3678 packets received by filter
72 packets dropped by kernel

```

---

### Post by mellowd on 2008-09-01
You say the Pc is plugged into your router? What's the IP address of the router interface facing your PC?

---

### Post by p1ruj3 on 2008-09-01
10.10.1.15

---

### Post by dmizer on 2008-09-01
Do you have NAT disabled on your router?  Since your Ubuntu computer is performing NAT, there will be a conflict if there are two NAT servers on the same subnet.

---

### Post by p1ruj3 on 2008-09-01
im sorry its 10.10.1.5

here is from a machine behind router
C:\Documents and Settings\Matthew Yelick>ipconfig

Windows IP Configuration


Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 10.10.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway & dns . . . . . . . . . : 10.10.1.5

C:\Documents and Settings\Matthew Yelick>

---

### Post by mellowd on 2008-09-01
So it isn't an issue with the IP address. Your pc and router are on the 10.10.0.0/24 subnet while the outgoing router interface will have a public IP.


But hang on, there is something I don't understand. a PPP connection is generally a logical connection bound to a physical interface (the E1) but you say when you disconnect the cat5 cable you can browse the net fine. 

So, how exactly is this set up? Do you have an adsl modem in your linux box as well? Is that dialing out seperately to your router connection?

---

### Post by p1ruj3 on 2008-09-01
i do not beleive there to be nat turned on, or existing on my router

 its a DI-524 dlink

---

### Post by dmizer on 2008-09-01
All routers do NAT unless it's specifically disabled.

Have a look here: [http://forums.whirlpool.net.au/forum-replies-archive.cfm/735497.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/735497.html)

---

### Post by p1ruj3 on 2008-09-01
i have my ubuntu machine which has a usb720 wireless usb evdo card that i uses pppd to establish a ppp0 connection which is my internet... then i have a eth0 interface which i masq out to my dlink di-524 wireless router where i have my other machines connected to wireless'ly and hardwired...

it seems if i max the connection out on any machines connected to the wireless router then connection drops randomly.... but if i unplug the eth0 and for exe upgrade ubuntu it said connected and did 800mb of transfer just fine....

i tried to upgrade it for a month and it wouldnt hold a solid connection untill i figured out to unplug the eth0 for a few hours so it could do that.... i was hoping that would resolve the issue... it didn't

---

### Post by dmizer on 2008-09-01
Here's what your problem is. You have two network connections both connected to routeable IP addresses. Your Ubuntu computer doesn't know which adapter to send data across.

Your dlink router and Ubuntu are fighting for domination on the same subnet. In other words, both your Ubuntu computer AND your dlink router are trying to give IP addresses to the rest of the computers on your network.

There may be other problems involved here, but NAT is certainly causing you some difficulty. You'll need to fix that before you can move on to other things.

---

### Post by p1ruj3 on 2008-09-01
ok dmizer, so i connect the cord from my ubuntu machine eth0 interface to just one of the four ports besides the lan and that disables nat? so i am in effect just using it as a hub?

---

### Post by dmizer on 2008-09-01
You will _also_ need to turn off DHCP in the router settings. So yes, your router will be nothing more than a hub.

---

### Post by p1ruj3 on 2008-09-01
wow understood, yes disable dhcp on my dlink, and enable it in ubuntu to make it simple...? and then (the last bit i am unclear about) set the dlink to get its wan i from ubuntu or set it static to be 10.10.0.5 or should that be its lan ip?

i only need one subnet and i was using two right?

---

### Post by dmizer on 2008-09-01
The dlink will no longer get or need an IP from anything.  If you have ICS configured correctly on your Ubuntu machine, then all computers in your network will be getting an IP address directly from Ubuntu.  More information here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Edit ... forgot to answer this:
> **p1ruj3 said:**
> i only need one subnet and i was using two right?
Not exactly. If it had been two subnets you would have been fine, but none of the network computers would be able to talk with Ubuntu directly.

Your problem was that you had two NAT servers on the SAME subnet.

More information here:[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)

And a more simplistic explanation here: [http://computer.howstuffworks.com/nat.htm](http://computer.howstuffworks.com/nat.htm)

---

### Post by p1ruj3 on 2008-09-01
ok got everything working need to flood the connection now and see if it drops it THANK YOU SO MUCH

so far i had to set everything up static, i think i need to do the dnsmasq and my dhcp server will work out... ill let you know, thanks for getting me in the right direction!!! i knew it was something "common sensed" :popcorn::lolflag:

---

### Post by p1ruj3 on 2008-09-01
okay, as you predicted there are other issues going on... connection is still randomly disconnecting... ( did get dhcp3 to work just fine )
i have no clue where to go from here

---

### Post by p1ruj3 on 2008-09-01
```

Sep  1 01:28:21 ibm chat[19561]: ATDT#777^M^M
Sep  1 01:28:21 ibm chat[19561]: CONNECT
Sep  1 01:28:21 ibm chat[19561]:  -- got it 
Sep  1 01:28:21 ibm chat[19561]: send (\d)
Sep  1 01:28:22 ibm pppd[6091]: Serial connection established.
Sep  1 01:28:22 ibm pppd[6091]: Using interface ppp0
Sep  1 01:28:22 ibm pppd[6091]: Connect: ppp0 <--> /dev/ttyUSB0
Sep  1 01:28:23 ibm pppd[6091]: local  IP address 70.209.13.247
Sep  1 01:28:23 ibm pppd[6091]: remote IP address 66.174.66.4
Sep  1 01:28:23 ibm pppd[6091]: primary   DNS address 66.174.92.14
Sep  1 01:28:23 ibm pppd[6091]: secondary DNS address 66.174.95.44
Sep  1 01:28:24 ibm kernel: [46675.613442] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:ce:a3:d4:bf:08:00 SRC=10.10.0.198 DST=10.255.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17234 PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep  1 01:28:27 ibm kernel: [101173.676119] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:ce:a3:d4:bf:08:00 SRC=10.10.0.198 DST=10.255.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17267 PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep  1 01:28:27 ibm kernel: [101174.426033] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:ce:a3:d4:bf:08:00 SRC=10.10.0.198 DST=10.255.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17272 PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep  1 01:30:12 ibm pppd[6091]: LCP terminated by peer
Sep  1 01:30:12 ibm pppd[6091]: Connect time 1.9 minutes.
Sep  1 01:30:12 ibm pppd[6091]: Sent 60329 bytes, received 141709 bytes.
Sep  1 01:30:12 ibm pppd[6091]: Hangup (SIGHUP)
Sep  1 01:30:12 ibm pppd[6091]: Modem hangup
Sep  1 01:30:12 ibm pppd[6091]: Connection terminated.


Sep  1 01:16:12 ibm kernel: [100271.985745] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:ce:4b:f1:f0:08:00 SRC=10.10.0.200 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=42618 PROTO=UDP SPT=68 DPT=67 LEN=308 
Sep  1 01:16:13 ibm kernel: [46261.612789] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:ce:a3:d4:bf:08:00 SRC=10.10.0.198 DST=10.255.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=12746 PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep  1 01:16:16 ibm kernel: [100276.866826] Unknown InputIN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:ce:4b:f1:f0:08:00 SRC=10.10.0.200 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=42619 PROTO=UDP SPT=68 DPT=67 LEN=308 
Sep  1 01:16:25 ibm kernel: [46268.368897] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:ce:4b:f1:f0:08:00 SRC=10.10.0.200 DST=10.255.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=42623 PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep  1 01:16:26 ibm kernel: [100288.112661] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:ce:4b:f1:f0:08:00 SRC=10.10.0.200 DST=10.255.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=42624 PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep  1 01:16:26 ibm kernel: [100289.066768] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:ce:4b:f1:f0:08:00 SRC=10.10.0.200 DST=10.255.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=42625 PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep  1 01:23:28 ibm kernel: [46512.692308] device ppp0 entered promiscuous mode
Sep  1 01:23:28 ibm kernel: [46512.692324] audit(1220253808.429:18): dev=ppp0 prom=256 old_prom=0 auid=4294967295
Sep  1 01:24:50 ibm kernel: [46555.488760] device ppp0 left promiscuous mode
Sep  1 01:24:50 ibm kernel: [46555.488776] audit(1220253890.505:19): dev=ppp0 prom=0 old_prom=256 auid=4294967295
Sep  1 01:28:24 ibm kernel: [46675.613442] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:ce:a3:d4:bf:08:00 SRC=10.10.0.198 DST=10.255.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17234 PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep  1 01:28:27 ibm kernel: [101173.676119] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:ce:a3:d4:bf:08:00 SRC=10.10.0.198 DST=10.255.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17267 PROTO=UDP SPT=137 DPT=137 LEN=58 
Sep  1 01:28:27 ibm kernel: [101174.426033] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:13:ce:a3:d4:bf:08:00 SRC=10.10.0.198 DST=10.255.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=17272 PROTO=UDP SPT=137 DPT=137 LEN=58 

Sep  1 01:27:48 ibm pppd[6091]: Script /etc/ppp/ip-down started (pid 19449)
Sep  1 01:27:48 ibm pppd[6091]: sent [LCP TermAck id=0xa3]
Sep  1 01:27:48 ibm pppd[6091]: Script /etc/ppp/ip-down finished (pid 19449), status = 0x1
Sep  1 01:28:22 ibm pppd[6091]: using channel 154
Sep  1 01:28:23 ibm pppd[6091]: sent [LCP ConfReq id=0x9a <asyncmap 0x0> <magic 0x6c2b30a0> <pcomp> <accomp>]
Sep  1 01:28:23 ibm pppd[6091]: rcvd [LCP ConfReq id=0xa4 <mru 1500> <asyncmap 0x0> <magic 0x8c886360> <pcomp> <accomp>]
Sep  1 01:28:23 ibm pppd[6091]: sent [LCP ConfAck id=0xa4 <mru 1500> <asyncmap 0x0> <magic 0x8c886360> <pcomp> <accomp>]
Sep  1 01:28:23 ibm pppd[6091]: rcvd [LCP ConfAck id=0x9a <asyncmap 0x0> <magic 0x6c2b30a0> <pcomp> <accomp>]
Sep  1 01:28:23 ibm pppd[6091]: sent [CCP ConfReq id=0x9a <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Sep  1 01:28:23 ibm pppd[6091]: sent [IPCP ConfReq id=0xcc <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 01:28:23 ibm pppd[6091]: rcvd [LCP DiscReq id=0xa5 magic=0x8c886360]
Sep  1 01:28:23 ibm pppd[6091]: rcvd [IPCP ConfReq id=0xea <addr 66.174.66.4>]
Sep  1 01:28:23 ibm pppd[6091]: sent [IPCP ConfAck id=0xea <addr 66.174.66.4>]
Sep  1 01:28:23 ibm pppd[6091]: rcvd [LCP ProtRej id=0xa6 80 fd 01 9a 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Sep  1 01:28:23 ibm pppd[6091]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Sep  1 01:28:23 ibm pppd[6091]: rcvd [IPCP ConfRej id=0xcc <compress VJ 0f 01>]
Sep  1 01:28:23 ibm pppd[6091]: sent [IPCP ConfReq id=0xcd <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 01:28:23 ibm pppd[6091]: rcvd [IPCP ConfNak id=0xcd <addr 70.209.13.247> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 01:28:23 ibm pppd[6091]: sent [IPCP ConfReq id=0xce <addr 70.209.13.247> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 01:28:23 ibm pppd[6091]: rcvd [IPCP ConfAck id=0xce <addr 70.209.13.247> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 01:28:23 ibm pppd[6091]: Script /etc/ppp/ip-up started (pid 19564)
Sep  1 01:28:33 ibm pppd[6091]: Script /etc/ppp/ip-up finished (pid 19564), status = 0x0
Sep  1 01:30:12 ibm pppd[6091]: rcvd [LCP TermReq id=0xa7]
Sep  1 01:30:12 ibm pppd[6091]: Script /etc/ppp/ip-down started (pid 20311)
Sep  1 01:30:12 ibm pppd[6091]: sent [LCP TermAck id=0xa7]
Sep  1 01:30:12 ibm pppd[6091]: Script /etc/ppp/ip-down finished (pid 20311), status = 0x1
Sep  1 01:30:46 ibm pppd[6091]: using channel 155
Sep  1 01:30:47 ibm pppd[6091]: sent [LCP ConfReq id=0x9b <asyncmap 0x0> <magic 0xe16f84f8> <pcomp> <accomp>]
Sep  1 01:30:47 ibm pppd[6091]: rcvd [LCP ConfReq id=0xa8 <mru 1500> <asyncmap 0x0> <magic 0x8c8a96ef> <pcomp> <accomp>]
Sep  1 01:30:47 ibm pppd[6091]: sent [LCP ConfAck id=0xa8 <mru 1500> <asyncmap 0x0> <magic 0x8c8a96ef> <pcomp> <accomp>]
Sep  1 01:30:47 ibm pppd[6091]: rcvd [LCP ConfAck id=0x9b <asyncmap 0x0> <magic 0xe16f84f8> <pcomp> <accomp>]
Sep  1 01:30:47 ibm pppd[6091]: sent [CCP ConfReq id=0x9b <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Sep  1 01:30:47 ibm pppd[6091]: sent [IPCP ConfReq id=0xcf <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 01:30:47 ibm pppd[6091]: rcvd [LCP DiscReq id=0xa9 magic=0x8c8a96ef]
Sep  1 01:30:47 ibm pppd[6091]: rcvd [IPCP ConfReq id=0xeb <addr 66.174.66.4>]
Sep  1 01:30:47 ibm pppd[6091]: sent [IPCP ConfAck id=0xeb <addr 66.174.66.4>]
Sep  1 01:30:47 ibm pppd[6091]: rcvd [LCP ProtRej id=0xaa 80 fd 01 9b 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Sep  1 01:30:47 ibm pppd[6091]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Sep  1 01:30:47 ibm pppd[6091]: rcvd [IPCP ConfRej id=0xcf <compress VJ 0f 01>]
Sep  1 01:30:47 ibm pppd[6091]: sent [IPCP ConfReq id=0xd0 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 01:30:47 ibm pppd[6091]: rcvd [IPCP ConfNak id=0xd0 <addr 70.209.162.21> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 01:30:47 ibm pppd[6091]: sent [IPCP ConfReq id=0xd1 <addr 70.209.162.21> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 01:30:47 ibm pppd[6091]: rcvd [IPCP ConfAck id=0xd1 <addr 70.209.162.21> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 01:30:47 ibm pppd[6091]: Script /etc/ppp/ip-up started (pid 20418)
Sep  1 01:30:58 ibm pppd[6091]: Script /etc/ppp/ip-up finished (pid 20418), status = 0x0
Sep  1 01:32:20 ibm pppd[6091]: rcvd [LCP TermReq id=0xab]
Sep  1 01:32:20 ibm pppd[6091]: Script /etc/ppp/ip-down started (pid 21127)
Sep  1 01:32:20 ibm pppd[6091]: sent [LCP TermAck id=0xab]
Sep  1 01:32:20 ibm pppd[6091]: Script /etc/ppp/ip-down finished (pid 21127), status = 0x1

```

---

### Post by p1ruj3 on 2008-09-01
Windows IP Configuration

        Host Name . . . . . . . . . . . . : Treatment
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Broadcast
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Intel(R) PRO/Wireless 2915ABG Networ
k Connection
        Physical Address. . . . . . . . . : 00-13-CE-A3-D4-BF
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.10.0.198
        Subnet Mask . . . . . . . . . . . : 255.0.0.0
        Default Gateway . . . . . . . . . : 10.10.0.1
        DHCP Server . . . . . . . . . . . : 10.10.0.1
        DNS Servers . . . . . . . . . . . : 66.174.92.14
        Lease Obtained. . . . . . . . . . : Monday, September 01, 2008 1:11:42 A
M
        Lease Expires . . . . . . . . . . : Monday, September 01, 2008 7:11:42 A
M

---

### Post by dmizer on 2008-09-01
Just on a whim, try disabling IPv6 according to this howto:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

Also, post the output of:
```
lshw -C network
```

---

### Post by p1ruj3 on 2008-09-01
ok.. not sure if that link was right, i didnt see any specific directions on disabling ipv6 so i did this

/etc/modprobe.d/aliases

and change the line: alias net-pf-10 ipv6

to: alias net-pf-10 off ipv6


.....

lshw -C network

```

  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=80 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:09:6b:5f:34:88
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=10.10.0.1 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

```
im going to reboot to get ipv6 off

---

### Post by p1ruj3 on 2008-09-01
er do i need to reboot? 

btw whats ird0?

 ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:09:6b:5f:34:88 brd ff:ff:ff:ff:ff:ff
    inet 10.10.0.1/8 brd 10.255.255.255 scope global eth0
    inet6 fe80::209:6bff:fe5f:3488/64 scope link 
       valid_lft forever preferred_lft forever
3: irda0: <NOARP> mtu 2048 qdisc noop qlen 8
    link/irda 00:00:00:00 brd ff:ff:ff:ff
168: ppp0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 3
    link/ppp 
    inet 70.209.9.52 peer 66.174.66.4/32 scope global ppp0

---

### Post by dmizer on 2008-09-01
Okay, updated the link, should have been this: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?) Moving between Windows at work and linux at home always screws with my copy/paste routine.

Yes, you do need to reboot. Looks like you still have IPv6 addressing in place too.

Irda is for infrared.

---

### Post by p1ruj3 on 2008-09-01
ok i did that and rebootd, as far as i can tell ipv6 is not running, still randomly disconnecting me...

---

### Post by p1ruj3 on 2008-09-01
tcpdump -i ppp0 -v
tcpdump: listening on ppp0, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
02:48:24.319149 IP (tos 0x0, ttl 63, id 18767, offset 0, flags [none], proto TCP (6), length 40) 10.10.0.199.50994 > feijoa.canonical.com.www: F, cksum 0x8069 (correct), 658272351:658272351(0) ack 1658955984 win 65535
02:48:31.972507 IP (tos 0x0, ttl 63, id 21668, offset 0, flags [none], proto TCP (6), length 40) 10.10.0.199.50995 > feijoa.canonical.com.www: F, cksum 0xf2f4 (correct), 650282155:650282155(0) ack 1654727346 win 65535
02:48:24.373057 IP (tos 0x0, ttl 64, id 5914, offset 0, flags [DF], proto UDP (17), length 71) 70.209.207.30.52899 > 66.174.92.14.domain: 45634+ PTR? 12.94.189.91.in-addr.arpa. (43)
tcpdump: pcap_loop: recvfrom: Network is down


it seems as if it is disconnecting way faster now, can hardly stay connected for 20 seconds....

---

### Post by p1ruj3 on 2008-09-01
ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:09:6b:5f:34:88 brd ff:ff:ff:ff:ff:ff
    inet 10.10.0.1/8 brd 10.255.255.255 scope global eth0
3: irda0: <NOARP> mtu 2048 qdisc noop qlen 8
    link/irda 00:00:00:00 brd ff:ff:ff:ff
19: ppp0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 3
    link/ppp 
    inet 70.209.154.65 peer 66.174.66.4/32 scope global ppp0


so ipv6 is definetly off

---

### Post by p1ruj3 on 2008-09-01
```

515 > feijoa.canonical.com.www: ., cksum 0x6cd5 (correct), ack 7209 win 16153
02:52:13.093399 IP (tos 0x0, ttl 42, id 56210, offset 0, flags [DF], proto TCP (6), length 40) feijoa.canonical.com.www > 65.sub-70-209-154.myvzw.com.1516: F, cksum 0x6dc5 (correct), 201:201(0) ack 721 win 7200
02:52:13.094538 IP (tos 0x0, ttl 127, id 12267, offset 0, flags [DF], proto TCP (6), length 40) 65.sub-70-209-154.myvzw.com.1516 > feijoa.canonical.com.www: ., cksum 0x463d (correct), ack 202 win 17320
02:52:13.314430 IP (tos 0x0, ttl 42, id 22854, offset 0, flags [DF], proto TCP (6), length 40) feijoa.canonical.com.www > 65.sub-70-209-154.myvzw.com.1517: F, cksum 0x8d21 (correct), 201:201(0) ack 737 win 6624
02:52:13.315623 IP (tos 0x0, ttl 127, id 12270, offset 0, flags [DF], proto TCP (6), length 40) 65.sub-70-209-154.myvzw.com.1517 > feijoa.canonical.com.www: ., cksum 0x6359 (correct), ack 202 win 17320
02:52:13.533448 IP (tos 0x0, ttl 42, id 32298, offset 0, flags [DF], proto TCP (6), length 40) feijoa.canonical.com.www > 65.sub-70-209-154.myvzw.com.1518: F, cksum 0xeb13 (correct), 201:201(0) ack 729 win 7280
02:52:13.534658 IP (tos 0x0, ttl 127, id 12271, offset 0, flags [DF], proto TCP (6), length 40) 65.sub-70-209-154.myvzw.com.1518 > feijoa.canonical.com.www: ., cksum 0xc3db (correct), ack 202 win 17320
02:52:13.751472 IP (tos 0x0, ttl 42, id 15560, offset 0, flags [DF], proto TCP (6), length 40) feijoa.canonical.com.www > 65.sub-70-209-154.myvzw.com.1519: F, cksum 0xc595 (correct), 201:201(0) ack 728 win 7270
02:52:13.752691 IP (tos 0x0, ttl 127, id 12272, offset 0, flags [DF], proto TCP (6), length 40) 65.sub-70-209-154.myvzw.com.1519 > feijoa.canonical.com.www: ., cksum 0x9e53 (correct), ack 202 win 17320
02:52:16.229929 IP (tos 0x0, ttl 63, id 14872, offset 0, flags [none], proto TCP (6), length 52) 10.10.0.199.50992 > feijoa.canonical.com.www: F, cksum 0xf8b6 (correct), 0:0(0) ack 1 win 65535 <nop,nop,timestamp 2518 820476402>
02:52:21.670255 IP (tos 0x0, ttl 63, id 4382, offset 0, flags [none], proto TCP (6), length 552) 10.10.0.199.50991 > feijoa.canonical.com.www: . 0:500(500) ack 1 win 65535 <nop,nop,timestamp 2476 820482850>
02:52:24.898041 IP (tos 0x0, ttl 127, id 12462, offset 0, flags [DF], proto TCP (6), length 40) 65.sub-70-209-154.myvzw.com.1519 > feijoa.canonical.com.www: F, cksum 0x9e52 (correct), 728:728(0) ack 202 win 17320
02:52:24.898325 IP (tos 0x0, ttl 127, id 12463, offset 0, flags [DF], proto TCP (6), length 40) 65.sub-70-209-154.myvzw.com.1518 > feijoa.canonical.com.www: F, cksum 0xc3da (correct), 729:729(0) ack 202 win 17320
02:52:24.898626 IP (tos 0x0, ttl 127, id 12464, offset 0, flags [DF], proto TCP (6), length 40) 65.sub-70-209-154.myvzw.com.1517 > feijoa.canonical.com.www: F, cksum 0x6358 (correct), 737:737(0) ack 202 win 17320
02:52:24.898926 IP (tos 0x0, ttl 127, id 12465, offset 0, flags [DF], proto TCP (6), length 40) 65.sub-70-209-154.myvzw.com.1516 > feijoa.canonical.com.www: F, cksum 0x463c (correct), 721:721(0) ack 202 win 17320
02:52:24.899424 IP (tos 0x0, ttl 127, id 12466, offset 0, flags [DF], proto TCP (6), length 40) 65.sub-70-209-154.myvzw.com.1515 > feijoa.canonical.com.www: F, cksum 0x6cd4 (correct), 2695:2695(0) ack 7209 win 16153
tcpdump: pcap_loop: recvfrom: Network is down
432 packets captured
432 packets received by filter
0 packets dropped by kernel

```

---

### Post by p1ruj3 on 2008-09-01
tcpdump of eth0
```

02:54:09.782533 IP (tos 0x0, ttl 64, id 17241, offset 0, flags [DF], proto TCP (6), length 722) ibm.local.5900 > 10.10.0.198.1435: P 112827:113509(682) ack 577 win 5840
02:54:09.783681 IP (tos 0x0, ttl 64, id 17242, offset 0, flags [DF], proto TCP (6), length 823) ibm.local.5900 > 10.10.0.198.1435: P 113509:114292(783) ack 577 win 5840
02:54:09.783787 IP (tos 0x0, ttl 64, id 17243, offset 0, flags [DF], proto TCP (6), length 66) ibm.local.5900 > 10.10.0.198.1435: P, cksum 0x6c13 (correct), 114292:114318(26) ack 577 win 5840
02:54:09.784557 IP (tos 0x0, ttl 128, id 14938, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x2dab (correct), ack 113509 win 15464
02:54:09.785237 IP (tos 0x0, ttl 64, id 17244, offset 0, flags [DF], proto TCP (6), length 757) ibm.local.5900 > 10.10.0.198.1435: P 114318:115035(717) ack 577 win 5840
02:54:09.785404 IP (tos 0x0, ttl 128, id 14939, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x2dab (correct), ack 114318 win 14655
02:54:09.786164 IP (tos 0x0, ttl 64, id 17245, offset 0, flags [DF], proto TCP (6), length 617) ibm.local.5900 > 10.10.0.198.1435: P 115035:115612(577) ack 577 win 5840
02:54:09.786267 IP (tos 0x0, ttl 64, id 17246, offset 0, flags [DF], proto TCP (6), length 66) ibm.local.5900 > 10.10.0.198.1435: P, cksum 0x6791 (correct), 115612:115638(26) ack 577 win 5840
02:54:09.788530 IP (tos 0x0, ttl 64, id 17247, offset 0, flags [DF], proto TCP (6), length 540) ibm.local.5900 > 10.10.0.198.1435: P 115638:116138(500) ack 577 win 5840
02:54:09.789730 IP (tos 0x0, ttl 128, id 14940, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x2dab (correct), ack 115612 win 13361
02:54:09.790479 IP (tos 0x0, ttl 64, id 17248, offset 0, flags [DF], proto TCP (6), length 345) ibm.local.5900 > 10.10.0.198.1435: P 116138:116443(305) ack 577 win 5840
02:54:09.791181 IP (tos 0x0, ttl 128, id 14941, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x2dab (correct), ack 116138 win 12835
02:54:09.791296 IP (tos 0x0, ttl 64, id 17249, offset 0, flags [DF], proto TCP (6), length 66) ibm.local.5900 > 10.10.0.198.1435: P, cksum 0x641c (correct), 116443:116469(26) ack 577 win 5840
02:54:09.792403 IP (tos 0x0, ttl 128, id 14942, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x2dab (correct), ack 116469 win 12504
02:54:09.799731 IP (tos 0x0, ttl 128, id 14943, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x1c4b (correct), ack 116469 win 16952
02:54:09.801355 IP (tos 0x0, ttl 64, id 17250, offset 0, flags [DF], proto TCP (6), length 753) ibm.local.5900 > 10.10.0.198.1435: P 116469:117182(713) ack 577 win 5840
02:54:09.802525 IP (tos 0x0, ttl 64, id 17251, offset 0, flags [DF], proto TCP (6), length 822) ibm.local.5900 > 10.10.0.198.1435: P 117182:117964(782) ack 577 win 5840
02:54:09.802635 IP (tos 0x0, ttl 64, id 17252, offset 0, flags [DF], proto TCP (6), length 66) ibm.local.5900 > 10.10.0.198.1435: P, cksum 0x5d41 (correct), 117964:117990(26) ack 577 win 5840
02:54:09.803985 IP (tos 0x0, ttl 64, id 17253, offset 0, flags [DF], proto TCP (6), length 730) ibm.local.5900 > 10.10.0.198.1435: P 117990:118680(690) ack 577 win 5840
02:54:09.804770 IP (tos 0x0, ttl 128, id 14944, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x1c4b (correct), ack 117964 win 15457
02:54:09.805253 IP (tos 0x0, ttl 128, id 14945, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x1c4b (correct), ack 118680 win 14741
02:54:09.809950 IP (tos 0x0, ttl 64, id 17254, offset 0, flags [DF], proto TCP (6), length 645) ibm.local.5900 > 10.10.0.198.1435: P 118680:119285(605) ack 577 win 5840
02:54:09.810040 IP (tos 0x0, ttl 64, id 17255, offset 0, flags [DF], proto TCP (6), length 66) ibm.local.5900 > 10.10.0.198.1435: P, cksum 0x58be (correct), 119285:119311(26) ack 577 win 5840
02:54:09.811338 IP (tos 0x0, ttl 128, id 14946, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x1c4b (correct), ack 119311 win 14110
02:54:09.812349 IP (tos 0x0, ttl 64, id 17256, offset 0, flags [DF], proto TCP (6), length 549) ibm.local.5900 > 10.10.0.198.1435: P 119311:119820(509) ack 577 win 5840
02:54:09.825026 IP (tos 0x0, ttl 64, id 17257, offset 0, flags [DF], proto TCP (6), length 366) ibm.local.5900 > 10.10.0.198.1435: P 119820:120146(326) ack 577 win 5840
02:54:09.825170 IP (tos 0x0, ttl 64, id 17258, offset 0, flags [DF], proto TCP (6), length 66) ibm.local.5900 > 10.10.0.198.1435: P, cksum 0x553f (correct), 120146:120172(26) ack 577 win 5840
02:54:09.826297 IP (tos 0x0, ttl 128, id 14947, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x1c4b (correct), ack 120146 win 13275
02:54:09.827627 IP (tos 0x0, ttl 64, id 17259, offset 0, flags [DF], proto TCP (6), length 764) ibm.local.5900 > 10.10.0.198.1435: P 120172:120896(724) ack 577 win 5840
02:54:09.828759 IP (tos 0x0, ttl 64, id 17260, offset 0, flags [DF], proto TCP (6), length 812) ibm.local.5900 > 10.10.0.198.1435: P 120896:121668(772) ack 577 win 5840
02:54:09.828830 IP (tos 0x0, ttl 64, id 17261, offset 0, flags [DF], proto TCP (6), length 66) ibm.local.5900 > 10.10.0.198.1435: P, cksum 0x4e63 (correct), 121668:121694(26) ack 577 win 5840
02:54:09.828878 IP (tos 0x0, ttl 128, id 14948, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x1c4b (correct), ack 120896 win 12525
02:54:09.830208 IP (tos 0x0, ttl 128, id 14949, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x1c4b (correct), ack 121694 win 11727
02:54:09.830261 IP (tos 0x0, ttl 64, id 17262, offset 0, flags [DF], proto TCP (6), length 784) ibm.local.5900 > 10.10.0.198.1435: P 121694:122438(744) ack 577 win 5840
02:54:09.831118 IP (tos 0x0, ttl 64, id 17263, offset 0, flags [DF], proto TCP (6), length 642) ibm.local.5900 > 10.10.0.198.1435: P 122438:123040(602) ack 577 win 5840
02:54:09.831194 IP (tos 0x0, ttl 64, id 17264, offset 0, flags [DF], proto TCP (6), length 73) ibm.local.5900 > 10.10.0.198.1435: P, cksum 0x6407 (correct), 123040:123073(33) ack 577 win 5840
02:54:09.832840 IP (tos 0x0, ttl 128, id 14950, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x1c4b (correct), ack 123040 win 10381
02:54:09.833713 IP (tos 0x0, ttl 64, id 17265, offset 0, flags [DF], proto TCP (6), length 800) ibm.local.5900 > 10.10.0.198.1435: P 123073:123833(760) ack 577 win 5840
02:54:09.834723 IP (tos 0x0, ttl 64, id 17266, offset 0, flags [DF], proto TCP (6), length 799) ibm.local.5900 > 10.10.0.198.1435: P 123833:124592(759) ack 577 win 5840
02:54:09.834788 IP (tos 0x0, ttl 64, id 17267, offset 0, flags [DF], proto TCP (6), length 95) ibm.local.5900 > 10.10.0.198.1435: P 124592:124647(55) ack 577 win 5840
02:54:09.834929 IP (tos 0x0, ttl 64, id 17268, offset 0, flags [DF], proto TCP (6), length 150) ibm.local.5900 > 10.10.0.198.1435: P 124647:124757(110) ack 577 win 5840
02:54:09.835013 IP (tos 0x0, ttl 128, id 14951, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x1c4b (correct), ack 123833 win 9588
02:54:09.836329 IP (tos 0x0, ttl 128, id 14952, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1435 > ibm.local.5900: ., cksum 0x1c4b (correct), ack 124647 win 8774
02:54:09.878236 arp who-has ibm.local tell 10.10.0.200

281 packets captured
995 packets received by filter
645 packets dropped by kernel

```

---

### Post by p1ruj3 on 2008-09-01
here is a good eth0 tcpdump without vnc open right before it dc's

tcpdump -i eth0 -v
```

tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
03:00:47.334025 IP (tos 0x0, ttl 64, id 64902, offset 0, flags [none], proto TCP (6), length 378) 10.10.0.199.50989 > l1.ycs.vip.s1s.yahoo.com.www: FP 748079974:748080312(338) ack 1348830690 win 65535
03:00:56.824301 IP (tos 0x0, ttl 64, id 40666, offset 0, flags [none], proto TCP (6), length 52) 10.10.0.199.50988 > feijoa.canonical.com.www: F, cksum 0x210a (correct), 3148617127:3148617127(0) ack 96332951 win 65535 <nop,nop,timestamp 1138 820564120>
03:00:58.850252 IP (tos 0x0, ttl 128, id 23963, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1544 > feijoa.canonical.com.www: F, cksum 0x3bd3 (correct), 1129745940:1129745940(0) ack 2923423163 win 17321
03:01:25.135557 IP (tos 0x0, ttl 64, id 59839, offset 0, flags [none], proto TCP (6), length 187) 10.10.0.199.50983 > service.playstation.net.5223: FP 2094634239:2094634374(135) ack 2869340140 win 65535 <nop,nop,timestamp 808 3307167024>
03:01:30.785857 IP (tos 0x0, ttl 64, id 61545, offset 0, flags [none], proto TCP (6), length 261) 10.10.0.199.50978 > 129.250.131.15.www: FP 3239382218:3239382427(209) ack 2740801081 win 65535 <nop,nop,timestamp 764 2903396291>

```

here is some wierd things i saw, maybe this might help too.... 
```

tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
02:59:42.668246 arp who-has 10.10.0.198 tell ibm.local
02:59:42.669267 arp reply 10.10.0.198 is-at 00:13:ce:a3:d4:bf (oui Unknown)
02:59:42.772337 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70) ibm.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 198.0.10.10.in-addr.arpa. (42)
02:59:43.330896 IP (tos 0x0, ttl 64, id 62168, offset 0, flags [none], proto TCP (6), length 378) 10.10.0.199.50989 > 209.73.191.242.www: FP 748079974:748080312(338) ack 1348830690 win 65535
02:59:43.330981 IP (tos 0xc0, ttl 64, id 1103, offset 0, flags [none], proto ICMP (1), length 406) ibm.local > 10.10.0.199: ICMP net 209.73.191.242 unreachable, length 386
	IP (tos 0x0, ttl 64, id 62168, offset 0, flags [none], proto TCP (6), length 378) 10.10.0.199.50989 > 209.73.191.242.www: FP 0:338(338) ack 1 win 65535[|icmp]
02:59:43.776337 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70) ibm.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 198.0.10.10.in-addr.arpa. (42)
02:59:44.895152 arp who-has ibm.local tell 10.10.0.200
02:59:44.895195 arp reply ibm.local is-at 00:09:6b:5f:34:88 (oui Unknown)
02:59:44.897661 IP (tos 0x0, ttl 1, id 43910, offset 0, flags [none], proto ICMP (1), length 33) 10.10.0.200 > ibm.local: ICMP echo request, id 768, seq 21024, length 13
02:59:44.897748 IP (tos 0x0, ttl 64, id 57307, offset 0, flags [none], proto ICMP (1), length 33) ibm.local > 10.10.0.200: ICMP echo reply, id 768, seq 21024, length 13
02:59:45.780325 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70) ibm.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 198.0.10.10.in-addr.arpa. (42)
02:59:47.776307 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 68) ibm.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 1.0.10.10.in-addr.arpa. (40)
02:59:47.776535 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 85) ibm.local.mdns > 224.0.0.251.mdns: 0*- [0q] 1/0/0 1.0.10.10.in-addr.arpa. (Cache flush) PTR[|domain]
02:59:47.880302 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70) ibm.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
02:59:48.884316 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 70) ibm.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
02:59:49.239242 IP (tos 0x0, ttl 128, id 23952, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1544 > feijoa.canonical.com.www: F, cksum 0x3bd3 (correct), 1129745940:1129745940(0) ack 2923423163 win 17321
02:59:49.239302 IP (tos 0xc0, ttl 64, id 29618, offset 0, flags [none], proto ICMP (1), length 68) ibm.local > 10.10.0.198: ICMP net feijoa.canonical.com unreachable, length 48
	IP (tos 0x0, ttl 128, id 23952, offset 0, flags [DF], proto TCP (6), length 40) 10.10.0.198.1544 > feijoa.canonical.com.www: F, cksum 0x3bd3 (correct), 0:0(0) ack 1 win 17321
02:59:49.896204 arp who-has 10.10.0.200 tell ibm.local
02:59:49.898264 arp reply 10.10.0.200 is-at 00:13:ce:4b:f1:f0 (oui Unknown)

```

---

### Post by p1ruj3 on 2008-09-01
ok after i set it as authoritative and made sure the subnet was 255.255.255.0 the connections seems solid... i will post if i have any other issues thanks so much dmizer and homie from south africa

cat /etc/dhcpd.conf 
```

# DHCP configuration generated by Firestarter

subnet 10.10.0.0 netmask 255.255.255.0 {
authoritative
	option routers 10.10.0.1;
	option subnet-mask 255.255.255.0;
	option domain-name-servers 66.174.92.14;
	option ip-forwarding on;
	range dynamic-bootp 10.10.0.100 10.10.0.200;
	default-lease-time 21600;
	max-lease-time 43200;
}

```

---

### Post by mellowd on 2008-09-01
Ah good to hear.

---

### Post by p1ruj3 on 2008-09-01
ok still not resolved here is the latest logs right during a disconnect
```

Sep  1 12:53:07 ibm pppd[6324]: Script /etc/ppp/ip-up finished (pid 6343), status = 0x0
Sep  1 14:19:14 ibm pppd[6324]: rcvd [LCP TermReq id=0xae]
Sep  1 14:19:14 ibm pppd[6324]: Script /etc/ppp/ip-down started (pid 7360)
Sep  1 14:19:14 ibm pppd[6324]: sent [LCP TermAck id=0xae]
Sep  1 14:19:15 ibm pppd[6324]: Script /etc/ppp/ip-down finished (pid 7360), status = 0x1
Sep  1 14:19:49 ibm pppd[6324]: using channel 2
Sep  1 14:19:50 ibm pppd[6324]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0xb62b99e7> <pcomp> <accomp>]
Sep  1 14:19:50 ibm pppd[6324]: rcvd [LCP ConfReq id=0xaf <mru 1500> <asyncmap 0x0> <magic 0x8f4aa38d> <pcomp> <accomp>]
Sep  1 14:19:50 ibm pppd[6324]: sent [LCP ConfAck id=0xaf <mru 1500> <asyncmap 0x0> <magic 0x8f4aa38d> <pcomp> <accomp>]
Sep  1 14:19:50 ibm pppd[6324]: rcvd [LCP ConfAck id=0x2 <asyncmap 0x0> <magic 0xb62b99e7> <pcomp> <accomp>]
Sep  1 14:19:50 ibm pppd[6324]: sent [CCP ConfReq id=0x2 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Sep  1 14:19:50 ibm pppd[6324]: sent [IPCP ConfReq id=0x4 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 14:19:50 ibm pppd[6324]: rcvd [LCP DiscReq id=0xb0 magic=0x8f4aa38d]
Sep  1 14:19:50 ibm pppd[6324]: rcvd [LCP ProtRej id=0xb1 80 fd 01 02 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Sep  1 14:19:50 ibm pppd[6324]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Sep  1 14:19:50 ibm pppd[6324]: rcvd [IPCP ConfReq id=0x2e <addr 66.174.66.4>]
Sep  1 14:19:50 ibm pppd[6324]: sent [IPCP ConfAck id=0x2e <addr 66.174.66.4>]
Sep  1 14:19:50 ibm pppd[6324]: rcvd [IPCP ConfRej id=0x4 <compress VJ 0f 01>]
Sep  1 14:19:50 ibm pppd[6324]: sent [IPCP ConfReq id=0x5 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 14:19:50 ibm pppd[6324]: rcvd [IPCP ConfNak id=0x5 <addr 70.209.102.48> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 14:19:50 ibm pppd[6324]: sent [IPCP ConfReq id=0x6 <addr 70.209.102.48> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 14:19:50 ibm pppd[6324]: rcvd [IPCP ConfAck id=0x6 <addr 70.209.102.48> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 14:19:50 ibm pppd[6324]: Script /etc/ppp/ip-up started (pid 7467)
Sep  1 14:20:00 ibm pppd[6324]: Script /etc/ppp/ip-up finished (pid 7467), status = 0x0

```

as you can see i have a more solid connect time, i wasnt using the network much though....
```

Sep  1 13:49:58 ibm dhcpd: DHCPREQUEST for 10.10.0.197 from 00:26:54:0e:b2:8c (goldun) via eth0
Sep  1 13:49:58 ibm dhcpd: DHCPACK on 10.10.0.197 to 00:26:54:0e:b2:8c (goldun) via eth0
Sep  1 13:50:16 ibm kernel: [ 3725.754623] Inbound IN=ppp0 OUT= MAC= SRC=218.10.111.106 DST=70.219.15.40 LEN=40 TOS=0x00 PREC=0x00 TTL=109 ID=256 DF PROTO=TCP SPT=12200 DPT=8000 WINDOW=8192 RES=0x00 SYN URGP=0 
Sep  1 13:57:21 ibm kernel: [ 4150.802522] Inbound IN=ppp0 OUT= MAC= SRC=92.62.101.23 DST=70.219.15.40 LEN=48 TOS=0x00 PREC=0x00 TTL=98 ID=23485 PROTO=TCP SPT=25432 DPT=1080 WINDOW=65535 RES=0x00 SYN URGP=0 
Sep  1 14:00:00 ibm kernel: [ 4310.011856] Inbound IN=ppp0 OUT= MAC= SRC=24.64.245.187 DST=70.219.15.40 LEN=516 TOS=0x00 PREC=0x00 TTL=63 ID=47029 PROTO=UDP SPT=17901 DPT=1028 LEN=496 
Sep  1 14:07:50 ibm kernel: [ 4779.980039] Inbound IN=ppp0 OUT= MAC= SRC=24.64.81.84 DST=70.219.15.40 LEN=516 TOS=0x00 PREC=0x00 TTL=63 ID=60912 PROTO=UDP SPT=24885 DPT=1028 LEN=496 
Sep  1 14:13:39 ibm kernel: [ 5129.090500] Inbound IN=ppp0 OUT= MAC= SRC=24.64.74.6 DST=70.219.15.40 LEN=516 TOS=0x00 PREC=0x00 TTL=63 ID=57966 PROTO=UDP SPT=11466 DPT=1028 LEN=496 
Sep  1 14:17:01 ibm CRON[7334]: User account has expired
Sep  1 14:19:14 ibm pppd[6324]: rcvd [LCP TermReq id=0xae]
Sep  1 14:19:14 ibm pppd[6324]: LCP terminated by peer
Sep  1 14:19:14 ibm pppd[6324]: Connect time 86.3 minutes.

```

---

### Post by dmizer on 2008-09-01
I really don't see anything strange in your logs, just regular packet transfer.

You may have better results if you do not use firestarter for configuring ICS, but you have a WAN IP, so I certainly understand wanting to run a completely configured firewall.

You may also get good resulst if you disable NetworkManager. Disabling NetworkManager will cause you to loose the network configuration icon in your system tray, and it's also difficult to re-enable it once it's been disabled. However, you can still configure your network quite easily by going to system > administration > network.

Disable network manager: [https://help.ubuntu.com/community/NetworkManager#Disabling](https://help.ubuntu.com/community/NetworkManager#Disabling) NetworkManager

---

### Post by p1ruj3 on 2008-09-01
man so annoying, random disconnects.. maybe this shows something... 
```

Sep  1 21:33:41 ibm pppd[6115]: sent [LCP ConfReq id=0x4 <asyncmap 0x0> <magic 0xc0fb85bb> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP ConfReq id=0xc <mru 1500> <asyncmap 0x0> <magic 0x90d7d2b8> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: sent [LCP ConfAck id=0xc <mru 1500> <asyncmap 0x0> <magic 0x90d7d2b8> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP ConfAck id=0x4 <asyncmap 0x0> <magic 0xc0fb85bb> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: sent [CCP ConfReq id=0x4 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfReq id=0xa <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP DiscReq id=0xd magic=0x90d7d2b8]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfReq id=0x3 <addr 66.174.66.4>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfAck id=0x3 <addr 66.174.66.4>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP ProtRej id=0xe 80 fd 01 04 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Sep  1 21:33:41 ibm pppd[6115]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfRej id=0xa <compress VJ 0f 01>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfReq id=0xb <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfNak id=0xb <addr 70.209.197.161> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfReq id=0xc <addr 70.209.197.161> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfAck id=0xc <addr 70.209.197.161> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]

```

---

### Post by dmizer on 2008-09-01
How many clients do you have connected to your Ubuntu gateway?

Do you have a crossover cable? If so, try bypassing the dlink and going direct.  See if the problem is maybe the dlink.

---

### Post by p1ruj3 on 2008-09-02
one thing i thought of is it might be in my pppd chatscripts or connect script.... at this point i might have overlooked something in there not truely understanding whats goin on and relying on google to help me get it correct, anything noticable in there to try adding / removing?

just have no clue whats causing the lcp term req.... it seems disable'n nat on my dlink helped on connectivity just for webbrowsing, but when i try to download anything or open a few windows, or god forbid sign on to the playstation network it drops right away.... at one point i had it working just fine but my hd died and i cannot seem to get it back to the way it was (even with my double nats...somehow hahaha) super thanks in advance for all the help guys!!!

---

### Post by p1ruj3 on 2008-09-02
man so annoying, random disconnects.. maybe this shows something... 
```

Sep  1 21:33:41 ibm pppd[6115]: sent [LCP ConfReq id=0x4 <asyncmap 0x0> <magic 0xc0fb85bb> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP ConfReq id=0xc <mru 1500> <asyncmap 0x0> <magic 0x90d7d2b8> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: sent [LCP ConfAck id=0xc <mru 1500> <asyncmap 0x0> <magic 0x90d7d2b8> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP ConfAck id=0x4 <asyncmap 0x0> <magic 0xc0fb85bb> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: sent [CCP ConfReq id=0x4 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfReq id=0xa <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP DiscReq id=0xd magic=0x90d7d2b8]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfReq id=0x3 <addr 66.174.66.4>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfAck id=0x3 <addr 66.174.66.4>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP ProtRej id=0xe 80 fd 01 04 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Sep  1 21:33:41 ibm pppd[6115]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfRej id=0xa <compress VJ 0f 01>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfReq id=0xb <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfNak id=0xb <addr 70.209.197.161> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfReq id=0xc <addr 70.209.197.161> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfAck id=0xc <addr 70.209.197.161> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]

```

---

### Post by p1ruj3 on 2008-09-02
i have tried a direct link, didnt seem to help, and i will try my other buffaloe router and see if that helps now that i know not to have nat enabled... seems the dlink was the only router working with two nats hahaha... for a while i assumed the buff router was bad...

---

### Post by p1ruj3 on 2008-09-02
man so annoying, random disconnects.. maybe this shows something... 
```

Sep  1 21:33:41 ibm pppd[6115]: sent [LCP ConfReq id=0x4 <asyncmap 0x0> <magic 0xc0fb85bb> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP ConfReq id=0xc <mru 1500> <asyncmap 0x0> <magic 0x90d7d2b8> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: sent [LCP ConfAck id=0xc <mru 1500> <asyncmap 0x0> <magic 0x90d7d2b8> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP ConfAck id=0x4 <asyncmap 0x0> <magic 0xc0fb85bb> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: sent [CCP ConfReq id=0x4 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfReq id=0xa <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP DiscReq id=0xd magic=0x90d7d2b8]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfReq id=0x3 <addr 66.174.66.4>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfAck id=0x3 <addr 66.174.66.4>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP ProtRej id=0xe 80 fd 01 04 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Sep  1 21:33:41 ibm pppd[6115]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfRej id=0xa <compress VJ 0f 01>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfReq id=0xb <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfNak id=0xb <addr 70.209.197.161> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfReq id=0xc <addr 70.209.197.161> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfAck id=0xc <addr 70.209.197.161> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]

```

---

### Post by dmizer on 2008-09-02
When you get disconnected:

1) Are you still able to browse the internet on the Ubuntu gateway computer?
2) Does ping (by name or by ip) work on any machine?

Look in logs other than your tcp packets.  Look in /var/log for any other events that occur around the same time as your disconnect.  Packets don't appear to be saying anything.

---

### Post by p1ruj3 on 2008-09-02
ok switched to the buffalo router, and for a second thought it fixed the problem, it seems its staying connected a little longer now but still disconnecting 
```

Sep  1 22:48:40 ibm pppd[6115]: rcvd [LCP TermReq id=0x7f]
Sep  1 22:48:40 ibm pppd[6115]: LCP terminated by peer
Sep  1 22:48:40 ibm pppd[6115]: Connect time 2.6 minutes.
Sep  1 22:48:40 ibm pppd[6115]: Sent 93355 bytes, received 4460138 bytes.
Sep  1 22:48:40 ibm dnsmasq[5101]: reading /etc/resolv.conf
Sep  1 22:48:40 ibm dnsmasq[5101]: using nameserver 66.174.95.44#53
Sep  1 22:48:40 ibm dnsmasq[5101]: using nameserver 66.174.92.14#53
Sep  1 22:48:40 ibm pppd[6115]: Script /etc/ppp/ip-down started (pid 1224)
Sep  1 22:48:40 ibm pppd[6115]: sent [LCP TermAck id=0x7f]

Sep  1 22:49:15 ibm pppd[6115]: rcvd [LCP DiscReq id=0x81 magic=0x911d0135]

Sep  1 22:45:31 ibm pppd[6115]: rcvd [LCP TermReq id=0x7b]
Sep  1 22:45:31 ibm pppd[6115]: LCP terminated by peer
Sep  1 22:45:31 ibm pppd[6115]: Connect time 10.0 minutes.
Sep  1 22:45:31 ibm pppd[6115]: Sent 586154 bytes, received 18189850 bytes.

```

as you can see i switched it right around 35 and it lasted 10 minutes after that, now its back to its usual dc'n in less then a minute.....

i am just copy pasting what seems odd to me... let me know what i can show you to help...

```

 Sep  1 22:49:15 ibm pppd[6115]: rcvd [IPCP ConfRej id=0x61 <compress VJ 0f 01>]
Sep  1 22:49:15 ibm pppd[6115]: sent [IPCP ConfReq id=0x62 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 22:49:15 ibm pppd[6115]: rcvd [IPCP ConfNak id=0x62 <addr 70.209.117.166> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 22:49:15 ibm pppd[6115]: sent [IPCP ConfReq id=0x63 <addr 70.209.117.166> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 22:49:15 ibm pppd[6115]: rcvd [IPCP ConfAck id=0x63 <addr 70.209.117.166> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]

```
yeah right after switch it stayed connected for 10 min... now its like declining... 10min to 2.6 to 2.6 to now 1.6....

i have (right now) two windows machines one wired, one wireless, and a playstation3 (right now wireless, i have tried wired no diff)

---

### Post by p1ruj3 on 2008-09-02
no when its dc/d no  browsing on ubuntu computer (i do ping tests and it shows pinging then unreachable etc... and pinging is working between network because i have a vnc session that remains open while its dc'n the ppp0

---

### Post by dmizer on 2008-09-02
What adapter are you using for your ppp0?

---

### Post by p1ruj3 on 2008-09-02
these are rougly started and stopped at same time...
```

airdog@ibm:~$ ping 10.10.0.199
PING 10.10.0.199 (10.10.0.199) 56(84) bytes of data.
64 bytes from 10.10.0.199: icmp_seq=1 ttl=255 time=1.34 ms
64 bytes from 10.10.0.199: icmp_seq=2 ttl=255 time=1.37 ms
64 bytes from 10.10.0.199: icmp_seq=3 ttl=255 time=2.45 ms
64 bytes from 10.10.0.199: icmp_seq=4 ttl=255 time=1.41 ms
64 bytes from 10.10.0.199: icmp_seq=5 ttl=255 time=5.10 ms
64 bytes from 10.10.0.199: icmp_seq=6 ttl=255 time=6.37 ms
64 bytes from 10.10.0.199: icmp_seq=7 ttl=255 time=1.45 ms
64 bytes from 10.10.0.199: icmp_seq=8 ttl=255 time=1.32 ms
64 bytes from 10.10.0.199: icmp_seq=9 ttl=255 time=2.12 ms
64 bytes from 10.10.0.199: icmp_seq=10 ttl=255 time=1.35 ms
64 bytes from 10.10.0.199: icmp_seq=11 ttl=255 time=1.63 ms
64 bytes from 10.10.0.199: icmp_seq=12 ttl=255 time=2.99 ms
64 bytes from 10.10.0.199: icmp_seq=13 ttl=255 time=4.32 ms
64 bytes from 10.10.0.199: icmp_seq=14 ttl=255 time=5.62 ms
64 bytes from 10.10.0.199: icmp_seq=15 ttl=255 time=1.98 ms
64 bytes from 10.10.0.199: icmp_seq=16 ttl=255 time=1.34 ms
64 bytes from 10.10.0.199: icmp_seq=17 ttl=255 time=1.34 ms
64 bytes from 10.10.0.199: icmp_seq=18 ttl=255 time=1.35 ms
64 bytes from 10.10.0.199: icmp_seq=19 ttl=255 time=1.41 ms
64 bytes from 10.10.0.199: icmp_seq=20 ttl=255 time=2.18 ms
64 bytes from 10.10.0.199: icmp_seq=21 ttl=255 time=3.49 ms
64 bytes from 10.10.0.199: icmp_seq=22 ttl=255 time=4.82 ms
64 bytes from 10.10.0.199: icmp_seq=23 ttl=255 time=1.35 ms
64 bytes from 10.10.0.199: icmp_seq=24 ttl=255 time=1.38 ms
64 bytes from 10.10.0.199: icmp_seq=25 ttl=255 time=1.34 ms
64 bytes from 10.10.0.199: icmp_seq=26 ttl=255 time=1.32 ms
64 bytes from 10.10.0.199: icmp_seq=27 ttl=255 time=3.49 ms
64 bytes from 10.10.0.199: icmp_seq=28 ttl=255 time=1.44 ms
64 bytes from 10.10.0.199: icmp_seq=29 ttl=255 time=2.65 ms
64 bytes from 10.10.0.199: icmp_seq=30 ttl=255 time=3.98 ms
64 bytes from 10.10.0.199: icmp_seq=31 ttl=255 time=1.78 ms
64 bytes from 10.10.0.199: icmp_seq=32 ttl=255 time=1.28 ms
64 bytes from 10.10.0.199: icmp_seq=33 ttl=255 time=1.27 ms
64 bytes from 10.10.0.199: icmp_seq=34 ttl=255 time=1.37 ms
64 bytes from 10.10.0.199: icmp_seq=35 ttl=255 time=1.43 ms
64 bytes from 10.10.0.199: icmp_seq=36 ttl=255 time=2.89 ms
64 bytes from 10.10.0.199: icmp_seq=37 ttl=255 time=1.87 ms
64 bytes from 10.10.0.199: icmp_seq=38 ttl=255 time=1.36 ms

--- 10.10.0.199 ping statistics ---
38 packets transmitted, 38 received, 0% packet loss, time 37014ms
rtt min/avg/max/mdev = 1.278/2.292/6.378/1.370 ms


64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=32 ttl=235 time=334 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=33 ttl=235 time=250 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=34 ttl=235 time=251 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=35 ttl=235 time=252 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=36 ttl=235 time=266 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=37 ttl=235 time=243 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=38 ttl=235 time=270 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=39 ttl=235 time=264 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=40 ttl=235 time=264 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=41 ttl=235 time=251 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=42 ttl=235 time=257 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=43 ttl=235 time=391 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=44 ttl=235 time=257 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=45 ttl=235 time=268 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=46 ttl=235 time=365 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=47 ttl=235 time=710 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=48 ttl=235 time=424 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=49 ttl=235 time=319 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=50 ttl=235 time=354 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=51 ttl=235 time=318 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=52 ttl=235 time=336 ms
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=91 ttl=235 time=257 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=92 ttl=235 time=257 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=93 ttl=235 time=270 ms

--- google.com ping statistics ---
93 packets transmitted, 55 received, 40% packet loss, time 97117ms
rtt min/avg/max/mdev = 228.678/285.907/710.646/69.264 ms

```

---

### Post by p1ruj3 on 2008-09-02
usb720 - tell me what command to give you most information on it..(modprobe, lsusb)

[ 3522.020399] usb 2-2: USB disconnect, address 2
[ 3522.021741] option 2-2:1.0: device disconnected
[ 3522.022300] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 3522.024637] option 2-2:1.1: device disconnected
[ 7635.202521] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 7637.747607] usb 2-2: new full speed USB device using uhci_hcd and address 3
[ 3523.827140] usb 2-2: configuration #1 chosen from 1 choice
[ 3523.832968] option 2-2:1.0: GSM modem (1-port) converter detected
[ 3523.833223] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 3523.838424] option 2-2:1.1: GSM modem (1-port) converter detected
[ 3523.838649] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1

---

### Post by p1ruj3 on 2008-09-02
man so annoying, random disconnects.. maybe this shows something... 

```

Sep  1 21:33:41 ibm pppd[6115]: sent [LCP ConfReq id=0x4 <asyncmap 0x0> <magic 0xc0fb85bb> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP ConfReq id=0xc <mru 1500> <asyncmap 0x0> <magic 0x90d7d2b8> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: sent [LCP ConfAck id=0xc <mru 1500> <asyncmap 0x0> <magic 0x90d7d2b8> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP ConfAck id=0x4 <asyncmap 0x0> <magic 0xc0fb85bb> <pcomp> <accomp>]
Sep  1 21:33:41 ibm pppd[6115]: sent [CCP ConfReq id=0x4 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfReq id=0xa <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP DiscReq id=0xd magic=0x90d7d2b8]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfReq id=0x3 <addr 66.174.66.4>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfAck id=0x3 <addr 66.174.66.4>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [LCP ProtRej id=0xe 80 fd 01 04 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Sep  1 21:33:41 ibm pppd[6115]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfRej id=0xa <compress VJ 0f 01>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfReq id=0xb <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfNak id=0xb <addr 70.209.197.161> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 21:33:41 ibm pppd[6115]: sent [IPCP ConfReq id=0xc <addr 70.209.197.161> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]
Sep  1 21:33:41 ibm pppd[6115]: rcvd [IPCP ConfAck id=0xc <addr 70.209.197.161> <ms-dns1 66.174.92.14> <ms-dns3 66.174.95.44>]

```

---

### Post by p1ruj3 on 2008-09-02
i bought a usb727 (the newer evdo card from verizon wireless for 350$ but i guess its not supported till ubuntu 's october release....)

maybe im not monitoring the right logs... here is whats showing up in my log viewer

/var/log/debug
auth
daemon
kern
message
syslog
user
xorg

---

### Post by p1ruj3 on 2008-09-02
i bought a usb727 (the newer evdo card from verizon wireless for 350$ but i guess its not supported till ubuntu 's october release....)

---

### Post by p1ruj3 on 2008-09-02
it might just be when i dc the eth0 cord i just dont request that much data being sent on the ubuntu machine to drop the connection 

```

Sep  1 23:14:38 ibm pppd[6115]: Connect: ppp0 <--> /dev/ttyUSB0
Sep  1 23:14:39 ibm pppd[6115]: local  IP address 70.209.20.73
Sep  1 23:14:39 ibm pppd[6115]: remote IP address 66.174.66.4
Sep  1 23:14:39 ibm pppd[6115]: primary   DNS address 66.174.92.14
Sep  1 23:14:39 ibm pppd[6115]: secondary DNS address 66.174.95.44
Sep  1 23:19:34 ibm kernel: [ 8923.191933] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Sep  1 23:20:58 ibm pppd[6115]: LCP terminated by peer
Sep  1 23:20:58 ibm pppd[6115]: Connect time 6.4 minutes.
Sep  1 23:20:58 ibm pppd[6115]: Sent 135723 bytes, received 606065 bytes.

```

but you can see how its stable then i plug it in and it drops ina minute....
i have it about narrowed down to the pppd config or my eth0 card on this machine... those are my two top guesses now, i have a wireless card on the ubuntu machine maybe ill try to do the ics through that and see if it matters take away the possiblity of a bad eth0 or cord (even though pings suggest its not that from my previous post)

---

### Post by p1ruj3 on 2008-09-02
ok i tried two different wireless cards, got the ics working with both of them, and still random disconnects... 

i also tried for the heck of it another cable, and still dc'd

so at this time i feel i have narrowed it down to my ppp configuration. any help looking over what i got witht hat would be greatly appreciated!!!!

---

### Post by jimv on 2008-09-02
If I had to bet, I'd put my money on crappy phone lines/noise on the lines.

---

### Post by dmizer on 2008-09-02
Your replies to your own thread are getting excessive. If you have new relavant information, it's helpful to edit your post. Also, please wrap lengthy terminal output in [noparse]```

```[/noparse] brackets so the posts don't get so long.

Earlier, I asked you to post the output of:
```
lshw -C network
```
Does your USB adapter not show up in that output?

Do not post the entire output of this command, but look for information on your USB adapter here:
```
sudo lshw
```

---

### Post by p1ruj3 on 2008-09-02
Jimv, its a pure wireless ppp0 connection, no phone lines noise, etc...

sorry for lengthy posts..... i am just learning this forum platform..... and with the connection dropping it double posted a few times i think... i did the ls -C network output on page 3, i dont see any usb information in there let me try the other one and try to find relavent info

```
 
 *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=80 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:09:6b:5f:34:88
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=10.10.0.1 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

```

i did not see anything with my usb device there, i would post the entire thing butyou directed me not too, if you want me to paste the usb controller information let me know, but nothing on the adapter...

lsusb
```

lsusb 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1410:2110  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```


one other feeling i have is i might have my subnet mask not perfect in my config on the ubuntu machine if you could double check it i'd appreciate it.... (im getting wierd authoritative msgs still 

Sep  2 10:43:34 ibm dhcpd: DHCPINFORM from 10.10.0.200 via eth0: not authoritative for subnet 10.0.0.0

here is all my config stuff i can think of

```

/etc/hosts
127.0.0.1 localhost
127.0.1.1 ibm


/etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback


iface eth0 inet static
address 10.10.0.1
netmask 255.255.255.0

auto eth0

/etc/dhcp3/dhcpd.conf
subnet 10.0.0.0 netmask 255.0.0.0 {
authoritative;
        option routers 10.10.0.1;
        option subnet-mask 255.255.255.0;
        option domain-name-servers 66.174.92.14;
        option ip-forwarding on;
        range dynamic-bootp 10.10.0.100 10.10.0.200;
        default-lease-time 21600;
        max-lease-time 43200;
}

```
is that correct having the auth inside the brackets? i also notice i have a /etc/dhcpd.conf not sure which one is being used so i have them both identical

i guess to clarify my question here which one is best
```

a:
subnet 10.0.0.0 netmask 255.0.0.0 {

b:
subnet 10.10.0.0 netmask 255.255.255.0 {

``` seems in school we spent more time understanding 255.255.255.248 etc and my understanding of subnets is poor (but i guess its all in comparrison to whom.... haha thanks so much... connection does seem a lot more solid now with only one nat machine, and the buffalo router it has remained connected on idle for several hours now thats a major improvement)

---

### Post by dmizer on 2008-09-02
Well, here's what I'm looking for:

1) Since you can ping across your local network, that means the problem is not on your eth0.
2) Since you can ping across your local network, this also means that the problem is not likely to be your ICS configuration.
3) Since you cannot ping the internet from any machine (ICS gateway included), this means that the problem is either the USB adapter or some other piece of equipment between the Ubuntu gateway and the internet.

Possible causes for problem three include (but are not limited to):
1) Poorly written drivers (for your USB adapter).
2) Bad/flaky hardware (including the USB adapter)
3) Bad lines
4) A combination of all of the above.

I made some brief searches for the information your adapter and lost connection, but didn't come up with anything solid.

---

### Post by p1ruj3 on 2008-09-03
ok sounds good... appreciate the help...
as far as getting in touch with those responsible for the drivers to fix any issues i may have dug up, how do i go about doing that?  the next release of ubuntu should support the updated usb card i purchased....not everyone has that luxury though...

it seems now my other machines in windows browse and send email just fine, the only machine which has issues using its browser or downloading from playstation store is my playstation 3.... so far madden 09 has completed 3 full games so far with out a disconnect, but as soon as i load the browser up to refresh this page, it dropped the connection..... does the term_disq id number refer to anything???

sorry for this problem i live in the mountains in colorado and this is my only option for internet period....besides isdn which is i afforded for years getting ripped off at 128/128 at 12k dl's where this wireless ppp0 connection ive seen speeds at 150k, just super frusterating the documentation on this wireless evdo card and the chatscripts etc is all hearsay and i peace togeather its settings from sprint and verizon usa and europe ideas over google with very limited knowledge to begin with from the man pages

again thank you

here is a few things that i cannot understand... same settings it stayed connected and downloaded 800mbs of ubuntu updates once i dc'd the eth0 cord... thats why i assumed it was a iptables issue, not drivers/faulty ppp adapter..... i have switched out to pure wireless communications so that eliminates bad lines cause its all wireless, i have done over 30gigs of usage in past 26 days...  i figured there has to be some log of errors showings whats up and all i get is random 

lcp term req id=*x**

i am just noticing this over and over in my logs, is it an issue????
```
 
Sep  2 23:06:07 ibm kernel: [83154.717320] Inbound IN=eth0 OUT= MAC=00:09:6b:5f:34:88:00:13:ce:4b:f1:f0:08:00 SRC=10.10.0.200 DST=10.10.0.1 LEN=33 TOS=0x00 PREC=0x00 TTL=1 ID=28009 PROTO=ICMP TYPE=8 CODE=0 ID=768 SEQ=34104 
Sep  2 23:06:08 ibm kernel: [38364.991135] Inbound IN=eth0 OUT= MAC=00:09:6b:5f:34:88:00:13:ce:4b:f1:f0:08:00 SRC=10.10.0.200 DST=10.10.0.1 LEN=33 TOS=0x00 PREC=0x00 TTL=1 ID=28010 PROTO=ICMP TYPE=8 CODE=0 ID=768 SEQ=34360 
Sep  2 23:06:10 ibm kernel: [83159.683056] Inbound IN=eth0 OUT= MAC=00:09:6b:5f:34:88:00:13:ce:4b:f1:f0:08:00 SRC=10.10.0.200 DST=10.10.0.1 LEN=33 TOS=0x00 PREC=0x00 TTL=1 ID=28011 PROTO=ICMP TYPE=8 CODE=0 ID=768 SEQ=34616 
Sep  2 23:06:11 ibm kernel: [83161.182552] Inbound IN=eth0 OUT= MAC=00:09:6b:5f:34:88:00:13:ce:4b:f1:f0:08:00 SRC=10.10.0.200 DST=10.10.0.1 LEN=33 TOS=0x00 PREC=0x00 TTL=1 ID=28014 PROTO=ICMP TYPE=8 CODE=0 ID=768 SEQ=34872 
Sep  2 23:06:13 ibm kernel: [83163.114645] Inbound IN=eth0 OUT= MAC=00:09:6b:5f:34:88:00:13:ce:4b:f1:f0:08:00 SRC=10.10.0.200 DST=10.10.0.1 LEN=33 TOS=0x00 PREC=0x00 TTL=1 ID=28015 PROTO=ICMP TYPE=8 CODE=0 ID=768 SEQ=35128 
Sep  2 23:06:14 ibm dhcpd: DHCPREQUEST for 10.10.0.200 from 00:13:ce:4b:f1:f0 (winxp) via eth0
Sep  2 23:06:14 ibm dhcpd: DHCPACK on 10.10.0.200 to 00:13:ce:4b:f1:f0 (winxp) via eth0
Sep  2 23:06:14 ibm dhcpd: DHCPREQUEST for 10.10.0.200 from 00:13:ce:4b:f1:f0 (winxp) via eth0
Sep  2 23:06:14 ibm dhcpd: DHCPACK on 10.10.0.200 to 00:13:ce:4b:f1:f0 (winxp) via eth0
Sep  2 23:06:14 ibm dhcpd: DHCPREQUEST for 10.10.0.200 from 00:13:ce:4b:f1:f0 (winxp) via eth0
Sep  2 23:06:14 ibm dhcpd: DHCPACK on 10.10.0.200 to 00:13:ce:4b:f1:f0 (winxp) via eth0
Sep  2 23:06:14 ibm dhcpd: DHCPREQUEST for 10.10.0.200 from 00:13:ce:4b:f1:f0 (winxp) via eth0
Sep  2 23:06:14 ibm dhcpd: DHCPACK on 10.10.0.200 to 00:13:ce:4b:f1:f0 (winxp) via eth0

```

thats a windows machine

---

### Post by p1ruj3 on 2008-09-11
I confirmed the problem with my original belief.  Anyone dealing with verizon it took me over 2 hours of heated supervisor to supervisor hopping until i finally got a guy willing to help provide me with the information i needed.  Which he in turn had their tech team monitor my connection for a a day after the ticket had to be escalated several times (over a two week process)

In the end this is the confirmed problem.  Because i have had this issue on several different ubuntu machines, i am certain it is an issue in ubuntu iptables or routing.  The bottom line is right now windows is a more stable platform for ics, which makes me sick...

The problem is its routing my lan ip's over the wan (or randomly bridging the connection rather then routing it) my terminology might be off, verizon explained it to me "it is leaking internal ip address's to our network which is why we are disconnecting you"  

this is exactly what i guessed was going on as my tcpdump logs show 
<code>
(example)
tcpdump -i ppp0 -v
10.10.0.x > google.com
</code>

I have tried setting up my ics through the tutorial, through guide + guard dog , and through firestarter and with the Genius of Dmizer looking at my setup configs i feel my configuration is correct and this is an error inside of the actual tcp/ip routing protocols of ubuntu and should be a major security risk and a sense of honor since somehow Windows XP is more reliable :confused: 

The major concern here is windows is not secure, i have had several machines get destroyed through firewalls because the wan is completely open to constant attacks, I have even had a ubuntu machine go down when i had no firewall running.

Please admins escalate this issue to the parties with the knowledge and ability to get this issue corrected, or direct me to them and i will absolutely take the time to do so.  Unfortunately i just do not have a strong enough understanding of programming to fathom where to start.

Thanks everyone, have to love the power of open source.

p.s. please feel free to correct me on my terminology so i can edit this post so others with the same issue will have a better time following and finding it.

---

### Post by dmizer on 2008-09-11
I wouldn't be so fast to blame IP tables until you've actually configured IP tables directly (without firestarter).

My suggestion to you for a next troubleshooting step would be to eliminate firestarter from the equasion, and use this howto for configuring ICS: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

I posted it earlier, but it's worth posting again. If you follow that howto there is no need for firestarter.

---

### Post by p1ruj3 on 2008-09-11
I have tried that configuring iptables directly. and decided to try firestarter, and guarddog guide dog to see if there was an error in how i configured it.

that is the exact guide i used. and i just tried it again and same problem, when i use the connection on a machine behind the ics its randomly drops... seems the higher the load i create the quicker it drops, but not always...

---

### Post by dmizer on 2008-09-11
Did you completely uninstall firestarter, and reset iptables to default before retrying the guide I posted? If not, firestarter may still be interfering.

---

### Post by p1ruj3 on 2008-09-15
yes i have, and i just did it again....

still having issues....

only thing i can think of is im not reseting iptables to defaults... whats the best way to do so?

---

### Post by dmizer on 2008-09-15
To find out if there are iptables rules in place, run this command:
```
sudo iptables -L
```
The output should look like this]
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

If there are any rules in place, you can clear them with this command:
```
sudo iptables -F
```

---

### Post by p1ruj3 on 2008-09-16
right exactly what i was doing...

i think i noticed some improved performance messing around with route add default route del commands

could it be a bug in pppd when its connecting with self setting up something bad there??? i think i got it working at one point (untill a rebooted) and the only thing i can think of is i was following your guide and on accident did the route add thing, then figured out that messed it up, then deleted it then reconnected with ppp and it seemed to be improved but for whatever reason i cannot duplicate it...

btw i did get my usb727 card vs the one i had the 720 working doing a ohci modprobe load

---

### Post by p1ruj3 on 2008-09-23
ok so i formated, installed the new xubuntu and still having issues following your guide to the T

please help!!!
iptables config 

sudo iptables -A FORWARD -i ppp0 -o eth0 -s 10.10.0.0/24 -m state --state NEW -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"


```

airdog@IBM:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
66.174.66.4     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

tcpdump of ppp0 int

22:10:37.734650 IP service.playstation.net.www > 27.sub-70-209-130.myvzw.com.49787: R 406:406(0) ack 1471 win 5850
22:10:48.124520 IP 10.10.0.199.49801 > 129.250.131.72.www: F 0:0(0) ack 1 win 65535 <nop,nop,timestamp 946 3091277687>
22:11:02.144831 IP service.playstation.net.5223 > 27.sub-70-209-130.myvzw.com.49833: P 11827:11885(58) ack 3087 win 7466 <nop,nop,timestamp 1067341799 1840>
22:11:02.226836 IP a72-247-30-176.deploy.akamaitechnologies.com.www > 27.sub-70-209-130.myvzw.com.49842: F 517:517(0) ack 196 win 6432 <nop,nop,timestamp 1520454199 8>
22:11:02.227087 IP 27.sub-70-209-130.myvzw.com.49842 > a72-247-30-176.deploy.akamaitechnologies.com.www: . ack 518 win 65535 <nop,nop,timestamp 2006 1520454199>
22:11:02.335171 IP 27.sub-70-209-130.myvzw.com.49833 > service.playstation.net.5223: . ack 11885 win 65535 <nop,nop,timestamp 1968 1067341799>
22:11:04.339433 IP 27.sub-70-209-130.myvzw.com.49833 > service.playstation.net.5223: P 3087:3116(29) ack 11885 win 65535 <nop,nop,timestamp 1976 1067341799>
22:11:04.604055 IP service.playstation.net.5223 > 27.sub-70-209-130.myvzw.com.49833: . ack 3116 win 7495 <nop,nop,timestamp 1067344832 1976>
22:11:09.455556 IP 10.10.0.199.49822 > 129.250.131.136.www: F 0:0(0) ack 1 win 65535 <nop,nop,timestamp 1872 3091210878>
22:11:44.341522 IP 27.sub-70-209-130.myvzw.com.49833 > service.playstation.net.5223: P 3116:3145(29) ack 11885 win 65535 <nop,nop,timestamp 2136 1067341799>
22:11:44.409613 IP service.playstation.net.5223 > 27.sub-70-209-130.myvzw.com.49833: P 11885:11943(58) ack 3116 win 7495 <nop,nop,timestamp 1067382009 1976>
22:11:44.607123 IP 27.sub-70-209-130.myvzw.com.49833 > service.playstation.net.5223: . ack 11943 win 65535 <nop,nop,timestamp 2136 1067382009>
22:11:44.703646 IP service.playstation.net.5223 > 27.sub-70-209-130.myvzw.com.49833: . ack 3145 win 7524 <nop,nop,timestamp 1067384921 2136>
22:11:52.127520 IP 10.10.0.199.49801 > 129.250.131.72.www: F 0:0(0) ack 1 win 65535 <nop,nop,timestamp 1202 3091277687>
22:12:13.458485 IP 10.10.0.199.49822 > 129.250.131.136.www: F 0:0(0) ack 1 win 65535 <nop,nop,timestamp 2128 3091210878>
22:12:22.043989 IP service.playstation.net.5223 > 27.sub-70-209-130.myvzw.com.49833: P 11943:12001(58) ack 3145 win 7524 <nop,nop,timestamp 1067422218 2136>
22:12:22.238891 IP 27.sub-70-209-130.myvzw.com.49833 > service.playstation.net.5223: . ack 12001 win 65535 <nop,nop,timestamp 2286 1067422218>
22:12:24.343604 IP 27.sub-70-209-130.myvzw.com.49833 > service.playstation.net.5223: P 3145:3174(29) ack 12001 win 65535 <nop,nop,timestamp 2296 1067422218>
22:12:24.621229 IP service.playstation.net.5223 > 27.sub-70-209-130.myvzw.com.49833: . ack 3174 win 7553 <nop,nop,timestamp 1067424830 2296>
22:12:56.130473 IP 10.10.0.199.49801 > 129.250.131.72.www: F 0:0(0) ack 1 win 65535 <nop,nop,timestamp 1458 3091277687>
22:13:02.222599 IP service.playstation.net.5223 > 27.sub-70-209-130.myvzw.com.49833: P 12001:12059(58) ack 3174 win 7553 <nop,nop,timestamp 1067462427 2296>
22:13:02.420752 IP 27.sub-70-209-130.myvzw.com.49833 > service.playstation.net.5223: . ack 12059 win 65535 <nop,nop,timestamp 2448 1067462427>
22:13:04.345755 IP 27.sub-70-209-130.myvzw.com.49833 > service.playstation.net.5223: P 3174:3203(29) ack 12059 win 65535 <nop,nop,timestamp 2456 1067462427>
22:13:04.621819 IP service.playstation.net.5223 > 27.sub-70-209-130.myvzw.com.49833: . ack 3203 win 7582 <nop,nop,timestamp 1067464827 2456>
22:13:07.964137 IP service.playstation.net.5223 > 27.sub-70-209-130.myvzw.com.49833: P 12059:12845(786) ack 3203 win 7582 <nop,nop,timestamp 1067468051 2456>
22:13:08.161007 IP 27.sub-70-209-130.myvzw.com.49833 > service.playstation.net.5223: . ack 12845 win 65535 <nop,nop,timestamp 2470 1067468051>
22:13:13.175148 IP 27.sub-70-209-130.myvzw.com.1025 > 192.168.0.90.snmp:  GetRequest(63)  25.3.2.1.5.1 [|snmp]
22:13:17.461456 IP 10.10.0.199.49822 > 129.250.131.136.www: F 0:0(0) ack 1 win 65535 <nop,nop,timestamp 2384 3091210878>
22:13:17.498104 IP 27.sub-70-209-130.myvzw.com.49833 > service.playstation.net.5223: P 3203:3504(301) ack 12845 win 65535 <nop,nop,timestamp 2508 1067468051>
22:13:17.789998 IP service.playstation.net.5223 > 27.sub-70-209-130.myvzw.com.49833: . ack 3504 win 7883 <nop,nop,timestamp 1067477992 2508>
22:13:17.967447 IP 10.10.0.199.49842 > a72-247-30-176.deploy.akamaitechnologies.com.www: F 787971390:787971390(0) ack 2275513981 win 65535 <nop,nop,timestamp 2550 1520454199>
22:13:17.973897 IP 27.sub-70-209-130.myvzw.com.49833 > service.playstation.net.5223: P 3504:3565(61) ack 12845 win 65535 <nop,nop,timestamp 2510 1067468051>
22:13:18.134954 IP 27.sub-70-209-130.myvzw.com.49833 > service.playstation.net.5223: FP 3565:3610(45) ack 12845 win 65535 <nop,nop,timestamp 2510 1067468051>
22:13:18.135687 IP 10.10.0.199.49790 > 129.250.131.111.www: F 548029501:548029501(0) ack 1321115227 win 65535 <nop,nop,timestamp 822 3091968512>
22:13:19.523365 IP 27.sub-70-209-130.myvzw.com.1025 > 192.168.0.90.snmp:  GetRequest(63)  25.3.2.1.5.1 [|snmp]
tcpdump: pcap_loop: recvfrom: Network is down
242423 packets captured
248899 packets received by filter
6476 packets dropped by kernel
 

``` you can see the 10.10.0.199's being sent out

---

### Post by dmizer on 2008-09-23
You should try monitoring your wireless signal strength. It's possible that your wireless is getting disconnected because of interferene or because of a weak driver.

---

### Post by p1ruj3 on 2008-09-23
so my -i and -o are correct for following that tutorial? signal is fine... its the stupid reserved ips being sent out the ppp0 interface thats dc'n me

---

### Post by p1ruj3 on 2008-09-23
maybe this will help, so i did a iptables -F and cleared the tables but watched in tcpdump it continue to send the 10.10.0.199 ip out and drop my ppp0 connection as it connected...

---

### Post by p1ruj3 on 2008-09-24
not sure if this is a fix, cause i still have seen the error occur, but stability seems to increase

i think ppp0 was setting the default route in a poor manor

even though connections worked, it wasnt correct?

/sbin/route del default gw 0.0.0.0      # Remove nonsense route
/sbin/route add default gw PPP_REMOTE  # Add correct route

---

### Post by p1ruj3 on 2008-10-07
I think its a route table issue comparing how it builds in windows to the linux route table it builds that i show in the prior post how should i build the route table in unix correctly to match the one below??? 

(to make it easier for you guys i differentiate windows lan 192.168 / linux 10.10 )

>route PRINT
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x10003 ...00 50 22 ba 0b ef ...... Realtek RTL8139 Family PCI Fast Ethernet N

0x20004 ...00 53 45 00 00 00 ...... WAN (PPP/SLIP) Interface
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0    70.219.141.12   70.219.141.12       1
      66.174.67.4  255.255.255.255    70.219.141.12   70.219.141.12       1
    70.219.141.12  255.255.255.255        127.0.0.1       127.0.0.1       50
   70.255.255.255  255.255.255.255    70.219.141.12   70.219.141.12       50
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      192.168.0.0    255.255.255.0      192.168.0.1     192.168.0.1       20
      192.168.0.1  255.255.255.255        127.0.0.1       127.0.0.1       20
    192.168.0.255  255.255.255.255      192.168.0.1     192.168.0.1       20
        224.0.0.0        240.0.0.0      192.168.0.1     192.168.0.1       20
        224.0.0.0        240.0.0.0    70.219.141.12   70.219.141.12       1
  255.255.255.255  255.255.255.255    70.219.141.12   70.219.141.12       1
  255.255.255.255  255.255.255.255      192.168.0.1     192.168.0.1       1
Default Gateway:     70.219.141.12
===========================================================================
Persistent Routes:
  None

---

### Post by dmizer on 2008-10-08
Okay, let's try a different iptables configuration then.

Flush your current configuration:
```
sudo iptables -F
```
Make sure your iptables is unconfigured.
^ this is VERY important. If any rules remain in iptables, they may be causing you problems. Please confirm this by posting the output of this command:
```
sudo iptables -L
```

If there are no iptables rules in place, then run this command:
```
sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
```

reference: [http://www.linuxforums.org/forum/ubuntu-help/125639-howto-internet-connection-sharing-ubuntu-server-puppy-linux-client.html](http://www.linuxforums.org/forum/ubuntu-help/125639-howto-internet-connection-sharing-ubuntu-server-puppy-linux-client.html)

---

### Post by p1ruj3 on 2008-10-08
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

problem still occurs....

linux routing table

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
66.174.66.4     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

windows routing table
```
 
Network Destination Netmask Gateway Interface Metric
0.0.0.0 0.0.0.0 70.219.141.12 70.219.141.12 1
66.174.67.4 255.255.255.255 70.219.141.12 70.219.141.12 1
70.219.141.12 255.255.255.255 127.0.0.1 127.0.0.1 50
70.255.255.255 255.255.255.255 70.219.141.12 70.219.141.12 50
127.0.0.0 255.0.0.0 127.0.0.1 127.0.0.1 1
192.168.0.0 255.255.255.0 192.168.0.1 192.168.0.1 20
192.168.0.1 255.255.255.255 127.0.0.1 127.0.0.1 20
192.168.0.255 255.255.255.255 192.168.0.1 192.168.0.1 20
224.0.0.0 240.0.0.0 192.168.0.1 192.168.0.1 20
224.0.0.0 240.0.0.0 70.219.141.12 70.219.141.12 1
255.255.255.255 255.255.255.255 70.219.141.12 70.219.141.12 1
255.255.255.255 255.255.255.255 192.168.0.1 192.168.0.1 1
Default Gateway: 70.219.141.12


```
are you sure its not in how my routing tables are look at the two above there are differences  arnt there?


how do i add this route in linux? ```
 66.174.67.4 255.255.255.255 70.219.141.12 70.219.141.12 1
 
```

---

### Post by dmizer on 2008-10-20
Why does your eth0 have two ip addresses? Are you certain that NAT is disabled on the router?

---

### Post by nimrodwebdesign on 2009-11-12
Hi p1ruj3,

did you ever get this resolved? I'm having the exact same problem.

I had it working fine until Oct 29th when I was downloading the new release, and suddenly it all went belly up.

My UBS727 in in an ubuntu server machine, which is also my dhcp and dns server. It's wired to a switch through which a desktop and two laptops connect (one wirelessly).

I had the same problem with Verizon not telling the me the reason for my disconnects, but eventually they found it was an 'IP Violation', like you.

I've used tshark to monitor ppp0 and sure enough, like you, I have the occasional internal IP 'leaking' out.

I don't understand how ONLY SOME get through the NAT. For the most part it's fine but occasionally some get through, and after about 10 leak through I get disconnected.

The only common thing I've noticed so far is that all the packets that get through 'appear' to originate from Opera 10.01. I don't know if it's possible for a program to create packets that can slip thought the NAT.

My machines are kept up to date package wise, except I haven't gone to the new version (9.10) on my server or desktop yet.

The longer I look at this the more I think it's a bug with iptables NAT.


Anyway I hope you, or someone, can help.

Colin =)


Here's some configs:

My network is 192.168.1.x
My server is 192.168.1.2 (because my switch (which is a router with DHCP and everything disabled) is 192.168.1.1)

iptables-save - the virbr0 stuff is added by virtualbox for my vm's:
```

# Generated by iptables-save v1.4.1.1 on Thu Nov 12 10:57:05 2009
*nat
:PREROUTING ACCEPT [674:47355]
:POSTROUTING ACCEPT [534:82365]
:OUTPUT ACCEPT [534:82365]
-A POSTROUTING -s 192.168.1.0/24 -o ppp0 -j MASQUERADE 
COMMIT
# Completed on Thu Nov 12 10:57:05 2009
# Generated by iptables-save v1.4.1.1 on Thu Nov 12 10:57:05 2009
*mangle
:PREROUTING ACCEPT [28893:8870703]
:INPUT ACCEPT [11859:1060018]
:FORWARD ACCEPT [17034:7810685]
:OUTPUT ACCEPT [7171:1240521]
:POSTROUTING ACCEPT [24599:9124071]
COMMIT
# Completed on Thu Nov 12 10:57:05 2009
# Generated by iptables-save v1.4.1.1 on Thu Nov 12 10:57:05 2009
*filter
:INPUT DROP [159:31824]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [7173:1240849]
-A INPUT -i lo -j ACCEPT 
-A INPUT -i eth0 -j ACCEPT 
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A FORWARD -i eth0 -j ACCEPT 
-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A FORWARD -d 192.168.122.0/24 -o virbr0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT 
-A FORWARD -i virbr0 -o virbr0 -j ACCEPT 
-A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable 
-A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable 
COMMIT
# Completed on Thu Nov 12 10:57:05 2009

```

---

### Post by nimrodwebdesign on 2009-11-13
I think I've solved it!!

My rule to allow traffic out of the network to the internet was:

```
-A FORWARD -i eth0 -j ACCEPT
```

I trust all the computers on my network so I thought this was fine.

However the problem with that is that it lets INVALID packets through, and it seems to be the invalid packets don't get translated in the NAT rules.

So, changing the rule to:

```
-A FORWARD -i eth0 -m state --state NEW -j ACCEPT
```

...means that the INVALID packets (and UNTRACKED ones) don't get through to the NAT rules because they don't get accepted.

Well I lost a lot of hair over that one, but at least it's solved now. :KS


Oh, and for the record it wasn't _just_ Opera that was sending invalid packets ;)

---

