---
title: "kvpc cannot establish PPTP with my router"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by cometta on 2008-06-04
i able to establish pptp with my router when i on my windows machine. but with kvpnc, i have the log as below


debug: No default interface given, tried default interface, got success, using "eth0".
debug: Username: ghost
debug: Trying to connect to server "www.myhomeserver.com" with user "ghost"... 
debug: [pppd] using channel 1
debug: [pppd] Using interface ppp0
debug: [pppd] Connect: ppp0 /dev/pts/0
debug: [pppd] Warning - secret file /etc/ppp/pap-secrets has world and/or group access
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] rcvd [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfAck id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] rcvd [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfAck id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] rcvd [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfAck id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] rcvd [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfAck id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] rcvd [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfAck id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] rcvd [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfAck id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] rcvd [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfAck id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] rcvd [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfAck id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] rcvd [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfAck id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] rcvd [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfAck id=0x1 ]
debug: [pppd] LCP: timeout sending Config-Requests
debug: [pppd] Connection terminated.
info: Connection has been terminated.
debug: [pppd] Modem hangup
error: Remote modem has hung up. Connection was terminated.

---

### Post by cmnorton on 2008-07-01
I am having trouble following your question. Is there a vpn server running on your router, or are you trying to connect to a host "beyond" (routed to by) your router?

Is KVpcn not connecting at all, or are you connecting, but cannot ping a host on the new network?

Edit:
---------

Have you just not been able to connect at all, or did you connect once, and cannot re-connect?

I tried uploading my pptp config screen shot, but it was too big. I have the following checked:

Require MPPE, Do not use BSD Compression, Do not use MPPC compression, Allow MPPE stateful mode, Refuse EAP, and Do not use deflate method.

I found those settings affected getting the connection to complete.

---

