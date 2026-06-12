---
title: "PPTP VPN NetworkManager Ubuntu 7.10 can not set up connection"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by mirko1 on 2008-01-29
Hello experts

I have installed Ubuntu 7.10 , it is not possible to set PPTP connection via VPN from NetworkManager (Internet from Golden Telecom). 
Network address is  automatically determined, other computers in local network is visible.
VPN gateway is pinged successfully. But VPN is not connected. Who can suggest me what I am doing wrong?
network-manager-pptp parameters are visible in the syslog.
I have installed  pptp-linux (pptp-linux_1.7.0-2ubuntu2_i386.deb) and network-manager-pptp (network-manager-pptp_0.6.5 + svnhead2574-0ubuntu1_i386.deb).

syslog shows
```
Jan 24 21:39:15 novomir-laptop NetworkManager: <debug> [1201199955.787078] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of VPN connection 'Golden' 
Jan 24 21:39:15 novomir-laptop NetworkManager: <debug> [1201199955.787728] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of VPN connection 'Golden' 
Jan 24 21:39:23 novomir-laptop NetworkManager: <info>  Will activate VPN connection 'Golden', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'novomir', vpn_data 'ppp-connection-type / pptp / pptp-remote / fttb-vpn.mosreg.golden.ru / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / no / encrypt-mppe-stateful / no / compress-mppc / no / compress-deflate / yes / compress-bsd / yes / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / yes / ppp-refuse-mschap / yes / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Jan 24 21:39:23 novomir-laptop NetworkManager: <info>  VPN Activation (Golden) Stage 1 of 4 (Connection Prepare) scheduled... 
Jan 24 21:39:23 novomir-laptop NetworkManager: <info>  VPN Activation (Golden) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 6467) 
Jan 24 21:39:23 novomir-laptop NetworkManager: <info>  VPN Activation (Golden) Stage 1 of 4 (Connection Prepare) complete. 
Jan 24 21:39:23 novomir-laptop NetworkManager: <info>  VPN Activation (Golden) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Jan 24 21:39:23 novomir-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Jan 24 21:39:23 novomir-laptop NetworkManager: <info>  VPN Activation (Golden) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Jan 24 21:39:23 novomir-laptop NetworkManager: <info>  VPN Activation (Golden) Stage 2 of 4 (Connection Prepare Wait) complete. 
Jan 24 21:39:23 novomir-laptop NetworkManager: <info>  VPN Activation (Golden) Stage 3 of 4 (Connect) scheduled... 
Jan 24 21:39:23 novomir-laptop NetworkManager: <info>  VPN Activation (Golden) Stage 3 of 4 (Connect) sending connect request. 
Jan 24 21:39:23 novomir-laptop NetworkManager: <info>  VPN Activation (Golden) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Jan 24 21:39:23 novomir-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Jan 24 21:39:24 novomir-laptop pppd[6468]: Plugin nm-pppd-plugin.so loaded.
Jan 24 21:39:24 novomir-laptop pppd[6468]: nm-pppd-plugin: plugin initialized.
Jan 24 21:39:24 novomir-laptop NetworkManager: <info>  VPN Activation (Golden) Stage 3 of 4 (Connect) reply received. 
Jan 24 21:39:24 novomir-laptop NetworkManager: <info>  VPN Activation (Golden) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Jan 24 21:39:24 novomir-laptop NetworkManager: <info>  VPN Activation (Golden) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Jan 24 21:39:24 novomir-laptop pppd[6469]: pppd 2.4.4 started by root, uid 0
Jan 24 21:39:24 novomir-laptop pppd[6469]: using channel 2
Jan 24 21:39:24 novomir-laptop pppd[6469]: Using interface ppp0
Jan 24 21:39:24 novomir-laptop pppd[6469]: Connect: ppp0 <--> /dev/pts/1
Jan 24 21:39:24 novomir-laptop pptp[6472]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Jan 24 21:39:24 novomir-laptop pptp[6475]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Jan 24 21:39:24 novomir-laptop pptp[6475]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Jan 24 21:39:24 novomir-laptop pptp[6475]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Jan 24 21:39:25 novomir-laptop pppd[6469]: nm-pppd-plugin: CHAP check hook.
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0xa23ca7d> <pcomp> <accomp>]
Jan 24 21:39:25 novomir-laptop pptp[6475]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Jan 24 21:39:25 novomir-laptop pptp[6475]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Jan 24 21:39:25 novomir-laptop pptp[6475]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 19583). 
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0x1 <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfNak id=0x1 <auth chap MS-v2>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfNak id=0x1 <mru 1500>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0xa23ca7d> <pcomp> <accomp>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0x2 <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfNak id=0x2 <auth chap MS-v2>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfAck id=0x2 <asyncmap 0x0> <magic 0xa23ca7d> <pcomp> <accomp>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0x3 <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfNak id=0x3 <auth chap MS-v2>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0x4 <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfNak id=0x4 <auth chap MS-v2>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0x5 <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfNak id=0x5 <auth chap MS-v2>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0x6 <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfRej id=0x6 <auth pap>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0x7 <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfRej id=0x7 <auth pap>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0x8 <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfRej id=0x8 <auth pap>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0x9 <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfRej id=0x9 <auth pap>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0xa <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfRej id=0xa <auth pap>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0xb <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfRej id=0xb <auth pap>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0xc <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfRej id=0xc <auth pap>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0xd <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfRej id=0xd <auth pap>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0xe <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfRej id=0xe <auth pap>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0xf <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfRej id=0xf <auth pap>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP TermReq id=0x10]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP TermAck id=0x10]
Jan 24 21:39:25 novomir-laptop pptp[6475]: anon log[ctrlp_disp:pptp_ctrl.c:928]: Call disconnect notification received (call id 19583)
Jan 24 21:39:25 novomir-laptop pptp[6475]: anon log[ctrlp_disp:pptp_ctrl.c:787]: Received Stop Control Connection Request.
Jan 24 21:39:25 novomir-laptop pptp[6475]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 4 'Stop-Control-Connection-Reply' 
Jan 24 21:39:25 novomir-laptop pptp[6475]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
Jan 24 21:39:25 novomir-laptop pptp[6475]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Jan 24 21:39:25 novomir-laptop pptp[6475]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Jan 24 21:39:25 novomir-laptop pppd[6469]: Modem hangup
Jan 24 21:39:25 novomir-laptop pppd[6469]: Connection terminated.
Jan 24 21:39:25 novomir-laptop pppd[6469]: Script /usr/sbin/pptp 172.21.224.66 --nolaunchpppd finished (pid 6471), status = 0x0
Jan 24 21:39:25 novomir-laptop pppd[6469]: Exit.
Jan 24 21:39:35 novomir-laptop NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Jan 24 21:39:35 novomir-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Jan 24 21:39:35 novomir-laptop NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'Golden' because service was 5. 
Jan 24 21:39:35 novomir-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
```

WindowsXP VPN parameters are shown on screenshot below
[IMG]http://broadband.golden.ru/images/xp_vpn_9.jpg[/IMG]

regards
Novomir

---

### Post by mpokrywka on 2008-01-30
```
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0x5 <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfNak id=0x5 <auth chap MS-v2>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: rcvd [LCP ConfReq id=0x6 <auth pap> <magic 0x3235037a>]
Jan 24 21:39:25 novomir-laptop pppd[6469]: sent [LCP ConfRej id=0x6 <auth pap>]

```
Probably you checked refuse-pap or something similar in network manager configuration...

---

### Post by Juaqin on 2008-03-04
Hey! I have same problem on GoldenTelecom. Please post solution/progress if any ?

---

### Post by mirko1 on 2008-03-05
No progress yet. I have to use Windows for Internet.

---

### Post by DonnOMalley on 2008-03-07
Try this:
[LIST]
[*] Left Click your network icon on the panel, select "VPN Connections" and "Configure VPN".
[*] Create a New Connection using "Add"
[*] Select "PPTP tunnel" for your type of VPN Connection
[*] Type in a name for the connection and your VPN Server Address for your gateway and save the connection.
[*] Make a copy of your /etc/resolv.conf file (This gets overwritten when VPN Connects)
[*] Connect to the VPN connection just created
[*] Put your copy of resolv.conf back into the /etc directory
[*] Set up your routes to look like:
[INDENT]
68.87.xx.xxx gw 192.168.1.1 netmask 255.255.255.255 eth0 (DNS 1)
68.87.xx.xxx gw 192.168.1.1 netmask 255.255.255.255 eth0 (DNS 2)
209.172.xxx.xxx gw 192.168.1.1 netmask 255.255.255.255 eth0 (VPN Server)
209.172.xxx.xxx gw * netmask 255.255.255.255 ppp0 (VPN Server)
10.0.0.0 gw 209.172.xxx.xxx netmask 255.255.255.0 ppp0 (VPN Subnet with VPN Server as Gateway)
192.168.1.0 gw * netmask 255.255.255.0 eth0 (Local Subnet)
default gw 192.168.1.1 netmask 0.0.0.0.0 eth0 
[/INDENT]
[/LIST]
At least this is what has worked for me. It took a lot of trial and error, but with this config, i can successfully browse my Network at work over PPTP and the internet over my local network.

---

