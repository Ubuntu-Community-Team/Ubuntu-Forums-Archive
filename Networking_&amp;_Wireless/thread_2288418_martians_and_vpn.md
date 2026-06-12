---
title: "martians and vpn"
date: 2015-07-27
forum: Networking &amp; Wireless
---

### Post by lister171254 on 2015-07-27
I'm running shorewall on my laptop and I'm in the process of setting up ipvanish as my vpn.

I think I've got the setup more or less right as I can get through the firewall with the vpn. The only issue I have is that I get many messages like

kernel: [30997.800849] IPv4: martian source 10.0.0.12 from 103.4.235.252, on dev wlan0 

I'd appreciate any advice on how I can get rid of these warnings for 10.0.0.12.

Following are the shorewall files

interfaces
```
#ZONE	INTERFACE	OPTIONS
fixed     eth0            dhcp,optional,tcpflags,logmartians,nosmurfs,sourceroute=0
wire      wlan0           dhcp,optional,tcpflags,logmartians,nosmurfs,sourceroute=0
ovpn	tun0	routeback

``` 

zones
```
#ZONE	TYPE	OPTIONS			IN			OUT
#					OPTIONS			OPTIONS
fw	firewall
fixed	ipv4
wire	ipv4
ovpn	ipv4

```

policy
```
#SOURCE		DEST		POLICY		LOG LEVEL	LIMIT:BURST
fw		fixed		ACCEPT
fw		wire		ACCEPT
fw		ovpn		ACCEPT
ovpn		ovpn		ACCEPT
ovpn		fixed		ACCEPT
ovpn		wire		ACCEPT
fixed		all		DROP		info
wire		all		DROP		info
ovpn		fw		DROP		info
# The FOLLOWING POLICY MUST BE LAST
all		all		REJECT		info

```

rules
```
#ACTION		SOURCE		DEST		PROTO	DEST	SOURCE		ORIGINAL	RATE		USER/MARK	CONNLIMIT	TIME		HEADERS		SWITCH		HELPER
#							PORT	PORT(S)		DEST		LIMIT		GROUP
?SECTION ALL
?SECTION ESTABLISHED
?SECTION RELATED
?SECTION INVALID
?SECTION UNTRACKED
?SECTION NEW

# Drop packets in the INVALID state

Invalid(DROP)  fixed    	        fw		tcp
Invalid(DROP)  wire     	        fw		tcp

# Drop Ping from the "bad" net zone.. and prevent your log from being flooded..

Ping(DROP)	fixed		fw	
Ping(DROP)	wire		fw	

# Permit all ICMP traffic FROM the firewall TO the net zone

ACCEPT		fw		fixed		icmp
ACCEPT		fw		wire		icmp
#
# Permit openvpn

ACCEPT		fixed		fw		udp	1194
ACCEPT		wire		fw		udp	1194

```

masq
```
#INTERFACE:DEST		SOURCE		ADDRESS		PROTO	PORT(S)	IPSEC	MARK	USER/	SWITCH	ORIGINAL
#											GROUP		DEST
eth0			10.8.0.0
wlan0                   10.8.0.0

```

---

### Post by lister171254 on 2015-07-30
Given the lack of replies can somebody suggest another forum I could/should use?

---

