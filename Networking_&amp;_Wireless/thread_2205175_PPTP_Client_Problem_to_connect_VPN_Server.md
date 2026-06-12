---
title: "PPTP Client: Problem to connect VPN Server"
date: 2014-02-12
forum: Networking &amp; Wireless
---

### Post by themaxxx on 2014-02-12
Hi guys,

Well, i have a problems to connect to my VPN from the Ubuntu 12.04.

the /etc/ppp/peers/ade-vpn

ppty "pptp server.vpn --noloaunchpppd"
name XXXXXX
remotename ade-vpn
require-mppe-128
file /etc/ppp/options.pptp
ipparam ade-vpn


the pptp connection leaves this log:

```
Feb 12 12:21:07 OPERACIONES pppd[3239]: pppd 2.4.5 started by root, uid 0
Feb 12 12:21:07 OPERACIONES pppd[3239]: Using interface ppp1
Feb 12 12:21:07 OPERACIONES pppd[3239]: Connect: ppp1 <--> /dev/pts/0
Feb 12 12:21:07 OPERACIONES pptp[3241]: anon log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Feb 12 12:21:08 OPERACIONES pptp[3249]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Feb 12 12:21:09 OPERACIONES pptp[3249]: anon log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Feb 12 12:21:09 OPERACIONES pptp[3249]: anon log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Feb 12 12:21:09 OPERACIONES pptp[3249]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Feb 12 12:21:09 OPERACIONES pptp[3249]: anon log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Feb 12 12:21:09 OPERACIONES pptp[3249]: anon log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 9).
Feb 12 12:21:38 OPERACIONES pppd[3239]: LCP: timeout sending Config-Requests
Feb 12 12:21:38 OPERACIONES pppd[3239]: Connection terminated.
Feb 12 12:21:38 OPERACIONES pptp[3241]: anon warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Feb 12 12:21:38 OPERACIONES pptp[3241]: anon warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Feb 12 12:21:38 OPERACIONES pptp[3249]: anon log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Feb 12 12:21:38 OPERACIONES pptp[3249]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Feb 12 12:21:38 OPERACIONES pptp[3249]: anon log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Feb 12 12:21:38 OPERACIONES pppd[3239]: Modem hangup
Feb 12 12:21:38 OPERACIONES pppd[3239]: Exit.

```
Any idea? i cant found any solution for my problem!

Thanks foy your time.

---

