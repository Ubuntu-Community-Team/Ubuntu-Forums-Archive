---
title: "HotspotVPN Woes"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by dringess on 2006-11-27
I am trying the [www.HotSpotVPN.com](www.HotSpotVPN.com) service for security while traveling. I tried the mini howto at [http://customisinglife.wordpress.com/2006/10/17/access-microsoft-vpn-using-pptp](http://customisinglife.wordpress.com/2006/10/17/access-microsoft-vpn-using-pptp), but cannot connect. The system log says 

```
Nov 27 19:15:16 localhost pppd[11412]: Plugin nm-pppd-plugin.so loaded.
Nov 27 19:15:16 localhost pppd[11412]: nm-pppd-plugin: plugin initialized.
Nov 27 19:15:16 localhost pppd[11414]: pppd 2.4.4 started by root, uid 0
Nov 27 19:15:16 localhost pptp[11416]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Nov 27 19:15:16 localhost pppd[11414]: Using interface ppp0
Nov 27 19:15:16 localhost pppd[11414]: Connect: ppp0 <--> /dev/pts/1
Nov 27 19:15:16 localhost pptp[11421]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Nov 27 19:15:16 localhost pptp[11421]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Nov 27 19:15:16 localhost pptp[11421]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Nov 27 19:15:17 localhost pppd[11414]: nm-pppd-plugin: CHAP check hook.
Nov 27 19:15:17 localhost pptp[11421]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Nov 27 19:15:17 localhost pptp[11421]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Nov 27 19:15:17 localhost pptp[11421]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 52864). 
Nov 27 19:15:17 localhost pppd[11414]: nm-pppd-plugin: CHAP credentials requested.
Nov 27 19:15:17 localhost pptp[11416]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet 5 (expecting 4, lost or reordered)
Nov 27 19:15:17 localhost pppd[11414]: MS-CHAP authentication failed: Invalid!
Nov 27 19:15:17 localhost pppd[11414]: CHAP authentication failed
Nov 27 19:15:17 localhost pppd[11414]: Connection terminated.
Nov 27 19:15:17 localhost pptp[11421]: anon log[pptp_read_some:pptp_ctrl.c:543]: read returned zero, peer has closed
Nov 27 19:15:17 localhost pptp[11421]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
Nov 27 19:15:17 localhost pptp[11421]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Nov 27 19:15:17 localhost pptp[11421]: anon log[pptp_read_some:pptp_ctrl.c:543]: read returned zero, peer has closed
Nov 27 19:15:17 localhost pptp[11421]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Nov 27 19:15:17 localhost pppd[11414]: Exit.


```
Any suggestions?

---

### Post by dringess on 2006-11-29
I did get it to work -- HotspotVPN tech support gave me a different server address that apparently does CHAP in a different way. Works fine now.

---

