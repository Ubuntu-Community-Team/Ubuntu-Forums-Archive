---
title: "Can't connect to PPTP VPN"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by reinis on 2007-11-12
Hi,

I'm pretty new to Ubuntu, having just installed Gutsy. I've read a bunch of posts on here that show me how to set up a VPN connection to a Windows PPTP VPN. This bit all seems pretty straightforward but I can't seem to get a connection up and running.

From tailing the syslog the connection seems to authenticate OK to a point and then something causes it to fail. Any help on this would be appreciated.

```
Nov 12 22:32:11 cheetah NetworkManager: <info>  Will activate VPN connection 'Chicago', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'reinis', vpn_data 'ppp-connection-type / pptp / pptp-remote / 66.105.34.181 / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / yes / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / yes / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / yes / routes / 10.0.0.0/24 / use-routes / no', route ''. 
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 1 of 4 (Connection Prepare) scheduled... 
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 11604) 
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 1 of 4 (Connection Prepare) complete. 
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 2 of 4 (Connection Prepare Wait) complete. 
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 3 of 4 (Connect) scheduled... 
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 3 of 4 (Connect) sending connect request. 
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Nov 12 22:32:11 cheetah pppd[11605]: Plugin nm-pppd-plugin.so loaded.
Nov 12 22:32:11 cheetah pppd[11605]: nm-pppd-plugin: plugin initialized.
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 3 of 4 (Connect) reply received. 
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Nov 12 22:32:11 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Nov 12 22:32:11 cheetah pppd[11607]: pppd 2.4.4 started by root, uid 0
Nov 12 22:32:11 cheetah pptp[11609]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Nov 12 22:32:11 cheetah pppd[11607]: using channel 11
Nov 12 22:32:11 cheetah pppd[11607]: Using interface ppp0
Nov 12 22:32:11 cheetah pppd[11607]: Connect: ppp0 <--> /dev/pts/2
Nov 12 22:32:12 cheetah pptp[11612]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Nov 12 22:32:12 cheetah pptp[11612]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Nov 12 22:32:12 cheetah pptp[11612]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Nov 12 22:32:12 cheetah pppd[11607]: nm-pppd-plugin: CHAP check hook.
Nov 12 22:32:12 cheetah pppd[11607]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0x68ea7a43> <pcomp> <accomp>]
Nov 12 22:32:13 cheetah pptp[11612]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Nov 12 22:32:13 cheetah pptp[11612]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Nov 12 22:32:13 cheetah pptp[11612]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 17372). 
Nov 12 22:32:13 cheetah pppd[11607]: rcvd [LCP ConfReq id=0x0 <auth chap MS-v2> <magic 0x3c1b5f67> <pcomp> <accomp> <callback CBCP> <mrru 1614> <endpoint [local:c7.c4.65.fe.51.13.45.8f.ba.4b.9b.0f.fa.92.da.ad.00.00.00.00]> < 17 04 25 a0>]
Nov 12 22:32:13 cheetah pppd[11607]: sent [LCP ConfRej id=0x0 <callback CBCP> <mrru 1614> < 17 04 25 a0>]
Nov 12 22:32:13 cheetah pppd[11607]: rcvd [LCP ConfNak id=0x1 <mru 1500>]
Nov 12 22:32:13 cheetah pppd[11607]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0x68ea7a43> <pcomp> <accomp>]
Nov 12 22:32:14 cheetah pppd[11607]: rcvd [LCP ConfReq id=0x1 <auth chap MS-v2> <magic 0x3c1b5f67> <pcomp> <accomp> <endpoint [local:c7.c4.65.fe.51.13.45.8f.ba.4b.9b.0f.fa.92.da.ad.00.00.00.00]>]
Nov 12 22:32:14 cheetah pppd[11607]: sent [LCP ConfAck id=0x1 <auth chap MS-v2> <magic 0x3c1b5f67> <pcomp> <accomp> <endpoint [local:c7.c4.65.fe.51.13.45.8f.ba.4b.9b.0f.fa.92.da.ad.00.00.00.00]>]
Nov 12 22:32:14 cheetah pppd[11607]: rcvd [LCP ConfAck id=0x2 <asyncmap 0x0> <magic 0x68ea7a43> <pcomp> <accomp>]
Nov 12 22:32:14 cheetah pppd[11607]: sent [LCP EchoReq id=0x0 magic=0x68ea7a43]
Nov 12 22:32:14 cheetah pptp[11612]: anon log[ctrlp_disp:pptp_ctrl.c:949]: PPTP_SET_LINK_INFO received from peer_callid 0
Nov 12 22:32:14 cheetah pptp[11612]: anon log[ctrlp_disp:pptp_ctrl.c:952]:   send_accm is 00000000, recv_accm is FFFFFFFF
Nov 12 22:32:14 cheetah pptp[11612]: anon warn[ctrlp_disp:pptp_ctrl.c:955]: Non-zero Async Control Character Maps are not supported!
Nov 12 22:32:14 cheetah pppd[11607]: rcvd [CHAP Challenge id=0x0 <eefb23252e8b5603fde497ead680a561>, name = "CHIDC2"]
Nov 12 22:32:14 cheetah pppd[11607]: nm-pppd-plugin: CHAP credentials requested.
Nov 12 22:32:14 cheetah pppd[11607]: sent [CHAP Response id=0x0 <6c82b33d0a5278fc71620f3e409c93a90000000000000000198ca2ec0dcbbdb7486bcbe7f4e4de121ccaca95f735de0500>, name = "rgrauds"]
Nov 12 22:32:14 cheetah pppd[11607]: rcvd [LCP EchoRep id=0x0 magic=0x3c1b5f67]
Nov 12 22:32:14 cheetah pppd[11607]: rcvd [CHAP Success id=0x0 "S=71E33B027B4CC410FF1A681587DFC1E58F184E09M=Thank you for Logging in to CHicago PPTP server, please not that all traffic is a subject to monitoring."]
Nov 12 22:32:14 cheetah pppd[11607]: MS-CHAPv2 Success packet is badly formed.
Nov 12 22:32:14 cheetah pppd[11607]: CHAP authentication failed
Nov 12 22:32:14 cheetah pppd[11607]: sent [LCP TermReq id=0x3 "Failed to authenticate ourselves to peer"]
Nov 12 22:32:14 cheetah pppd[11607]: rcvd [CCP ConfReq id=0x3 <mppe +H +M +S +L -D +C>]
Nov 12 22:32:14 cheetah pppd[11607]: Discarded non-LCP packet when LCP not open
Nov 12 22:32:14 cheetah pppd[11607]: rcvd [IPCP ConfReq id=0x4 <addr 10.4.0.170>]
Nov 12 22:32:14 cheetah pppd[11607]: Discarded non-LCP packet when LCP not open
Nov 12 22:32:14 cheetah pptp[11612]: anon log[ctrlp_disp:pptp_ctrl.c:949]: PPTP_SET_LINK_INFO received from peer_callid 0
Nov 12 22:32:14 cheetah pptp[11612]: anon log[ctrlp_disp:pptp_ctrl.c:952]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Nov 12 22:32:14 cheetah pptp[11612]: anon warn[ctrlp_disp:pptp_ctrl.c:955]: Non-zero Async Control Character Maps are not supported!
Nov 12 22:32:14 cheetah pppd[11607]: rcvd [LCP TermAck id=0x3 "Failed to authenticate ourselves to peer"]
Nov 12 22:32:14 cheetah pppd[11607]: Connection terminated.
Nov 12 22:32:14 cheetah pptp[11609]: anon warn[decaps_hdlc:pptp_gre.c:197]: short read (-1): Input/output error
Nov 12 22:32:14 cheetah pptp[11609]: anon warn[decaps_hdlc:pptp_gre.c:209]: pppd may have shutdown, see pppd log
Nov 12 22:32:14 cheetah pptp[11612]: anon log[callmgr_main:pptp_callmgr.c:231]: Closing connection (unhandled)
Nov 12 22:32:14 cheetah pptp[11612]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Nov 12 22:32:14 cheetah pptp[11612]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Nov 12 22:32:14 cheetah pppd[11607]: Waiting for 1 child processes...
Nov 12 22:32:14 cheetah pppd[11607]:   script /usr/sbin/pptp 66.105.34.181 --nolaunchpppd, pid 11608
Nov 12 22:32:14 cheetah pppd[11607]: Script /usr/sbin/pptp 66.105.34.181 --nolaunchpppd finished (pid 11608), status = 0x0
Nov 12 22:32:14 cheetah pppd[11607]: Exit.
Nov 12 22:32:23 cheetah NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Nov 12 22:32:23 cheetah NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Nov 12 22:32:23 cheetah NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'Chicago' because service was 5. 
Nov 12 22:32:23 cheetah NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 

```

Thanks,
Reinis.

---

### Post by zanglang on 2007-11-12
What PPTP settings are you using? I've had this problem for a long time as well, although I did manage to find a combination that worked. Give it a try:

Tick
- Refuse EAP
- Allow Deflate compression
- Allow BSD compression
- Require MPPE encryption
- Require 128 bit MPPE encryption
- Enable stateful MPPE
- Use peer DNS

Do not tick
- Authenticate peer
- Refuse CHAP
- Refuse MS CHAP
- Require MPPC encryption

---

### Post by reinis on 2007-11-12
Thanks for replying. I've changed the settings you suggested but still no luck.

```
Nov 13 07:42:17 cheetah NetworkManager: <info>  Will activate VPN connection 'Chicago', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'reinis', vpn_data 'ppp-connection-type / pptp / pptp-remote / 66.105.34.181 / usepeerdns / yes / encrypt-mppe / yes / encrypt-mppe-128 / yes / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / yes / compress-bsd / yes / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / yes / routes / 10.0.0.0/24 / use-routes / no', route ''. 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 1 of 4 (Connection Prepare) scheduled... 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 12206) 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 1 of 4 (Connection Prepare) complete. 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 2 of 4 (Connection Prepare Wait) complete. 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 3 of 4 (Connect) scheduled... 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 3 of 4 (Connect) sending connect request. 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 3 of 4 (Connect) reply received. 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Nov 13 07:42:17 cheetah NetworkManager: <info>  VPN Activation (Chicago) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Nov 13 07:42:17 cheetah pppd[12207]: Plugin nm-pppd-plugin.so loaded.
Nov 13 07:42:17 cheetah pppd[12207]: nm-pppd-plugin: plugin initialized.
Nov 13 07:42:17 cheetah pppd[12209]: pppd 2.4.4 started by root, uid 0
Nov 13 07:42:17 cheetah pptp[12211]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Nov 13 07:42:17 cheetah pppd[12209]: using channel 12
Nov 13 07:42:17 cheetah pppd[12209]: Using interface ppp0
Nov 13 07:42:17 cheetah pppd[12209]: Connect: ppp0 <--> /dev/pts/2
Nov 13 07:42:17 cheetah pptp[12214]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Nov 13 07:42:18 cheetah pptp[12214]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Nov 13 07:42:18 cheetah pptp[12214]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Nov 13 07:42:18 cheetah pppd[12209]: nm-pppd-plugin: CHAP check hook.
Nov 13 07:42:18 cheetah pppd[12209]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0x3c952e6a> <pcomp> <accomp>]
Nov 13 07:42:18 cheetah pptp[12214]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Nov 13 07:42:19 cheetah pptp[12214]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Nov 13 07:42:19 cheetah pptp[12214]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 50142). 
Nov 13 07:42:19 cheetah pppd[12209]: rcvd [LCP ConfReq id=0x0 <auth chap MS-v2> <magic 0x5541424f> <pcomp> <accomp> <callback CBCP> <mrru 1614> <endpoint [local:c7.c4.65.fe.51.13.45.8f.ba.4b.9b.0f.fa.92.da.ad.00.00.00.00]> < 17 04 25 e5>]
Nov 13 07:42:19 cheetah pppd[12209]: sent [LCP ConfRej id=0x0 <callback CBCP> <mrru 1614> < 17 04 25 e5>]
Nov 13 07:42:19 cheetah pppd[12209]: rcvd [LCP ConfNak id=0x1 <mru 1500>]
Nov 13 07:42:19 cheetah pppd[12209]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0x3c952e6a> <pcomp> <accomp>]
Nov 13 07:42:19 cheetah pppd[12209]: rcvd [LCP ConfReq id=0x1 <auth chap MS-v2> <magic 0x5541424f> <pcomp> <accomp> <endpoint [local:c7.c4.65.fe.51.13.45.8f.ba.4b.9b.0f.fa.92.da.ad.00.00.00.00]>]
Nov 13 07:42:19 cheetah pppd[12209]: sent [LCP ConfAck id=0x1 <auth chap MS-v2> <magic 0x5541424f> <pcomp> <accomp> <endpoint [local:c7.c4.65.fe.51.13.45.8f.ba.4b.9b.0f.fa.92.da.ad.00.00.00.00]>]
Nov 13 07:42:19 cheetah pppd[12209]: rcvd [LCP ConfAck id=0x2 <asyncmap 0x0> <magic 0x3c952e6a> <pcomp> <accomp>]
Nov 13 07:42:19 cheetah pppd[12209]: sent [LCP EchoReq id=0x0 magic=0x3c952e6a]
Nov 13 07:42:19 cheetah pptp[12214]: anon log[ctrlp_disp:pptp_ctrl.c:949]: PPTP_SET_LINK_INFO received from peer_callid 0
Nov 13 07:42:19 cheetah pptp[12214]: anon log[ctrlp_disp:pptp_ctrl.c:952]:   send_accm is 00000000, recv_accm is FFFFFFFF
Nov 13 07:42:19 cheetah pptp[12214]: anon warn[ctrlp_disp:pptp_ctrl.c:955]: Non-zero Async Control Character Maps are not supported!
Nov 13 07:42:19 cheetah pppd[12209]: rcvd [CHAP Challenge id=0x0 <0a1aca9cd7a5fa9b10709dfb1f7b6369>, name = "CHIDC2"]
Nov 13 07:42:19 cheetah pppd[12209]: nm-pppd-plugin: CHAP credentials requested.
Nov 13 07:42:19 cheetah pppd[12209]: sent [CHAP Response id=0x0 <d0f9e1bc1e4eeb8e2f170b641032d8fe00000000000000005098cf2863126b24360b6bdb8e6091fbd8c10318210ab3ca00>, name = "rgrauds"]
Nov 13 07:42:19 cheetah pppd[12209]: rcvd [LCP EchoRep id=0x0 magic=0x5541424f]
Nov 13 07:42:20 cheetah pppd[12209]: rcvd [CHAP Success id=0x0 "S=B836C8DE09F9CC6A3E9B018D7567B68B8B8A0089M=Thank you for Logging in to CHicago PPTP server, please not that all traffic is a subject to monitoring."]
Nov 13 07:42:20 cheetah pppd[12209]: MS-CHAPv2 Success packet is badly formed.
Nov 13 07:42:20 cheetah pppd[12209]: CHAP authentication failed
Nov 13 07:42:20 cheetah pppd[12209]: sent [LCP TermReq id=0x3 "Failed to authenticate ourselves to peer"]
Nov 13 07:42:20 cheetah pppd[12209]: rcvd [CCP ConfReq id=0x3 <mppe +H +M +S +L -D +C>]
Nov 13 07:42:20 cheetah pppd[12209]: Discarded non-LCP packet when LCP not open
Nov 13 07:42:20 cheetah pppd[12209]: rcvd [IPCP ConfReq id=0x4 <addr 10.4.0.170>]
Nov 13 07:42:20 cheetah pppd[12209]: Discarded non-LCP packet when LCP not open
Nov 13 07:42:20 cheetah pptp[12214]: anon log[ctrlp_disp:pptp_ctrl.c:949]: PPTP_SET_LINK_INFO received from peer_callid 0
Nov 13 07:42:20 cheetah pptp[12214]: anon log[ctrlp_disp:pptp_ctrl.c:952]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Nov 13 07:42:20 cheetah pptp[12214]: anon warn[ctrlp_disp:pptp_ctrl.c:955]: Non-zero Async Control Character Maps are not supported!
Nov 13 07:42:20 cheetah pppd[12209]: rcvd [LCP TermAck id=0x3 "Failed to authenticate ourselves to peer"]
Nov 13 07:42:20 cheetah pppd[12209]: Connection terminated.
Nov 13 07:42:20 cheetah pptp[12211]: anon warn[decaps_hdlc:pptp_gre.c:197]: short read (-1): Input/output error
Nov 13 07:42:20 cheetah pptp[12211]: anon warn[decaps_hdlc:pptp_gre.c:209]: pppd may have shutdown, see pppd log
Nov 13 07:42:20 cheetah pptp[12214]: anon log[callmgr_main:pptp_callmgr.c:231]: Closing connection (unhandled)
Nov 13 07:42:20 cheetah pptp[12214]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Nov 13 07:42:20 cheetah pptp[12214]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Nov 13 07:42:20 cheetah pppd[12209]: Waiting for 1 child processes...
Nov 13 07:42:20 cheetah pppd[12209]:   script /usr/sbin/pptp 66.105.34.181 --nolaunchpppd, pid 12210
Nov 13 07:42:20 cheetah pppd[12209]: Script /usr/sbin/pptp 66.105.34.181 --nolaunchpppd finished (pid 12210), status = 0x0
Nov 13 07:42:20 cheetah pppd[12209]: Exit.
Nov 13 07:42:28 cheetah NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Nov 13 07:42:28 cheetah NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Nov 13 07:42:28 cheetah NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
Nov 13 07:42:28 cheetah NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'Chicago' because service was 6. 

```

---

### Post by mpokrywka on 2007-11-13
This is a problem:
```
Nov 13 07:42:20 cheetah pppd[12209]: rcvd [CHAP Success id=0x0 "S=B836C8DE09F9CC6A3E9B018D7567B68B8B8A0089M=Thank you for Logging in to CHicago PPTP server, please not that all traffic is a subject to monitoring."]
Nov 13 07:42:20 cheetah pppd[12209]: MS-CHAPv2 Success packet is badly formed.
```

PPTP server is sending message that you authenticaced successfully but this message is not understood by your ppp (you can see that there is space missing before "M=" in message). You have 2 solutions:
1) Talk to VPN server administrator and try to convince him that server sends responses that violates standard (good luck, windows clients probably work, so he has "no problem")
2) Patch your ppp to ignore any junk on the end of success message:
```
# install compiler and development packages
sudo aptitude install build-essential
sudo apt-get build-dep ppp
# create some dir where we will compile our version of ppp
mkdir ppp
cd ppp
# get ppp sources
apt-get source ppp
# IMPORTANT STEP!
# now put patch attached to this post into ppp-2.4.4rel/debian/patches
# compile package
cd ppp-2.4.4rel
fakeroot dpkg-buildpackage -b
cd ..
# install compiled package
sudo dpkg -i ppp_*.deb
```

and now try to connect...

---

### Post by reinis on 2007-11-14
Thanks for you help with this. I can see what we're trying to do here, but I'm getting stuck on the 'fakeroot buildpackage -b' step. I get the following error:
```
/usr/bin/fakeroot: 166: buildpackage: not found
```
Thanks,
Reinis.

---

### Post by mpokrywka on 2007-11-14
Sorry, my mistake, should be:
fakeroot dpkg-buildbackage -b

(now I fixed text above)

---

### Post by reinis on 2007-11-28
Sorry for the late reply... thank you very much for this, it works perfectly!

---

### Post by iansane on 2007-11-29
Hi, I've been trying to understand all of this and I've found some things to try on this and some other related posts, but they all talk about connecting to an allready existing vpn. I just want to set up a vpn between my ubuntu and a friends ubuntu. We both use dyndns and static IP's. Is this possible to do by creating a vpn and using the default settings on both ends? We've both done that but the vpn always fails to connect. Thanks

---

