---
title: "firewall not allowing incoming connections on ppp0"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by zamrg on 2008-07-18
I have a firewall configured with Shorewall on an Ubuntu server pc of mine.  It's an odd setup with a single eth0 network card connected to an old router in bridge mode.  The server establishes 2 ppp connections and splits local and international traffic (based on ip routes) over the 2 connections; international (ppp0) and local (ppp1).  The server is also setup as a gateway allowing other pcs on the network access to the internet.

My problem is that I can't seem to get a response from the server when I access it via the international (ppp0) ip, whilst it does work when using the local (ppp1) ip.

I'm not a linux or network expert but I do understand the basics and as far as I can see, my configuration looks fine.

I have included my Shorewall configs below, attached the output of 'routes -n' and 2 of my configs from /etc/ppp/peers which I establish the ppp0 (international) and ppp1 (local) connection sfrom.

zones
```

#ZONE	TYPE		OPTIONS		IN			OUT
#					OPTIONS			OPTIONS
fw	firewall
net	ipv4
loc	ipv4

```

interfaces
```

#ZONE	INTERFACE	BROADCAST	OPTIONS
net	ppp0		-
net	ppp1		-
loc	eth0	detect	tcpflags

```

policy
```

#SOURCE		DEST		POLICY		LOG		LIMIT:BURST
#						LEVEL
fw		net		ACCEPT
fw		loc		ACCEPT
loc		net		ACCEPT
net	all	DROP
all		all		REJECT		info

```

masq
```

#INTERFACE		SOURCE		ADDRESS		PROTO	PORT(S)	IPSEC	MARK
ppp0			eth0		$PPP0_IP
ppp1			eth0		$PPP1_IP
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE

```

params
```

PPP0_IP=$(find_first_interface_address ppp0)
PPP1_IP=$(find_first_interface_address ppp1)

```

rules
```

#ACTION		SOURCE		DEST		PROTO	DEST	SOURCE		ORIGINAL	RATE		USER/	MARK
#							PORT	PORT(S)		DEST		LIMIT		GROUP
#SECTION ESTABLISHED
#SECTION RELATED
#SECTION NEW
COMMENT allow green to ping fw
Ping/ACCEPT	all		fw
COMMENT allow green to access local services on fw
DNS/ACCEPT	loc		fw
HTTP/ACCEPT	all	fw
HTTPS/ACCEPT	all	fw
SSH/ACCEPT	all		fw
NTP/ACCEPT	loc		fw
SMB/ACCEPT	loc		fw
Webmin/ACCEPT	all		fw
ACCEPT	all	fw	tcp	6667
COMMENT sabnzbd web interface
ACCEPT	all	fw	tcp	8080
COMMENT dhcp server
ACCEPT	loc	fw	udp	67:68
COMMENT ntop web interface
ACCEPT	all	fw	tcp	3000
COMMENT znc irc bouncer
ACCEPT	loc	fw	tcp	1337
ACCEPT	loc	fw	tcp	1338
COMMENT route green through transparent proxy on fw
HTTP/REDIRECT	loc		8081		tcp	www	-		!192.168.1.100

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1d:7d:70:d6:04  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fe70:d604/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7316507 errors:0 dropped:1223802159 overruns:0 frame:0
          TX packets:11236517 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3061488713 (2.8 GB)  TX bytes:1263545923 (1.1 GB)
          Interrupt:221 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1826605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1826605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:393799050 (375.5 MB)  TX bytes:393799050 (375.5 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:41.240.30.XXX  P-t-P:41.240.64.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:18828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18703 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:13238035 (12.6 MB)  TX bytes:3655975 (3.4 MB)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:165.146.240.XXX  P-t-P:165.146.180.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:143614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138943 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:104129085 (99.3 MB)  TX bytes:31871599 (30.3 MB)

```

I would really appreciate some help as this has been bugging me for a while now.

---

