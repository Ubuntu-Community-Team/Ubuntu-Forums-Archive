---
title: "PPTP not accepting anymore W10 connections"
date: 2018-10-02
forum: Networking &amp; Wireless
---

### Post by emolina on 2018-10-02
Hi all,

I'm having such a nightmare trying to connect from a W10 to a 
Linux 4.15.0-34-generic #37-Ubuntu SMP Mon Aug 27 15:21:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

I have been able to connect via PPP with no problems at all until some days ago (I have been a whole week and a half fighting with this issue with any luck), but from one day to another, the system quit working. Whenever I try to connect from W10, it returns "The PPP Link Control Protocol Was Terminated". I have trying to study the dump and doing tons of changes to the pptpd_options and pptpd.conf with no luck yet.

So, please, could anyone tell me if you can find any clue of the problem here (or give me a hint of where else I should take an eye)?


```
pptpd[42803]: MGR: Launching /usr/sbin/pptpctrl to handle client
pptpd[42803]: CTRL: local address = 192.168.0.128
pptpd[42803]: CTRL: remote address = 192.168.0.128
pptpd[42803]: CTRL: pppd options file = /etc/ppp/pptpd-options
pptpd[42803]: CTRL: Client XXX.XXX.XXX.XXX control connection started
pptpd[42803]: CTRL: Received PPTP Control Message (type: 1)
pptpd[42803]: CTRL: Made a START CTRL CONN RPLY packet
pptpd[42803]: CTRL: I wrote 156 bytes to the client.
pptpd[42803]: CTRL: Sent packet to client
pptpd[42803]: CTRL: Received PPTP Control Message (type: 7)
pptpd[42803]: CTRL: Set parameters to 100000000 maxbps, 64 window size
pptpd[42803]: CTRL: Made a OUT CALL RPLY packet
pptpd[42803]: CTRL: Starting call (launching pppd, opening GRE)
pptpd[42803]: CTRL: pty_fd = 6
pptpd[42803]: CTRL: tty_fd = 7
pptpd[42803]: CTRL: I wrote 32 bytes to the client.
pptpd[42803]: CTRL: Sent packet to client
pptpd[42804]: CTRL (PPPD Launcher): program binary = /usr/sbin/pppd
pptpd[42804]: CTRL (PPPD Launcher): local address = 192.168.0.128
pptpd[42804]: CTRL (PPPD Launcher): remote address = 192.168.0.128
pppd[42804]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
pppd[42804]: pptpd-logwtmp: $Version$
pppd[42804]: pppd 2.4.7 started by server_user, uid 0
pppd[42804]: using channel 129
NetworkManager[790]: <info>  [1538470388.9334] manager: (ppp0): new Ppp device (/org/freedesktop/NetworkManager/Devices/135)
pppd[42804]: Using interface ppp0
pppd[42804]: Connect: ppp0 <--> /dev/pts/3
pppd[42804]: sent [LCP ConfReq id=0x1 <mru 1490> <asyncmap 0x0> <auth chap MS-v2> <magic 0x3cc21a57> <pcomp> <accomp>]
pptpd[42803]: GRE: Bad checksum from pppd.
pptpd[42803]: CTRL: Received PPTP Control Message (type: 15)
pptpd[42803]: CTRL: Got a SET LINK INFO packet with standard ACCMs
systemd-udevd[42805]: link_config: autonegotiation is unset or enabled, the speed and duplex are not writable.
pptpd[42803]: GRE: accepting packet #0
pppd[42804]: rcvd [LCP ConfReq id=0x0 <mru 1400> <magic 0x12b86bf0> <pcomp> <accomp> <callback CBCP>]
pppd[42804]: sent [LCP ConfRej id=0x0 <callback CBCP>]
pptpd[42803]: GRE: accepting packet #1
pppd[42804]: rcvd [LCP ConfAck id=0x1 <mru 1490> <asyncmap 0x0> <auth chap MS-v2> <magic 0x3cc21a57> <pcomp> <accomp>]
NetworkManager[790]: <info>  [1538470388.9623] devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
NetworkManager[790]: <info>  [1538470388.9623] device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
pptpd[42803]: GRE: accepting packet #2
pppd[42804]: rcvd [LCP ConfReq id=0x1 <mru 1400> <magic 0x12b86bf0> <pcomp> <accomp>]
pppd[42804]: sent [LCP ConfAck id=0x1 <mru 1400> <magic 0x12b86bf0> <pcomp> <accomp>]
pppd[42804]: sent [LCP EchoReq id=0x0 magic=0x3cc21a57]
pppd[42804]: sent [CHAP Challenge id=0x45 <ea9723a0fa76c77de846615274cb2c23>, name = "pptpd"]
pptpd[42803]: GRE: accepting packet #3
pptpd[42803]: GRE: accepting packet #4
pppd[42804]: rcvd [LCP Ident id=0x2 magic=0x12b86bf0 "MSRASV5.20"]
pppd[42804]: rcvd [LCP Ident id=0x3 magic=0x12b86bf0 "MSRAS-0-XXXXX"]
pptpd[42803]: GRE: accepting packet #5
pppd[42804]: rcvd [LCP Ident id=0x4 magic=0x12b86bf0 "\311\032\2620:\307\300B\233\313\261\320\2611\360\204"]
pptpd[42803]: GRE: accepting packet #6
pppd[42804]: rcvd [LCP EchoRep id=0x0 magic=0x12b86bf0]
pptpd[42803]: GRE: accepting packet #7
pppd[42804]: rcvd [LCP EchoRep id=0x0 magic=0x12b86bf0]
pptpd[42803]: GRE: accepting packet #8
pppd[42804]: rcvd [CHAP Response id=0x45 <XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX>, name = "XXXXXXXXXX"]
pppd[42804]: sent [CHAP Success id=0x45 "S=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX M=Access granted"]
pppd[42804]: peer from calling number XXX.XXX.XXX.XXX authorized
pppd[42804]: sent [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
pptpd[42803]: GRE: buffering packet #10 (expecting #9, lost or reordered)
pptpd[42803]: CTRL: Received PPTP Control Message (type: 15)
pptpd[42803]: CTRL: Ignored a SET LINK INFO packet with real ACCMs! (intentional non-compliance with section 2.15 of RFC 2637, ACCM is negotiated by PPP LCP asyncmap)
pptpd[42803]: GRE: accepting packet #9
pppd[42804]: rcvd [IPV6CP ConfReq id=0x5 <addr fe80::3066:5a7e:8623:e95b>]
pppd[42804]: Unsupported protocol 'IPv6 Control Protocol' (0x8057) received
pppd[42804]: sent [LCP ProtRej id=0x2 80 57 01 05 00 0e 01 0a 30 66 5a 7e 86 23 e9 5b]
pptpd[42803]: GRE: accepting #10 from queue
pptpd[42803]: GRE: accepting packet #11
pptpd[42803]: GRE: accepting packet #12
pptpd[42803]: GRE: accepting packet #13
pppd[42804]: rcvd [CCP ConfReq id=0x6 <mppe +H -M -S -L -D -C>]
pppd[42804]: sent [CCP ConfNak id=0x6 <mppe +H -M +S +L -D -C>]
pppd[42804]: rcvd [IPCP ConfReq id=0x7 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns2 0.0.0.0> <ms-wins 0.0.0.0>]
pppd[42804]: sent [IPCP TermAck id=0x7]
pppd[42804]: rcvd [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
pppd[42804]: sent [CCP ConfReq id=0x2 <mppe +H -M +S -L -D -C>]
pppd[42804]: rcvd [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
pptpd[42803]: GRE: accepting packet #14
pppd[42804]: rcvd [CCP ConfReq id=0x8 <mppe +H -M +S -L -D -C>]
pppd[42804]: sent [CCP ConfAck id=0x8 <mppe +H -M +S -L -D -C>]
pptpd[42803]: GRE: accepting packet #15
pppd[42804]: rcvd [CCP ConfAck id=0x2 <mppe +H -M +S -L -D -C>]
pppd[42804]: MPPE 128-bit stateless compression enabled
pppd[42804]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.0.128>]
pptpd[42803]: GRE: accepting packet #16
pppd[42804]: rcvd [CCP ConfReq id=0x9 <mppe +H -M +S -L -D -C>]
pppd[42804]: MPPE disabled
pppd[42804]: sent [LCP TermReq id=0x3 "MPPE disabled"]
pppd[42804]: sent [CCP ConfReq id=0x3 <mppe +H -M +S +L -D -C>]
pppd[42804]: sent [CCP ConfAck id=0x9 <mppe +H -M +S -L -D -C>]
pptpd[42803]: GRE: accepting packet #17
pppd[42804]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
pppd[42804]: Discarded non-LCP packet when LCP not open
pptpd[42803]: GRE: buffering packet #19 (expecting #18, lost or reordered)
pptpd[42803]: CTRL: Received PPTP Control Message (type: 15)
pptpd[42803]: CTRL: Got a SET LINK INFO packet with standard ACCMs
pptpd[42803]: GRE: accepting packet #18
pptpd[42803]: GRE: accepting #19 from queue
pptpd[42803]: GRE: accepting packet #20
pppd[42804]: rcvd [LCP TermAck id=0x3 "MPPE disabled"]
pppd[42804]: Connection terminated.
pppd[42804]: Connect time 0.1 minutes.
pppd[42804]: Sent 60 bytes, received 108 bytes.
NetworkManager[790]: <info>  [1538470389.0792] devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
pptpd[42803]: CTRL: Received PPTP Control Message (type: 12)
pptpd[42803]: CTRL: Made a CALL DISCONNECT RPLY packet
pptpd[42803]: CTRL: Received CALL CLR request (closing call)
pptpd[42803]: CTRL: Reaping child PPP[42804]
pppd[42804]: Exit.
pptpd[42803]: CTRL: Client 88.6.58.191 control connection finished
pptpd[42803]: CTRL: Exiting now
pptpd[42061]: MGR: Reaped child 42803


```

Some points I see, but I don't know if they are a real problem or only a warning with no effect, are parts such as:
GRE: Bad checksum from pppd.
systemd-udevd[42805]: link_config: autonegotiation is unset or enabled, the speed and duplex are not writable.
pppd[42804]: Unsupported protocol 'IPv6 Control Protocol' (0x8057) received (I don't have any interest on working with IPv6, by the way).
pppd[42804]: Discarded non-LCP packet when LCP not open
pppd[42804]: rcvd [LCP TermAck id=0x3 "MPPE disabled"]

I have seen that I can't access to the PPP from any W10 anymore, but I can from an iPad and from a Linux without problem.

/etc/ppp.conf:
```

option /etc/ppp/pptpd-options
debug
logwtmp
localip 192.168.0.128-228
remoteip 192.168.0.128-228


```

/etc/ppp/pptpd-options:
```

debug
name pptpd
lock
auth
refuse-eap
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
nobsdcomp
nodeflate
proxyarp
nodefaultroute
mtu 1490
mru 1490
ms-dns 62.81.16.164
ms-dns 62.81.16.213
require-mppe
mppe-stateful

```

I have being messing so much with these files that it's possible that they have additional serious issues. Any advice will be very helpful.

On the side client, W10 has the standard settings it defaults when creating a new VPN from Settings > VPN, setting the VPN to PPTP.

Thank you very much in advance.

---

