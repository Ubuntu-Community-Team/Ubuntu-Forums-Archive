---
title: "VPN to OS X 10.5"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by YaacovI on 2008-07-24
I'm trying to connect to a VPN running on an OS X 10.5 server. I'm getting "VPN connection error". A co-worker with a Mac is able to connect to the VPN and to able to do so using my username/password (reset, of course).

When I try to connect, this is what I see in the daemon log:

Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  Will activate VPN connection 'Work', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'work', vpn_data 'ppp-connection-type / pptp / pptp-remote / IP.IP.IP.IP / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / no / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes / 192.168.99.0/24 / use-routes / yes', route '192.168.99.0/24'. 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN Activation (Work) Stage 1 of 4 (Connection Prepare) scheduled... 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN Activation (Work) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 9147) 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN Activation (Work) Stage 1 of 4 (Connection Prepare) complete. 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN Activation (Work) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN Activation (Work) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN Activation (Work) Stage 2 of 4 (Connection Prepare Wait) complete. 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN Activation (Work) Stage 3 of 4 (Connect) scheduled... 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN Activation (Work) Stage 3 of 4 (Connect) sending connect request. 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN Activation (Work) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Jul 23 14:49:09 massofincandescentgas pptp[9151]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN Activation (Work) Stage 3 of 4 (Connect) reply received. 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN Activation (Work) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Jul 23 14:49:09 massofincandescentgas NetworkManager: <info>  VPN Activation (Work) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Jul 23 14:49:09 massofincandescentgas pptp[9155]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Jul 23 14:49:09 massofincandescentgas pptp[9155]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Jul 23 14:49:09 massofincandescentgas pptp[9155]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Jul 23 14:49:10 massofincandescentgas pptp[9155]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Jul 23 14:49:10 massofincandescentgas pptp[9155]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Jul 23 14:49:10 massofincandescentgas pptp[9155]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 61228). 
Jul 23 14:49:10 massofincandescentgas pptp[9155]: anon log[pptp_read_some:pptp_ctrl.c:543]: read returned zero, peer has closed
Jul 23 14:49:10 massofincandescentgas pptp[9155]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
Jul 23 14:49:10 massofincandescentgas pptp[9155]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Jul 23 14:49:10 massofincandescentgas pptp[9155]: anon log[pptp_read_some:pptp_ctrl.c:543]: read returned zero, peer has closed
Jul 23 14:49:10 massofincandescentgas pptp[9155]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Jul 23 14:49:20 massofincandescentgas NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Jul 23 14:49:20 massofincandescentgas NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Jul 23 14:49:20 massofincandescentgas NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
Jul 23 14:49:20 massofincandescentgas NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'Work' because service was 6. 

And in the messages log:

Jul 23 14:49:09 massofincandescentgas pppd[9148]: Plugin nm-pppd-plugin.so loaded.
Jul 23 14:49:09 massofincandescentgas pppd[9148]: nm-pppd-plugin: plugin initialized.
Jul 23 14:49:09 massofincandescentgas pppd[9149]: pppd 2.4.4 started by root, uid 0
Jul 23 14:49:09 massofincandescentgas pppd[9149]: Using interface ppp0
Jul 23 14:49:09 massofincandescentgas pppd[9149]: Connect: ppp0 <--> /dev/pts/2
Jul 23 14:49:10 massofincandescentgas pppd[9149]: nm-pppd-plugin: CHAP check hook.
Jul 23 14:49:10 massofincandescentgas pppd[9149]: nm-pppd-plugin: CHAP credentials requested.
Jul 23 14:49:10 massofincandescentgas pppd[9149]: Connection terminated.
Jul 23 14:49:10 massofincandescentgas pppd[9149]: Exit.

---

### Post by doloctona on 2009-09-28
I'm in much the same position - my company runs an OSX server to provide VPN access (IPSec/L2TP), and I have had little luck bringing up a connection.

My approach has been to use ipsec (ipsec-tools package), and this works now (using a pre-shared key, if I had to deal with certificates, it might be another matter).  However, the L2TP side of things (PPP) is proving somewhat difficult.  I have read the very useful howto at [http://www.jacco2.dds.nl/networking/linux-l2tp.html](http://www.jacco2.dds.nl/networking/linux-l2tp.html), and this has helped immensely, but xl2tpd is still spitting out errors.

In case anyone is reading this, my specific errors are (ip address hidden for companies safety):

xl2tpd[12462]: Connecting to host 2xx.2xx.2xx.xxx, port 1701
xl2tpd[12462]: Maximum retries exceeded for tunnel 31523. Closing.
xl2tpd[12462]: Connection 0 closed to 2xx.2xx.2xx.xxx, port 1701 (Timeout)
xl2tpd[12462]: Unable to deliver closing message for tunnel 31523. Destroying anyway.

Anyone have any ideas here?

---

