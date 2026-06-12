---
title: "PPTP routing"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by Miesco on 2008-10-20
I am connecting to my campus vpn server which uses pptp with ppp0.  I am connecting to the internet wirelessly with wlan0.

I can connect to the VPN, and get the nameserver's in resolv.conf without 'usepeerdns' in /etc/ppp/options.pptp

Here is what happends when I connect:

[INDENT][SIZE="2"]root@ubuntu:/home/shawn# pon slc debug dump 2 nodetach
pppd options in effect:
debug		# (from command line)
nodetach		# (from command line)
dump		# (from command line)
noauth		# (from /etc/ppp/options.pptp)
refuse-chap		# (from /etc/ppp/options.pptp)
refuse-mschap		# (from /etc/ppp/options.pptp)
refuse-eap		# (from /etc/ppp/options.pptp)
name [email]SWallis13@sl.on.ca[/email]		# (from /etc/ppp/peers/slc)
remotename PPTP		# (from /etc/ppp/peers/slc)
2		# (from command line)
		# (from /etc/ppp/options.pptp)
pty pptp vpn01.sl.on.ca --nolaunchpppd		# (from /etc/ppp/peers/slc)
crtscts		# (from /etc/ppp/options)
		# (from /etc/ppp/options)
asyncmap 0		# (from /etc/ppp/options)
lcp-echo-failure 4		# (from /etc/ppp/options)
lcp-echo-interval 30		# (from /etc/ppp/options)
hide-password		# (from /etc/ppp/options)
ipparam slc		# (from /etc/ppp/peers/slc)
proxyarp		# (from /etc/ppp/options)
usepeerdns		# (from /etc/ppp/options.pptp)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
require-mppe-128		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
speed 2 not supported
using channel 4
Using interface ppp0
Connect: ppp0 <--> /dev/pts/4
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x49c0616> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <mru 1400> <auth chap MS-v2> <magic 0x4b706197> <pcomp> <accomp> <callback CBCP> <mrru 1614> <endpoint [local:b9.ed.f7.de.bd.4a.4b.35.b2.84.6d.72.84.1b.77.07.00.00.00.00]> < 17 04 0e 2d>]
sent [LCP ConfRej id=0x0 <callback CBCP> <mrru 1614> < 17 04 0e 2d>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x49c0616> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1400> <auth chap MS-v2> <magic 0x4b706197> <pcomp> <accomp> <endpoint [local:b9.ed.f7.de.bd.4a.4b.35.b2.84.6d.72.84.1b.77.07.00.00.00.00]>]
sent [LCP ConfAck id=0x1 <mru 1400> <auth chap MS-v2> <magic 0x4b706197> <pcomp> <accomp> <endpoint [local:b9.ed.f7.de.bd.4a.4b.35.b2.84.6d.72.84.1b.77.07.00.00.00.00]>]
sent [LCP EchoReq id=0x0 magic=0x49c0616]
rcvd [CHAP Challenge id=0x0 <7d81539226c04ce02417ddd18335ed55>, name = "VPN02"]
Warning - secret file /etc/ppp/chap-secrets has world and/or group access
sent [CHAP Response id=0x0 <1c19f49400c7fa9636f7f70b6ff0d2100000000000000000420425224c226cc15ccc47cd1e989c621d97cf9c4d7559b800>, name = "SWallis13@sl.on.ca"]
rcvd [LCP EchoRep id=0x0 magic=0x4b706197]
rcvd [CHAP Success id=0x0 "S=C7393D09BB72D94804A28561FA968E054AC17EB3"]
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x3 <mppe +H -M +S -L -D +C>]
sent [CCP ConfNak id=0x3 <mppe +H -M +S -L -D -C>]
rcvd [IPCP ConfReq id=0x4 <addr 142.155.126.10>]
sent [IPCP TermAck id=0x4]
rcvd [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x5 <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x5 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.2.10> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x2 <addr 192.168.2.10> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr 142.155.126.47> <ms-dns1 142.155.200.3> <ms-dns3 142.155.216.1>]
sent [IPCP ConfReq id=0x3 <addr 142.155.126.47> <ms-dns1 142.155.200.3> <ms-dns3 142.155.216.1>]
rcvd [IPCP ConfAck id=0x3 <addr 142.155.126.47> <ms-dns1 142.155.200.3> <ms-dns3 142.155.216.1>]
rcvd [IPCP ConfReq id=0x6 <addr 142.155.126.10>]
sent [IPCP ConfAck id=0x6 <addr 142.155.126.10>]
Cannot determine ethernet address for proxy ARP
local  IP address 142.155.126.47
remote IP address 142.155.126.10
primary   DNS address 142.155.200.3
secondary DNS address 142.155.216.1
Script /etc/ppp/ip-up started (pid 18484)
Script /etc/ppp/ip-up finished (pid 18484), status = 0x0[/SIZE]

[/INDENT]

I connect:
[INDENT][SIZE="2"]root@ubuntu:/etc/ppp# ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:142.155.126.47  P-t-P:142.155.126.10  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:104 (104.0 B)  TX bytes:116 (116.0 B)[/SIZE][/INDENT]

Now here is my routing table:

[INDENT][SIZE="2"]root@ubuntu:/etc/ppp# ip route
142.155.126.10 dev ppp0  proto kernel  scope link  src 142.155.126.47 
142.155.32.0/22 dev wlan0  proto kernel  scope link  src 142.155.33.109 
default via 142.155.32.5 dev wlan0[/SIZE][/INDENT]

The network administrator said to make my assigned VPN IP my default gateway.

I can do this to connect to the dns server:
[SIZE="2"][INDENT]route add -host 142.155.200.3 gw 142.155.126.10[/INDENT][/SIZE]
But that only lets me connect to one computer in the network... I want to be able to connect to knas01.sl.on.ca so I can get my homework...

Would I do an 'route add -net'?
Or do I just need to make my default getaway my ppp0 connection... and in doing so wouldn't that make wlan0 not work?

Also if I have dns information for ppp0 in /etc/resolv.conf, I want my wlan0 dns info too.  Can you add them both in resolv.conf so they can both work?

My school wont help me because I use linux so any help is much appreciated.

---

### Post by Miesco on 2008-10-21
I just wanted to put this at the top again

---

