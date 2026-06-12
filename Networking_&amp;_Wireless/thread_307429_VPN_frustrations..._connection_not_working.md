---
title: "VPN frustrations... connection not working"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by telex4 on 2006-11-26
I'm trying to establish a VPN connection for the first time, to the server at work. I have all the details for Windows users and I've been trying to make them work with pptpconfig and KVpnc but to no avail. Background info - I've opened a hole through my firewall for all ports, just to eliminate that potential issue.

KVpnc seems to get nowhere. Aside from the UI being completely confusing, I just get these messages:

> info: [pppd]Using interface ppp0 Connect: ppp0 /dev/pts/2 
debug: Tunnel device: ppp0 Connect: ppp0 /dev/pts/2 
info: "pppd" started.
info: [pppd]LCP terminated by peer (y^\^PM-k^@
info: [pppd]Connection terminated. 
debug: There is a reason for stop connecting, terminating "pppd" process.
info: File /etc/ppp/chap-secrets sucessfully removed
info: [pppd]Modem hangup
info: "pppd route process" started.
info: [pppd] 

pptpconfig seems to get a little further, but it never completes the connection. It gets this far but then no further, so I'm unable to use the ping button:

> 
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ath0
pptpconfig: debug information dump ends, starting pppd
pppd options in effect:
debug		# (from /etc/ppp/peers/---blocked-out---)
updetach		# (from command line)
logfd 1		# (from command line)
linkname ---blocked-out---		# (from /etc/ppp/peers/---blocked-out---)
dump		# (from /etc/ppp/peers/---blocked-out---)
noauth		# (from /etc/ppp/options.pptp)
refuse-chap		# (from /etc/ppp/options.pptp)
refuse-mschap		# (from /etc/ppp/options.pptp)
refuse-eap		# (from /etc/ppp/options.pptp)
name ---blocked-out---\\tom.chance		# (from /etc/ppp/peers/---blocked-out---)
remotename ---blocked-out---		# (from /etc/ppp/peers/---blocked-out---)
		# (from /etc/ppp/options.pptp)
pty pptp mailgate.---blocked-out---.com --nolaunchpppd 		# (from /etc/ppp/peers/---blocked-out---)
crtscts		# (from /etc/ppp/options)
		# (from /etc/ppp/options)
asyncmap 0		# (from /etc/ppp/options)
lcp-echo-failure 4		# (from /etc/ppp/options)
lcp-echo-interval 30		# (from /etc/ppp/options)
hide-password		# (from /etc/ppp/options)
ipparam ---blocked-out---		# (from /etc/ppp/peers/---blocked-out---)
noproxyarp		# (from /etc/ppp/options)
usepeerdns		# (from /etc/ppp/peers/---blocked-out---)
nobsdcomp		# (from /etc/ppp/options.pptp)
nodeflate		# (from /etc/ppp/options.pptp)
require-mppe		# (from /etc/ppp/peers/---blocked-out---)
require-mppe-128		# (from /etc/ppp/options.pptp)
noipx		# (from /etc/ppp/options)
using channel 12
Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x16ce953a> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <mru 1400> <auth eap> <magic 0x3deb5e9b> <pcomp> <accomp> <callback CBCP> <mrru 1614> <endpoint [local:60.bc.73.24.8c.85.42.fd.9f.a5.b9.fe.a6.4a.62.66.00.00.00.00]> < 17 04 00 76>]
sent [LCP ConfRej id=0x0 <callback CBCP> <mrru 1614> < 17 04 00 76>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x16ce953a> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1400> <auth eap> <magic 0x3deb5e9b> <pcomp> <accomp> <endpoint [local:60.bc.73.24.8c.85.42.fd.9f.a5.b9.fe.a6.4a.62.66.00.00.00.00]>]
sent [LCP ConfNak id=0x1 <auth chap MS-v2>]
rcvd [LCP ConfReq id=0x2 <mru 1400> <auth chap MS-v2> <magic 0x3deb5e9b> <pcomp> <accomp> <endpoint [local:60.bc.73.24.8c.85.42.fd.9f.a5.b9.fe.a6.4a.62.66.00.00.00.00]>]
sent [LCP ConfAck id=0x2 <mru 1400> <auth chap MS-v2> <magic 0x3deb5e9b> <pcomp> <accomp> <endpoint [local:60.bc.73.24.8c.85.42.fd.9f.a5.b9.fe.a6.4a.62.66.00.00.00.00]>]
sent [LCP EchoReq id=0x0 magic=0x16ce953a]
rcvd [CHAP Challenge id=0x0 <f10abb840ca3607fa15cdf1059c6e072>, name = "BIO01"]
Warning - secret file /etc/ppp/chap-secrets has world and/or group access
sent [CHAP Response id=0x0 <7587b3e2eb04206221e87bca36b1ae700000000000000000ee804cbc2cc6a916f9fc7848c01b478f7d5182ad45aea7ce00>, name = "---blocked-out---\\---blocked-out---"]
rcvd [LCP EchoRep id=0x0 magic=0x3deb5e9b]
rcvd [CHAP Success id=0x0 "S=E810CCC9B25A63333AF6B2B57718B252520E36D3"]
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
rcvd [CCP ConfReq id=0x4 <mppe +H +M +S +L -D +C>]
sent [CCP ConfNak id=0x4 <mppe +H -M +S -L -D -C>]
rcvd [IPCP ConfReq id=0x5 <addr 192.168.0.32>]
sent [IPCP TermAck id=0x5]
rcvd [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfReq id=0x2 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x6 <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x6 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x2 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01> <ms-dns3 0.0.0.0>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr 192.168.0.31> <ms-dns1 192.168.0.4>]
sent [IPCP ConfReq id=0x3 <addr 192.168.0.31> <ms-dns1 192.168.0.4>]
rcvd [IPCP ConfAck id=0x3 <addr 192.168.0.31> <ms-dns1 192.168.0.4>]
rcvd [IPCP ConfReq id=0x7 <addr 192.168.0.32>]
sent [IPCP ConfAck id=0x7 <addr 192.168.0.32>]
local  IP address 192.168.0.31


That's with the routing set to "all to tunnel". If I set it to "client to LAN" then it doesn't reach the final line (quoting a local IP address).

I'm stuck and frustrated. Can anyone explain to me what I'm doing wrong?

---

### Post by telex4 on 2006-11-26
Part of the problem is that I can't see any useful feedback from the programs. Does anyone know of a trick to get more debugging back to help trace the problem?

---

