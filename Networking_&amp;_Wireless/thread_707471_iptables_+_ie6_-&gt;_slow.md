---
title: "iptables + ie6 -&gt; slow"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by ture_atlantis on 2008-02-25
I am using IE6 (installed via ies4linux) to access work email (an excahnge server) because the web based interface is much better than firefox's... When my iptables is configured with the following:

```
root@atlantis-laptop:~# iptables -nvL
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    6   460 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    2   208 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW,RELATED,ESTABLISHED 

```

My IE loads extremly slow...  If i change the policy of INPUT and OUTPUT to ACCEPT, it loads normally.  

If I change iptables INPUT policy back to DROP and add a rule to allow traffic from the web server:

```
iptables -I INPUT --src x.x.x.x -j ACCEPT
```

It still loads really slow.  At this point it seems that there is traffic coming from another address (possibly an ActiveX control for IE/Exchange) but tcpdumps do not show anything.  

If I change the input policy to state NEW,RELATED,ESTABLISHED it seems to connect fine as well.

Capturing packets with wireshark and performing the filter 'ip.src != x.x.x.x and ip.dst != x.x.x.x' shows no packets...

Anyone have a way I can troubleshoot this?

Does anyone have another way of troubleshooting this, or know how IE/Echange communicates?

---

### Post by The Cog on 2008-02-25
You aren't allowing any new connections in either direction. You shuld at least allow DNS requests (UDP port 53) and HTTP connections (TCP 80) out. In fact, it's probably easiest to  just have a default ACCEPT policy on outbound connections.

---

### Post by SpaceTeddy on 2008-02-25
> **The Cog said:**
> You aren't allowing any new connections in either direction. You shuld at least allow DNS requests (UDP port 53) and HTTP connections (TCP 80) out. In fact, it's probably easiest to  just have a default ACCEPT policy on outbound connections.
mhm... yes he does... 
> 2   208 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state **NEW**,RELATED,ESTABLISHED


The NEW allows any SYN paket to be send out. So, anything can be initiated as long as it is stateful.

But it is a good idea to at least add DNS as an extra rule, since that might not be considered stateful (udp is stateless, but somehow iptables is able to figure it stateful... in most cases anyway)

so how about adding
> sudo iptables -A INPUT -p udp --sport 53 -j ACCEPT
sudo iptables -A OUTPUT -p udp --dport 53 -j ACCEPT

---

### Post by ture_atlantis on 2008-02-26
Still no luck with adding the suggested DNS rules... I have also tried changeing the policy on outbound to ACCEPT, with no luck.  The problem has to do with the INPUT chain, and IE...

It works if I change the INPUT rule to allow 'new' states - which tells me that at some point the Exchange server is creating a connection back to my machine (initiating the connection) which is strange because nothing shows up in a tcp dump...

If I do a tcpdump or wireshark capture with a filter of 'host not webmail.company.com' the only thing that shows up is the DNS query... 

Any other ideas?

---

### Post by The Cog on 2008-02-26
Oops. SpaceTeddy is right - I didn't notice the "NEW". 
Try adding a "-j LOG" to each chain (as the last entry) to log all the defaulted packets and then tail /var/log/syslog to see what's being dropped.

---

### Post by ture_atlantis on 2008-02-26
iptables:
```
root@atlantis-laptop:~# iptables -nvL
Chain INPUT (policy DROP 8 packets, 1319 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    4  3356 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   11   727 ACCEPT     0    --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW,RELATED,ESTABLISHED 
    0     0 LOG        0    --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 

```


The packets that were being logged in syslog were:

```
Feb 26 15:21:44 atlantis-laptop kernel: [ 1042.420000] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=29 TOS=0x00 PREC=0x00 TTL=64 ID=54514 DF PROTO=UDP SPT=32813 DPT=32813 LEN=9 
Feb 26 15:21:45 atlantis-laptop kernel: [ 1043.668000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:43:77:2a:f7:08:00 SRC=165.137.34.113 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=40990 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:21:46 atlantis-laptop kernel: [ 1044.420000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:43:77:2a:f7:08:00 SRC=165.137.34.113 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=40994 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:21:47 atlantis-laptop kernel: [ 1045.168000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:43:77:2a:f7:08:00 SRC=165.137.34.113 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=40996 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:21:47 atlantis-laptop kernel: [ 1046.092000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:15:56:d6:f8:dd:08:00 SRC=165.137.34.2 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=14477 DF PROTO=UDP SPT=68 DPT=67 LEN=308 
Feb 26 15:22:11 atlantis-laptop kernel: [ 1069.320000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:15:c5:50:7e:e4:08:00 SRC=165.137.34.88 DST=165.137.34.127 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=4715 PROTO=UDP SPT=138 DPT=138 LEN=209 
Feb 26 15:22:13 atlantis-laptop kernel: [ 1071.196000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:15:56:d6:f8:dd:08:00 SRC=165.137.34.2 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=14478 DF PROTO=UDP SPT=68 DPT=67 LEN=308 
Feb 26 15:22:21 atlantis-laptop kernel: [ 1079.672000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:43:77:2a:f7:08:00 SRC=165.137.34.113 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=41044 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:22:22 atlantis-laptop kernel: [ 1080.424000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:43:77:2a:f7:08:00 SRC=165.137.34.113 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=41048 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:22:23 atlantis-laptop kernel: [ 1081.172000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:43:77:2a:f7:08:00 SRC=165.137.34.113 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=41051 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:22:38 atlantis-laptop kernel: [ 1096.300000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:15:56:d6:f8:dd:08:00 SRC=165.137.34.2 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=14479 DF PROTO=UDP SPT=68 DPT=67 LEN=308 
Feb 26 15:22:57 atlantis-laptop kernel: [ 1115.676000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:43:77:2a:f7:08:00 SRC=165.137.34.113 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=41095 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:22:58 atlantis-laptop kernel: [ 1116.428000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:43:77:2a:f7:08:00 SRC=165.137.34.113 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=41099 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:22:59 atlantis-laptop kernel: [ 1117.176000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:43:77:2a:f7:08:00 SRC=165.137.34.113 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=41103 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:23:02 atlantis-laptop kernel: [ 1121.140000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:00:85:0c:be:0a:08:00 SRC=165.137.34.8 DST=165.137.34.127 LEN=213 TOS=0x00 PREC=0x00 TTL=64 ID=34044 PROTO=UDP SPT=138 DPT=138 LEN=193 
Feb 26 15:23:03 atlantis-laptop kernel: [ 1121.404000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:15:56:d6:f8:dd:08:00 SRC=165.137.34.2 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=14480 DF PROTO=UDP SPT=68 DPT=67 LEN=308 
Feb 26 15:23:28 atlantis-laptop kernel: [ 1146.508000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:15:56:d6:f8:dd:08:00 SRC=165.137.34.2 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=14481 DF PROTO=UDP SPT=68 DPT=67 LEN=308 
Feb 26 15:23:33 atlantis-laptop kernel: [ 1151.680000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:43:77:2a:f7:08:00 SRC=165.137.34.113 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=41143 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:23:34 atlantis-laptop kernel: [ 1152.432000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:43:77:2a:f7:08:00 SRC=165.137.34.113 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=41147 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:23:35 atlantis-laptop kernel: [ 1153.184000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:43:77:2a:f7:08:00 SRC=165.137.34.113 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=41151 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:23:36 atlantis-laptop kernel: [ 1154.724000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:e0:29:43:6c:7c:08:00 SRC=165.137.34.69 DST=165.137.34.127 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=56916 PROTO=UDP SPT=138 DPT=138 LEN=209 
Feb 26 15:23:38 atlantis-laptop kernel: [ 1156.912000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:15:c5:40:cc:9e:08:00 SRC=165.137.34.45 DST=165.137.34.127 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=6416 PROTO=UDP SPT=138 DPT=138 LEN=209 
Feb 26 15:23:40 atlantis-laptop kernel: [ 1158.860000] IN=eth0 OUT= MAC= SRC=165.137.34.25 DST=224.0.0.251 LEN=96 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=76 
Feb 26 15:23:40 atlantis-laptop kernel: [ 1158.932000] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:06:5b:49:d3:f4:08:00 SRC=165.137.34.102 DST=224.0.0.251 LEN=304 TOS=0x00 PREC=0x00 TTL=255 ID=26492 PROTO=UDP SPT=5353 DPT=5353 LEN=284 
Feb 26 15:23:48 atlantis-laptop kernel: [ 1166.644000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:00:85:0c:be:0a:08:00 SRC=165.137.34.8 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=34047 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:23:49 atlantis-laptop kernel: [ 1167.640000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:00:85:0c:be:0a:08:00 SRC=165.137.34.8 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=34048 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:23:49 atlantis-laptop kernel: [ 1168.140000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:00:85:0c:be:0a:08:00 SRC=165.137.34.8 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=34049 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:23:50 atlantis-laptop kernel: [ 1168.640000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:00:85:0c:be:0a:08:00 SRC=165.137.34.8 DST=165.137.34.127 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=34050 PROTO=UDP SPT=137 DPT=137 LEN=58 
Feb 26 15:23:53 atlantis-laptop kernel: [ 1171.612000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:15:56:d6:f8:dd:08:00 SRC=165.137.34.2 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=14482 DF PROTO=UDP SPT=68 DPT=67 LEN=308 
Feb 26 15:23:58 atlantis-laptop kernel: [ 1176.900000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:0e:c7:8c:08:00 SRC=165.137.34.58 DST=165.137.34.127 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=11155 PROTO=UDP SPT=138 DPT=138 LEN=209 
Feb 26 15:24:00 atlantis-laptop kernel: [ 1178.232000] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:06:5b:ca:e5:f4:08:00 SRC=165.137.34.43 DST=165.137.34.127 LEN=241 TOS=0x00 PREC=0x00 TTL=128 ID=23371 PROTO=UDP SPT=138 DPT=138 LEN=221
```


My current IP info is: 
```
root@atlantis-laptop:~# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:18:8B:A6:2B:D3  
          inet addr:165.137.34.25  Bcast:165.137.34.127  Mask:255.255.255.128
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6100363 (5.8 MB)  TX bytes:1777619 (1.6 MB)
          Interrupt:18 
```

Could it be that wine gets a different IP address than my local one?  The dropped traffic is UDP going from 165.137.34.113 (on my same subnet) to the gateway...  

Any more ideas?

---

### Post by SpaceTeddy on 2008-02-26
wine does not get a different ip-address, i am pretty sure about that. But the traffic you logged there is windows shares... 137 is for netbios lookups in local networks usually. Since it is directed i would think that, for some reason, this means that you communicate over that port for some reason... so how about putting in a rule for the port 137 and 138 to allow them (for what reason these are used is absolutly beyond me) and see if that works.

rules should be
> sudo iptables -I INPUT -p udp -m multiport --sports 137,138 -j ACCEPT
sudo iptables -I OUTPUT -p udp -m multiport --dports 137,138 -j ACCEPT


**[thinking hard]**

mhm... forget it. i just read it again... none of these packets are for you. the whole 137 and 138 are broadcasts on your subnet by some machine announcing it's shares to other... if you look at the dst you will see that that is not your interface, but the broadcast interface... so in other words... none of these packets are related to your connection with the exchange server... as far as i can see it
i am going to leave my first idea in anyway, maybe there is something in there that other can pick up on and figure this out

---

### Post by The Cog on 2008-02-27
Did you try to use IE to access a web site during that log trace? I see no sign of any packets of significance being dropped during that time, other than the first packet which I can't identify. 

That first packet is from 127.0.0.1 to 127.0.0.1 - the computer trying to talk to itself. It's generally a good idea to allow this, so I suggest you allow this to happen. Something like this should do the trick (do it before the logging lines):
```
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -d 127.0.0.0/8 -j ACCEPT
```

---

