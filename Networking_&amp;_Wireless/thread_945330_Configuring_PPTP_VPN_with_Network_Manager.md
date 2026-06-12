---
title: "Configuring PPTP VPN with Network Manager"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by Emil8192 on 2008-10-12
Hi,

I'm using Network Manager with the pptp pluging to open a VPN connection to my office.

From my laptop running XP I can just create a new VPN connection and change nothing except adress/username/password, so I think everything is pretty standard at the server side. It's a win 2003 server.

All the settings I have selected appares in syslog, so I don't think I need to repeat them here, but there is one thing that doesn't seem right: "user_name 'emil'" This is my account on the Ubuntu PC, but it's NOT the name I enter whan easked for VPN user.

Any help will be apreciated.


Here's what appares in syslog:

Oct 12 11:15:47 emil-desktop NetworkManager: <info>  Will activate VPN connection 'LEN', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'emil', vpn_data 'ppp-connection-type / pptp / pptp-remote / nerd.homelinux.org / usepeerdns / yes / encrypt-mppe / yes / encrypt-mppe-128 / yes / encrypt-mppe-stateful / no / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Oct 12 11:15:47 emil-desktop NetworkManager: <info>  VPN Activation (LEN) Stage 1 of 4 (Connection Prepare) scheduled... 
Oct 12 11:15:47 emil-desktop NetworkManager: <info>  VPN Activation (LEN) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 8518) 
Oct 12 11:15:47 emil-desktop NetworkManager: <info>  VPN Activation (LEN) Stage 1 of 4 (Connection Prepare) complete. 
Oct 12 11:15:47 emil-desktop NetworkManager: <info>  VPN Activation (LEN) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Oct 12 11:15:47 emil-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Oct 12 11:15:48 emil-desktop NetworkManager: <info>  VPN Activation (LEN) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Oct 12 11:15:48 emil-desktop NetworkManager: <info>  VPN Activation (LEN) Stage 2 of 4 (Connection Prepare Wait) complete. 
Oct 12 11:15:48 emil-desktop NetworkManager: <info>  VPN Activation (LEN) Stage 3 of 4 (Connect) scheduled... 
Oct 12 11:15:48 emil-desktop NetworkManager: <info>  VPN Activation (LEN) Stage 3 of 4 (Connect) sending connect request. 
Oct 12 11:15:48 emil-desktop NetworkManager: <info>  VPN Activation (LEN) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Oct 12 11:15:48 emil-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Oct 12 11:15:48 emil-desktop pppd[8519]: Plugin nm-pppd-plugin.so loaded.
Oct 12 11:15:48 emil-desktop pppd[8519]: nm-pppd-plugin: plugin initialized.
Oct 12 11:15:48 emil-desktop pppd[8520]: pppd 2.4.4 started by root, uid 0
Oct 12 11:15:48 emil-desktop pptp[8523]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Oct 12 11:15:48 emil-desktop NetworkManager: <info>  VPN Activation (LEN) Stage 3 of 4 (Connect) reply received. 
Oct 12 11:15:48 emil-desktop NetworkManager: <info>  VPN Activation (LEN) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Oct 12 11:15:48 emil-desktop NetworkManager: <info>  VPN Activation (LEN) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Oct 12 11:15:48 emil-desktop pppd[8520]: using channel 22
Oct 12 11:15:48 emil-desktop pppd[8520]: Using interface ppp0
Oct 12 11:15:48 emil-desktop pppd[8520]: Connect: ppp0 <--> /dev/pts/2
Oct 12 11:15:48 emil-desktop pptp[8526]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Oct 12 11:15:48 emil-desktop pptp[8526]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Oct 12 11:15:48 emil-desktop pptp[8526]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Oct 12 11:15:49 emil-desktop pppd[8520]: nm-pppd-plugin: CHAP check hook.
Oct 12 11:15:49 emil-desktop pppd[8520]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0x4707590b> <pcomp> <accomp>]
Oct 12 11:15:49 emil-desktop pptp[8526]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Oct 12 11:15:49 emil-desktop pptp[8526]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Oct 12 11:15:49 emil-desktop pptp[8526]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 23028). 
Oct 12 11:15:52 emil-desktop pppd[8520]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0x4707590b> <pcomp> <accomp>]
Oct 12 11:15:58 emil-desktop last message repeated 2 times
Oct 12 11:15:59 emil-desktop pppd[8520]: Terminating on signal 15
Oct 12 11:15:59 emil-desktop pppd[8520]: sent [LCP TermReq id=0x2 "User request"]
Oct 12 11:15:59 emil-desktop NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Oct 12 11:15:59 emil-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Oct 12 11:15:59 emil-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
Oct 12 11:15:59 emil-desktop NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'LEN' because service was 6. 
Oct 12 11:15:59 emil-desktop pptp[8526]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
Oct 12 11:15:59 emil-desktop pptp[8526]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Oct 12 11:15:59 emil-desktop pptp[8526]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Oct 12 11:15:59 emil-desktop pppd[8520]: Child process /usr/sbin/pptp 84.49.145.250 --nolaunchpppd (pid 8522) terminated with signal 15
Oct 12 11:15:59 emil-desktop pppd[8520]: Modem hangup
Oct 12 11:15:59 emil-desktop pppd[8520]: Connection terminated.
Oct 12 11:15:59 emil-desktop pppd[8520]: Exit.

---

