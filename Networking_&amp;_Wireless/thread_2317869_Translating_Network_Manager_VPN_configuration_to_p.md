---
title: "Translating Network Manager VPN configuration to pptp-client"
date: 2016-03-20
forum: Networking &amp; Wireless
---

### Post by Drooling_Iguana on 2016-03-20
I'm trying to connect to a PPTP-based VPN. I'm able to do so through Network Manager but as I'm going to need to set this VPN up on a server with only CLI access I need to be able to get the connection to work using pptp-client, and I'm currently unable to do so.

My Network Manager config is as follows (certain config options have been redacted for security reasons):

```

[connection]
id=<ID goes here>
uuid=<UUID goes here>
type=vpn
permissions=user:<Linux username goes here>:;
autoconnect=false
timestamp=1458507947

[vpn]
service-type=org.freedesktop.NetworkManager.pptp
password-flags=1
require-mppe=yes
user=<VPN username goes here>
mppe-stateful=yes
refuse-eap=yes
refuse-chap=yes
gateway=<VPN IP goes here>
refuse-pap=yes

[ipv4]
method=auto
never-default=true

```

My current pptp-client peer file is as follows:

```

pty "pptp <VPN IP goes here> --nolaunchpppd"
lock
noauth
nobsdcomp
nodeflate
refuse-pap
refuse-chap
refuse-eap
require-mppe-128
name <VPN username goes here>
remotename <VPN name goes here>
ipparam <VPN name goes here>

```

When I run "sudo pon <VPN name goes here> debug dump logfd 2 nodetach" I get the following output:

```

pppd options in effect:
debug        # (from command line)
nodetach        # (from command line)
logfd 2        # (from command line)
dump        # (from command line)
noauth        # (from /etc/ppp/peers/<VPN name goes here>)
refuse-pap        # (from /etc/ppp/peers/<VPN name goes here>)
refuse-chap        # (from /etc/ppp/peers/<VPN name goes here>)
refuse-eap        # (from /etc/ppp/peers/<VPN name goes here>)
name <VPN username goes here>        # (from /etc/ppp/peers/<VPN name goes here>)
remotename ehealth        # (from /etc/ppp/peers/<VPN name goes here>)
        # (from /etc/ppp/peers/<VPN name goes here>)
pty pptp <VPN IP goes here> --nolaunchpppd        # (from /etc/ppp/peers/<VPN name goes here>)
crtscts        # (from /etc/ppp/options)
        # (from /etc/ppp/options)
asyncmap 0        # (from /etc/ppp/options)
lcp-echo-failure 4        # (from /etc/ppp/options)
lcp-echo-interval 30        # (from /etc/ppp/options)
hide-password        # (from /etc/ppp/options)
ipparam <VPN name goes here>        # (from /etc/ppp/peers/<VPN name goes here>)
nobsdcomp        # (from /etc/ppp/peers/<VPN name goes here>)
nodeflate        # (from /etc/ppp/peers/<VPN name goes here>)
require-mppe-128        # (from /etc/ppp/peers/<VPN name goes here>)
noipx        # (from /etc/ppp/options)
using channel 13
Using interface ppp1
Connect: ppp1 <--> /dev/pts/9
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa6031934> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xa6031934> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1400> <auth eap> <magic 0x73a86c96> <pcomp> <accomp> <callback CBCP> <mrru 1614> <endpoint [local:4e.b1.a7.63.fd.1e.40.dd.95.41.12.9c.71.61.f2.24.00.00.00.00]>]
No auth is possible
sent [LCP ConfRej id=0x1 <auth eap> <callback CBCP> <mrru 1614>]
rcvd [LCP TermReq id=0x2 "s\37777777650l\37777777626\000<\37777777715t\000\000\003\37777777627"]
sent [LCP TermAck id=0x2]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa6031934> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa6031934> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa6031934> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa6031934> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa6031934> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa6031934> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa6031934> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa6031934> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa6031934> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa6031934> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
Waiting for 1 child processes...
  script pptp <VPN IP goes here> --nolaunchpppd, pid 22064
sending SIGTERM to process 22064

```

Any ideas?

---

