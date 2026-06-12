---
title: "VPN using NetworkManager"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by gilad_no on 2007-06-12
Hi,

I'm trying to setup a connection to my office's vpn server (MS Windows). After installing pptp plugin for NetworkManager, I've created a new connection. "Refuse EAP" is checked, while "Authenticate Peer" is unchecked.

When I try to connect, I get "connection failed". Here is my output from the log:

Jun 12 00:58:32 desktop pptp[7072]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 10496). 
Jun 12 00:58:33 desktop pptp[7070]: anon warn[decaps_hdlc:pptp_gre.c:197]: short read (-1): Input/output error
Jun 12 00:58:33 desktop pptp[7070]: anon warn[decaps_hdlc:pptp_gre.c:209]: pppd may have shutdown, see pppd log
Jun 12 00:58:33 desktop pptp[7072]: anon log[callmgr_main:pptp_callmgr.c:231]: Closing connection (unhandled)
Jun 12 00:58:33 desktop pptp[7072]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Jun 12 00:58:33 desktop pptp[7072]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Jun 12 00:58:42 desktop NetworkManager: <WARNING>^I nm_vpn_service_process_signal (): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Jun 12 00:58:42 desktop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Jun 12 00:58:42 desktop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
Jun 12 00:58:42 desktop NetworkManager: <WARNING>^I nm_vpn_service_stop_connection (): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'Office' because service was 6.


I have no clue what "Input/Output error" means. Can someone help please?

Regards,
   Gilad

---

### Post by gilad_no on 2007-06-12
I've found the problem. It seems like my server does not support 128 bit encryption. After removing the checkbox, it all works now.

---

