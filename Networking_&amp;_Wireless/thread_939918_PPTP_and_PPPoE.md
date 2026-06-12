---
title: "PPTP and PPPoE"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by unkemptwolf on 2008-10-06
I am having trouble setting up a PPTP server over a PPPoE connection. The server connects to the ISP\Internet using a PPPoE connection on ppp0:

PPTP Server ----- PPP0\ISP ---- Internet ----- Client

When I try to connect windows clients I get:

```
Error 619
```

If I try to connect an ubuntu machine I get: 

```
[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 0). 
[pptp_read_some:pptp_ctrl.c:543]: read returned zero, peer has closed
[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
[pptp_read_some:pptp_ctrl.c:543]: read returned zero, peer has closed
[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
```

The logs on the server say:

```
GRE: read(fd=6,buffer=8058660,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
```

I have this same PPTP setup on a server at a different location, but it does not use PPPoE. I am at loss. Ive googled the issue from every angle I can think of, but cant seem to find why this isn't working. Ideas?

---

