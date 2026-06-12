---
title: "VPN Problems"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by oneadvent on 2007-04-27
I am trying to connect to my work VPN. I got the administrator to add me to the white list, and he insists he did it, but I can still not get logged in.

Does anyone know what is going on? 

He is the important part of my error logs:

Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IWill activate VPN connection 'Work Connection', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'jwelch', vpn_data 'ppp-connection-type / pptp / pptp-remote / ***.***.**.*** / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / no / compress-mppc / no / compress-deflate / yes / compress-bsd / yes / ppp-lock / no / ppp-auth-peer / no / ppp-refuse-eap / no / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / yes / routes / ***.***.**.*** / use-routes / no', route ''. 
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN Activation (Work Connection) Stage 1 of 4 (Connection Prepare) scheduled... 
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN Activation (Work Connection) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 28912) 
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN Activation (Work Connection) Stage 1 of 4 (Connection Prepare) complete. 
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN Activation (Work Connection) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN Activation (Work Connection) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN Activation (Work Connection) Stage 2 of 4 (Connection Prepare Wait) complete. 
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN Activation (Work Connection) Stage 3 of 4 (Connect) scheduled... 
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN Activation (Work Connection) Stage 3 of 4 (Connect) sending connect request. 
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN Activation (Work Connection) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Apr 27 11:42:33 Linux-Box pppd[28913]: Plugin nm-pppd-plugin.so loaded.
Apr 27 11:42:33 Linux-Box pppd[28913]: nm-pppd-plugin: plugin initialized.
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN Activation (Work Connection) Stage 3 of 4 (Connect) reply received. 
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN Activation (Work Connection) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Apr 27 11:42:33 Linux-Box NetworkManager: <information>^IVPN Activation (Work Connection) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Apr 27 11:42:33 Linux-Box pppd[28915]: pppd 2.4.4 started by root, uid 0
Apr 27 11:42:33 Linux-Box pppd[28915]: using channel 13
Apr 27 11:42:33 Linux-Box pppd[28915]: Using interface ppp0
Apr 27 11:42:33 Linux-Box pppd[28915]: Connect: ppp0 <--> /dev/pts/0
Apr 27 11:42:33 Linux-Box pptp[28917]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Apr 27 11:42:33 Linux-Box pptp[28920]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Apr 27 11:42:34 Linux-Box pptp[28920]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Apr 27 11:42:34 Linux-Box pptp[28920]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Apr 27 11:42:34 Linux-Box pppd[28915]: nm-pppd-plugin: CHAP check hook.
Apr 27 11:42:34 Linux-Box pppd[28915]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0x4f21e1fc> <pcomp> <accomp>]
Apr 27 11:42:34 Linux-Box pptp[28920]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Apr 27 11:42:35 Linux-Box pptp[28920]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Apr 27 11:42:35 Linux-Box pptp[28920]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 1). 
Apr 27 11:42:35 Linux-Box pppd[28915]: rcvd [LCP ConfReq id=0x1 <mru 338> <auth chap MS-v2> <magic 0x942b7727> <pcomp> <accomp>]
Apr 27 11:42:35 Linux-Box pppd[28915]: sent [LCP ConfAck id=0x1 <mru 338> <auth chap MS-v2> <magic 0x942b7727> <pcomp> <accomp>]
Apr 27 11:42:35 Linux-Box pppd[28915]: rcvd [LCP ConfRej id=0x1 <asyncmap 0x0>]
Apr 27 11:42:35 Linux-Box pppd[28915]: sent [LCP ConfReq id=0x2 <mru 1416> <magic 0x4f21e1fc> <pcomp> <accomp>]
Apr 27 11:42:35 Linux-Box pptp[28917]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet 4 (expecting 3, lost or reordered)
Apr 27 11:42:35 Linux-Box pppd[28915]: rcvd [LCP ConfAck id=0x2 <mru 1416> <magic 0x4f21e1fc> <pcomp> <accomp>]
Apr 27 11:42:35 Linux-Box pppd[28915]: sent [LCP EchoReq id=0x0 magic=0x4f21e1fc]
Apr 27 11:42:35 Linux-Box pppd[28915]: rcvd [CHAP Challenge id=0x1 <a8a6ae744b49cb76037bf9a1f8350b8e>, name = "watchguard"]
Apr 27 11:42:35 Linux-Box pppd[28915]: nm-pppd-plugin: CHAP credentials requested.
Apr 27 11:42:35 Linux-Box pppd[28915]: sent [CHAP Response id=0x1 <461386e971b5dff7703fd57ba2fd65ec00000000000000001f0dcf24517c7e93fe7c65532e6493fe4eeb5089918a5d6f00>, name = "jwelch"]
Apr 27 11:42:35 Linux-Box pppd[28915]: rcvd [LCP EchoRep id=0x0 magic=0x942b7727]
Apr 27 11:42:35 Linux-Box pppd[28915]: rcvd [CHAP Failure id=0x1 "E=649 R=1 Try again"]
Apr 27 11:42:35 Linux-Box pppd[28915]: MS-CHAP authentication failed: E=649 No dialin permission
Apr 27 11:42:35 Linux-Box pppd[28915]: CHAP authentication failed
Apr 27 11:42:35 Linux-Box pppd[28915]: sent [LCP TermReq id=0x3 "Failed to authenticate ourselves to peer"]
Apr 27 11:42:35 Linux-Box pppd[28915]: rcvd [LCP TermAck id=0x3]
Apr 27 11:42:35 Linux-Box pppd[28915]: Connection terminated.
Apr 27 11:42:35 Linux-Box pptp[28917]: anon warn[decaps_hdlc:pptp_gre.c:197]: short read (-1): Input/output error
Apr 27 11:42:35 Linux-Box pptp[28917]: anon warn[decaps_hdlc:pptp_gre.c:209]: pppd may have shutdown, see pppd log
Apr 27 11:42:35 Linux-Box pptp[28920]: anon log[callmgr_main:pptp_callmgr.c:231]: Closing connection (unhandled)
Apr 27 11:42:35 Linux-Box pptp[28920]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Apr 27 11:42:35 Linux-Box pptp[28920]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Apr 27 11:42:35 Linux-Box pppd[28915]: Waiting for 1 child processes...
Apr 27 11:42:35 Linux-Box pppd[28915]:   script /usr/sbin/pptp ***.***.**.*** --nolaunchpppd, pid 28916
Apr 27 11:42:35 Linux-Box pppd[28915]: Script /usr/sbin/pptp ***.***.**.*** --nolaunchpppd finished (pid 28916), status = 0x0
Apr 27 11:42:35 Linux-Box pppd[28915]: Exit.
Apr 27 11:42:44 Linux-Box NetworkManager: <WARNING>^I nm_vpn_service_process_signal (): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Apr 27 11:42:44 Linux-Box NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Apr 27 11:42:44 Linux-Box NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
Apr 27 11:42:44 Linux-Box NetworkManager: <WARNING>^I nm_vpn_service_stop_connection (): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'Work Connection' because service was 6.

---

