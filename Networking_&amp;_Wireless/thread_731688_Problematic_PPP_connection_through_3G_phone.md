---
title: "Problematic PPP connection through 3G phone"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by hkphooey on 2008-03-22
Hi,

I'm trying to connect my laptop to Smart Communications in the Philippines. The laptop, phone and USB cable combo worked OK using Windows, but I"m having trouble getting it going in Ubuntu. For the record, the phone is a Sony Ericsson K608i. I've tried setting up the connection with wvdial and KPPP and have the same problem with both. 

Basically what happens is that I get authenticated OK, and get given an IP address. However I don't seem to get a gateway set, and the DNS servers are set to 127.0.0.1 and 127.0.0.2 respectively which is clearly wrong. 

I've checked the settings in both wvdial and KPPP, and it should be 
 * asking the ISP for DNS servers. 
 * setting the default gateway to the one received from the ISP

I've found a reference here [http://axion.physics.ubc.ca/ppp-linux.html](http://axion.physics.ubc.ca/ppp-linux.html) which suggests that Smart have their PPP server set up wrong, and it isn't reporting its IP address to me properly. I tried the fix suggested there:
> The PPP setup returns the error "Could not determine remote IP address". This means that your ISP has a damaged implementation of ppp, which does not know (or refuses to report) who it is. So you need to assign your ISP an IP number. Put the lines
:192.168.255.1
ipcp-accept-remote
into the /etc/ppp/options file. These assign your ISP the IP number 192.168.255.1 (a "reserved" IP number) since they refuse to tell you theirs, and also tells pppd to accept their version if at this point they wake up and finally send you an IP address for themselves.
You might also notify your ISP that maybe they should know their own IP number.
But that doesn't work either. 

Here are the outputs of a few commands and the contents of some log files. Any suggestions gratefully received. 
```

--------- cat /var/log/messages
Mar 22 15:52:07 drongo2 pppd[23387]: pppd 2.4.4 started by root, uid 0
Mar 22 15:52:07 drongo2 kernel: [15952.960000] PPP generic driver version 2.4.2
Mar 22 15:52:07 drongo2 pppd[23387]: Using interface ppp0
Mar 22 15:52:07 drongo2 pppd[23387]: Connect: ppp0 <--> /dev/ttyACM0
Mar 22 15:52:07 drongo2 pppd[23387]: Remote message: Congratulations!
Mar 22 15:52:07 drongo2 pppd[23387]: PAP authentication succeeded
Mar 22 15:52:08 drongo2 kernel: [15953.136000] PPP BSD Compression module registered
Mar 22 15:52:08 drongo2 kernel: [15953.196000] PPP Deflate Compression module registered
Mar 22 15:52:11 drongo2 pppd[23387]: Could not determine remote IP address: defaulting to 10.64.64.64
Mar 22 15:52:11 drongo2 pppd[23387]: local  IP address 10.155.79.242
Mar 22 15:52:11 drongo2 pppd[23387]: remote IP address 10.64.64.64
Mar 22 15:52:11 drongo2 pppd[23387]: primary   DNS address 127.0.0.1
Mar 22 15:52:11 drongo2 pppd[23387]: secondary DNS address 127.0.0.2
Mar 22 15:55:57 drongo2 pppd[23387]: Terminating on signal 15
Mar 22 15:55:57 drongo2 pppd[23387]: Connect time 3.8 minutes.
Mar 22 15:55:57 drongo2 pppd[23387]: Sent 3192 bytes, received 504 bytes.
Mar 22 15:55:57 drongo2 pppd[23387]: Connection terminated.
Mar 22 15:55:57 drongo2 pppd[23387]: Exit.


-------- sudo wvdial

WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#*
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#*
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!}!} }8}#}$@#}(}"}'}"}"}&} } } } }%}&}2[1b]&?#e~
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: ~[7f]}#@!}!}"} }8}#}$@#}(}"}'}"}"}&} } } } }%}&}2[1b]&?iw~
WvDial<*1>: PPP negotiation detected.
WvDial<Notice>: Starting pppd at Sat Mar 22 15:52:07 2008
WvDial<Notice>: Pid of pppd: 23387
WvDial<*1>: Using interface ppp0
WvDial<*1>: local  IP address 10.155.79.242
WvDial<*1>: remote IP address 10.64.64.64
WvDial<*1>: primary   DNS address 127.0.0.1
WvDial<*1>: secondary DNS address 127.0.0.2
Caught signal 2:  Attempting to exit gracefully...
WvDial<*1>: Terminating on signal 15
WvDial<*1>: Connect time 3.8 minutes.
WvDial<*1>: Disconnecting at Sat Mar 22 15:55:57 2008

--------------- various network diagnostics -------------------------

------------------ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

----------------- netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.64.64.64     *               255.255.255.255 UH        0 0          0 ppp0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         *               0.0.0.0         U         0 0          0 ppp0
default         *               0.0.0.0         U         0 0          0 eth0

--------------------- ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:32:A0:B0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:849 errors:0 dropped:0 overruns:0 frame:0
          TX packets:849 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36659 (35.7 KB)  TX bytes:36659 (35.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.155.79.242  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:58 (58.0 b)  TX bytes:113 (113.0 b)

--------------------- ping 10.64.64.64
PING 10.64.64.64 (10.64.64.64) 56(84) bytes of data.
From 10.137.31.1 icmp_seq=1 Packet filtered
From 10.137.31.1 icmp_seq=6 Packet filtered
From 10.137.31.1 icmp_seq=7 Packet filtered
From 10.137.31.1 icmp_seq=9 Packet filtered
From 10.137.31.1 icmp_seq=10 Packet filtered
From 10.137.31.1 icmp_seq=11 Packet filtered
From 10.137.31.1 icmp_seq=13 Packet filtered
From 10.137.31.1 icmp_seq=14 Packet filtered
From 10.137.31.1 icmp_seq=15 Packet filtered

--- 10.64.64.64 ping statistics ---
15 packets transmitted, 0 received, +9 errors, 100% packet loss, time 14017ms
, pipe 3

------------------ ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.

--- 208.67.222.222 ping statistics ---
23 packets transmitted, 0 received, 100% packet loss, time 21999ms
-------------:~$ ping google.com
ping: unknown host google.com

----------------- cat /etc/resolv.conf
# generated by NetworkManager, do not edit!

nameserver 127.0.0.1
nameserver 127 0.0.2

search Skel


```

---

