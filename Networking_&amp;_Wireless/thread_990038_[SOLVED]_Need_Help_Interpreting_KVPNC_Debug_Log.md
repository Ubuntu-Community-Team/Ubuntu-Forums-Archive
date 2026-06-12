---
title: "[SOLVED] Need Help Interpreting KVPNC Debug Log"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2008-11-22
I am using KVPNC to connect to our firewall. I believe KVPNC's settings are good, because I can connect with no problem at work inside our firewall. I attribute the success in part to LAN speed at work versus DSL speed at home.

I am asking for pointers to solve this problem using two means. One is taking direction from the log file; the other would be to control the PPP configuration.

1) What do I make of the debug log? It appears to point to the chap-secrets file, but I do not understand what it is telling me. Here is an extract of the log:

debug: [pppd] Modem hangup
error: Remote modem has hung up. Connection was terminated.
debug: There is a reason for stop connecting, terminating "pppd" process.
debug: pppd secrets file: /etc/ppp/chap-secrets
debug: Start marker in /etc/ppp/chap-secrets found
debug: End marker in /etc/ppp/chap-secrets found
debug: File /etc/ppp/chap-secrets successfully removed
debug: File /etc/ppp/chap-secrets sucessfully rewritten

2) Given I suspect a timing problem off my DSL connection at home, I have forgotten which PPP files control things like delaying before making the VPN connection. I have Googled for whick files control PPP connections. I am coming up short on links to information.

Edit:
----------------------------------------------
 pptp[10092]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
pptp[10092]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 101).
pptp[10092]: anon log[pptp_read_some:pptp_ctrl.c:543]: read returned zero, peer has closed
pptp[10092]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
pptp[10092]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
pptp[10092]: anon log[pptp_read_some:pptp_ctrl.c:543]: read returned zero, peer has closed
pptp[10092]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
pppd[10087]: Modem hangup
pppd[10087]: Connection terminated.
pppd[10087]: Exit.

---

### Post by cmnorton on 2008-12-29
All of a sudden, my VPN from home just works. I have kept my Kubuntu 8.04 system up-to-date by clicking on the update icon, whenever prompted. 

So, either a component got fixed, or a change happened to our firewall, which is unlikely. Either way, something fixed KVPNC's being able to connect to our firewall.

---

