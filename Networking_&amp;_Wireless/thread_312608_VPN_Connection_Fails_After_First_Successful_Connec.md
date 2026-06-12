---
title: "VPN Connection Fails After First Successful Connection"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by shaun.nolan@gmail.com on 2006-12-04
Hi All,

I hope someone can help with this as it is driving me insane.  Basically, I want to connect to my work's network (just like everyone else!). I'm using KVPNc and have been successful at connecting in and doing a telnet to one of the machines.  I've even been able to browse one of the Windows servers from Kronqueror too.  So, I know that I can do it and it's not that I'm making any obvious mistakes or any settings are wrong.

However, the VPN connection only works once!  After the first successful connection I start to get a pppd error and - even though it successfully connects - I can't see anything on the network.

The only way I can get the connection to work properly again is if I use Adept to reinstall all the software installed for pptp and restarting X.

Below is a copy of the KVPNc log.  It shows a successful connection followed immediately by a failed connection because of the pppd error.

Any ideas?


---- START OF LOG ----

debug: New type: pptp.
info: The required deamons (pppd and pptp) are available, connect will be enabled.
debug: Preserving network environment
info: Connect try requested
debug: pppd: /usr/sbin/pppd
debug: /usr/sbin/pppd has MPPE support and uses new style.
debug: Some passwords which are need got from password enter dialog.
info: "PppdUpScript" started.
info: "PppdUpScript" finished.
debug: pppd peer script: /etc/ppp/peers/kvpnc.WorkVPN 
debug: pppd chat script: /etc/ppp/chap-secrets 
debug: Username: sn
debug: chmod of /etc/ppp/chap-secrets (go-rwx) started.
debug: pppd: /usr/sbin/pppd 
debug: Trying to connect to server "xxxxxxx.xxxxxxxxxx.xx.xx" with user "sn"...
info: "pppd" started.
info: [pppd]using channel 1
info: [pppd] 
info: [pppd]Using interface ppp0
info: [pppd] Connect: ppp0 /dev/pts/4 
info: [pppd]sent [LCP ConfReq id=0x1 ]
info: [pppd] 
info: [pppd]rcvd [LCP ConfReq id=0x0 ] sent [LCP ConfRej id=0x0 ] 
info: [pppd]rcvd [LCP ConfAck id=0x1 ] 
info: [pppd]rcvd [LCP ConfReq id=0x1 ] sent [LCP ConfAck id=0x1 ] sent [LCP EchoReq id=0x0 magic=0x50d302d4] 
info: [pppd]rcvd [CHAP Challenge id=0x0 , name = "XXXX-XXX"] sent [CHAP Response id=0x0 , name = "sn"]
info: [pppd]rcvd [LCP EchoRep id=0x0 magic=0x24a90def] 
info: [pppd]rcvd [CHAP Success id=0x0 "S=ADBF78811DBF9CD8F8E9F1674739A992DE026714"] CHAP authentication succeeded sent [CCP ConfReq id=0x1 ] 
info: [pppd]rcvd [CCP ConfReq id=0x3 ] sent [CCP ConfNak id=0x3 ] rcvd [IPCP ConfReq id=0x4 ] sent [IPCP TermAck id=0x4] 
info: [pppd]rcvd [CCP ConfNak id=0x1 ] sent [CCP ConfReq id=0x2 ] 
info: [pppd]rcvd [CCP ConfReq id=0x5 ] sent [CCP ConfAck id=0x5 ] 
info: [pppd]rcvd [CCP ConfAck id=0x2 ] MPPE 128-bit stateless compression enabled sent [IPCP ConfReq id=0x1 ] 
info: [pppd]rcvd [IPCP ConfReq id=0x6 ] sent [IPCP ConfAck id=0x6 ] 
info: [pppd]sent [IPCP ConfReq id=0x1 ] 
info: [pppd]rcvd [IPCP ConfRej id=0x1 ] sent [IPCP ConfReq id=0x2 ] 
info: [pppd]rcvd [IPCP ConfNak id=0x2 ] sent [IPCP ConfReq id=0x3 ] 
info: [pppd]rcvd [IPCP ConfAck id=0x3 ] 
info: [pppd]Cannot determine ethernet address for proxy ARP local IP address xx.xxx.x.xx remote IP address xx.xxx.x.xx primary DNS address xx.xxx.x.x secondary DNS address xx.xxx.x.x Script /etc/ppp/ip-up started (pid 6091) Script /etc/ppp/ip-up finished (pid 6091), status = 0x0
info: Successful connected to server "xxxxxxx.xxxxxxxxxx.xx.xx" user: "sn") at Mon Dec 4 21:29:20 2006
info: "PppdUpScript" started.
info: "PppdUpScript" finished.
debug: Default interface eth1
debug: route: "route add -net xx.xxx.x.x/24 ppp0"
debug: Use gateway address (xxxxxxx.xxxxxxxxxx.xx.xx) for connection status check.
info: "ping_check.sh" started.
debug: Ping to xxxxxxx.xxxxxxxxxx.xx.xx within 4 checks every 1s was ok.
debug: Ping to xxxxxxx.xxxxxxxxxx.xx.xx within 4 checks every 1s was ok.
info: Disconnect requested
debug: Disconnect requested, status connected
info: "PppdDownScript" started.
info: "PppdDownScript" finished.
debug: killing "pptp"...
debug: "killall -3 pptp" was successful.
info: Successful disconnected.
info: Connection duration was 00 hours, 01 minutes, 33 seconds
info: File /etc/ppp/chap-secrets sucessfully removed

** START OF CONNECTION 2 **

info: "pppd route process" started.
info: Connect try requested
debug: pppd: /usr/sbin/pppd
debug: /usr/sbin/pppd has MPPE support and uses new style.
debug: Some passwords which are need got from password enter dialog.
info: "PppdUpScript" started.
info: "PppdUpScript" finished.
debug: pppd peer script: /etc/ppp/peers/kvpnc.WorkVPN 
debug: pppd chat script: /etc/ppp/chap-secrets 
debug: Username: sn
debug: chmod of /etc/ppp/chap-secrets (go-rwx) started.
debug: pppd: /usr/sbin/pppd 
debug: Trying to connect to server "xxxxxxx.xxxxxxxxxx.xx.xx" with user "sn"...
info: [pppd]using channel 2 Using interface ppp0 Connect: ppp0 /dev/pts/4 
info: "pppd" started.
info: [pppd]sent [LCP ConfReq id=0x1 ]
info: [pppd] 
info: [pppd]rcvd [LCP ConfReq id=0x0 ] sent [LCP ConfRej id=0x0 ] 
info: [pppd]rcvd [LCP ConfAck id=0x1 ] 
info: [pppd]rcvd [LCP ConfReq id=0x1 ] sent [LCP ConfAck id=0x1 ] sent [LCP EchoReq id=0x0 magic=0x1a2eb9a7] 
info: [pppd]rcvd [CHAP Challenge id=0x0 , name = "XXXX-XXX"]
info: [pppd]sent [CHAP Response id=0x0 , name = "sn"] rcvd [LCP EchoRep id=0x0 magic=0x67c966a1] 
info: [pppd]rcvd [CHAP Success id=0x0 "S=02CA8108FC6210FD7CCD10297BEEF4821B0EEAB6"] CHAP authentication succeeded sent [CCP ConfReq id=0x1 ] 
info: [pppd]rcvd [CCP ConfReq id=0x3 ] sent [CCP ConfNak id=0x3 ] rcvd [IPCP ConfReq id=0x4 ] sent [IPCP TermAck id=0x4] 
info: [pppd]rcvd [CCP ConfNak id=0x1 ] sent [CCP ConfReq id=0x2 ] 
info: [pppd]rcvd [CCP ConfReq id=0x5 ] sent [CCP ConfAck id=0x5 ] 
info: [pppd]rcvd [CCP ConfAck id=0x2 ] MPPE 128-bit stateless compression enabled sent [IPCP ConfReq id=0x1 ] 
info: [pppd]rcvd [IPCP ConfRej id=0x1 ] sent [IPCP ConfReq id=0x2 ] 
info: [pppd]rcvd [IPCP ConfNak id=0x2 ] sent [IPCP ConfReq id=0x3 ] 
info: [pppd]rcvd [IPCP ConfAck id=0x3 ] 
info: [pppd]rcvd [IPCP ConfReq id=0x6 ] sent [IPCP ConfAck id=0x6 ] 
info: [pppd]Cannot determine ethernet address for proxy ARP local IP address xx.xxx.x.xx remote IP address xx.xxx.x.xx primary DNS address xx.xxx.x.x secondary DNS address xx.xxx.x.x Script /etc/ppp/ip-up started (pid 6176)
info: Successful connected to server "xxxxxxx.xxxxxxxxxx.xx.xx" user: "sn") at Mon Dec 4 21:31:11 2006
info: "PppdUpScript" started.
info: "PppdUpScript" finished.
debug: Default interface eth1
[SIZE="4"]**error: [pppd err]** [/SIZE]
debug: route: "route add -net xx.xxx.x.x/24 Using interface ppp0 Connect: ppp0 /dev/pts/4 "
debug: Use gateway address (xxxxxxx.xxxxxxxxxx.xx.xx) for connection status check.
info: "ping_check.sh" started.
info: [pppd]Script /etc/ppp/ip-up finished (pid 6176), status = 0x0 
info: Disconnect requested
debug: Disconnect requested, status connected
info: "PppdDownScript" started.
info: "PppdDownScript" finished.
debug: killing "pptp"...
debug: "killall -3 pptp" was successful.
info: Successful disconnected.
info: Connection duration was 00 hours, 00 minutes, 50 seconds
info: File /etc/ppp/chap-secrets sucessfully removed
info: "pppd route process" started.

---

