---
title: "connecting to relakks pptp using Knetwork Manager"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by dragoon3seven on 2008-06-28
I'm using a D531 dell laptop with Kubuntu 8.04 (KDE3)

trying to connect to relakks but with little luck.

Using KNetwork Manager with latest updates, and on a fresh install of Kubuntu 8.04 also with latest updates. 

Here's my syslog, any help is appreciated. :D

```
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  Will activate VPN connection 'Relakks', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'dhca89', vpn_data 'ppp-connection-type / pptp / pptp-remote / pptp.relakks.com / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / yes / encrypt-mppe-stateful / no / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1400 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN Activation (Relakks) Stage 1 of 4 (Connection Prepare) scheduled... 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN Activation (Relakks) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 8411) 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN Activation (Relakks) Stage 1 of 4 (Connection Prepare) complete. 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN Activation (Relakks) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN Activation (Relakks) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN Activation (Relakks) Stage 2 of 4 (Connection Prepare Wait) complete. 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN Activation (Relakks) Stage 3 of 4 (Connect) scheduled... 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN Activation (Relakks) Stage 3 of 4 (Connect) sending connect request. 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN Activation (Relakks) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN Activation (Relakks) Stage 3 of 4 (Connect) reply received. 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN Activation (Relakks) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Jun 28 08:21:26 d531kde3 NetworkManager: <info>  VPN Activation (Relakks) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Jun 28 08:21:27 d531kde3 pppd[8414]: Plugin nm-pppd-plugin.so loaded.
Jun 28 08:21:27 d531kde3 pppd[8414]: nm-pppd-plugin: plugin initialized.
Jun 28 08:21:27 d531kde3 kernel: [  230.120882] PPP generic driver version 2.4.2
Jun 28 08:21:27 d531kde3 pppd[8423]: pppd 2.4.4 started by root, uid 0
Jun 28 08:21:27 d531kde3 pptp[8427]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Jun 28 08:21:27 d531kde3 pppd[8423]: Using interface ppp0
Jun 28 08:21:27 d531kde3 pppd[8423]: Connect: ppp0 <--> /dev/pts/1
Jun 28 08:21:28 d531kde3 pppd[8423]: nm-pppd-plugin: CHAP check hook.
Jun 28 08:21:30 d531kde3 pptp[8451]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Jun 28 08:21:38 d531kde3 pppd[8423]: Terminating on signal 15
Jun 28 08:21:38 d531kde3 NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Jun 28 08:21:38 d531kde3 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Jun 28 08:21:38 d531kde3 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
Jun 28 08:21:38 d531kde3 NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'Relakks' because service was 6. 
Jun 28 08:21:38 d531kde3 pppd[8423]: Child process /usr/sbin/pptp 83.233.169.2 --nolaunchpppd (pid 8426) terminated with signal 15
Jun 28 08:21:38 d531kde3 pppd[8423]: Modem hangup
Jun 28 08:21:38 d531kde3 pppd[8423]: Connection terminated.
Jun 28 08:21:38 d531kde3 pppd[8423]: Exit.
Jun 28 08:22:20 d531kde3 NetworkManager: <info>  Updating allowed wireless network lists. 
Jun 28 08:22:20 d531kde3 NetworkManager: <info>  Updating VPN Connections... 
```

---

