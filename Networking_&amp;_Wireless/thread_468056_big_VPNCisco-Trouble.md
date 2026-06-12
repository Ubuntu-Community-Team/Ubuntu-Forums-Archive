---
title: "big VPN/Cisco-Trouble"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by e-the-real on 2007-06-08
hi guys, 
sorry for coming up with this poor topic, but i have problems creating a vpn connection to a Win-VPN network. i've already searched tons of threads in a few communities and asked some guys (some linux freaks of my university - i am studying computer science so i should be able to help myself - well, unfortunately i am not ), but it doesn't help. although i do not seem to be the only one with vpn-troubles, i haven't got the right hint yet, so i hope, i find some advices right here. ok lets start with some facts: 

OS- ubuntu feisty  7.04 without modifieing any considerable system configs, no firewall, no router

1st try Network-Manager + pptp-plugin. After having installed pptp-linux and plugins and creating a new connection, network manager tries to connect (there is a golden lightning ( kind of ) dancing round the network symbol next to a little golden lock) but fails after about 3-5 seconds saying something like "could not create connection as the vpn server does not provide a suitable network configuration" (german, translated into poor english). 
i got this reply with any permutation of settings enabled i tried out. a friend of mine sent his pcf-file to me with which he is able to connect to the same vpn network, but it does not work so this might not be a consequence of perhaps wrong settings. here is the syslog: 

```

May 30 19:26:14 konstantin-desktop NetworkManager: <information>^IWill activate VPN connection 'FU Info', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'konstantin', vpn_data 'ppp-connection-type / pptp / pptp-remote / 160.45.113.141 / usepeerdns / yes / encrypt-mppe / yes / encrypt-mppe-128 / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra / / ppp-debug / no / usepeerdns-overtunnel / yes / routes / / use-routes / no', route ''.
May 30 19:26:14 konstantin-desktop NetworkManager: <information>^IVPN Activation (FU Info) Stage 1 of 4 (Connection Prepare) scheduled...
May 30 19:26:14 konstantin-desktop NetworkManager: <information>^IVPN Activation (FU Info) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 10223)
May 30 19:26:14 konstantin-desktop NetworkManager: <information>^IVPN Activation (FU Info) Stage 1 of 4 (Connection Prepare) complete.
May 30 19:26:14 konstantin-desktop NetworkManager: <information>^IVPN Activation (FU Info) Stage 2 of 4 (Connection Prepare Wait) scheduled...
May 30 19:26:14 konstantin-desktop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6.
May 30 19:26:15 konstantin-desktop NetworkManager: <information>^IVPN Activation (FU Info) Stage 2 of 4 (Connection Prepare Wait) waiting...
May 30 19:26:15 konstantin-desktop NetworkManager: <information>^IVPN Activation (FU Info) Stage 2 of 4 (Connection Prepare Wait) complete.
May 30 19:26:15 konstantin-desktop NetworkManager: <information>^IVPN Activation (FU Info) Stage 3 of 4 (Connect) scheduled...
May 30 19:26:15 konstantin-desktop NetworkManager: <information>^IVPN Activation (FU Info) Stage 3 of 4 (Connect) sending connect request.
May 30 19:26:15 konstantin-desktop NetworkManager: <information>^IVPN Activation (FU Info) Stage 3 of 4 (Connect) request sent, waiting for reply...
May 30 19:26:15 konstantin-desktop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3.
May 30 19:26:15 konstantin-desktop NetworkManager: <information>^IVPN Activation (FU Info) Stage 3 of 4 (Connect) reply received.
May 30 19:26:15 konstantin-desktop NetworkManager: <information>^IVPN Activation (FU Info) Stage 4 of 4 (IP Config Get) timeout scheduled...
May 30 19:26:15 konstantin-desktop NetworkManager: <information>^IVPN Activation (FU Info) Stage 3 of 4 (Connect) complete, waiting for IP configuration...
May 30 19:26:15 konstantin-desktop pppd[10224 Plugin nm-pppd-plugin.so loaded.
May 30 19:26:15 konstantin-desktop pppd[10224]: nm-pppd-plugin: plugin initialized.
May 30 19:26:15 konstantin-desktop pppd[10226]: pppd 2.4.4 started by root, uid 0
May 30 19:26:15 konstantin-desktop pptp[10228]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated
May 30 19:26:15 konstantin-desktop pppd[10226]: Using interface ppp1
May 30 19:26:15 konstantin-desktop pppd[10226]: Connect: ppp1 <--> /dev/pts/1
May 30 19:26:15 konstantin-desktop pptp[10231]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
May 30 19:26:15 konstantin-desktop pptp[10231]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
May 30 19:26:15 konstantin-desktop pptp[10231]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
May 30 19:26:16 konstantin-desktop pppd[10226]: nm-pppd-plugin: CHAP check hook.
May 30 19:26:16 konstantin-desktop pptp[10231]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
May 30 19:26:16 konstantin-desktop pptp[10231]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
May 30 19:26:16 konstantin-desktop pptp[10231]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 61696).
May 30 19:26:16 konstantin-desktop pppd[10226]: nm-pppd-plugin: CHAP credentials requested.
May 30 19:26:16 konstantin-desktop pppd[10226]: CHAP authentication succeeded
May 30 19:26:16 konstantin-desktop pppd[10226]: MPPE 128-bit stateless compression enabled
May 30 19:26:19 konstantin-desktop pppd[10226]: Cannot determine ethernet address for proxy ARP
May 30 19:26:19 konstantin-desktop pppd[10226]: local IP address 160.45.116.6
May 30 19:26:19 konstantin-desktop pppd[10226]: remote IP address 160.45.116.1
May 30 19:26:19 konstantin-desktop pppd[10226]: primary DNS address 160.45.110.15
May 30 19:26:19 konstantin-desktop pppd[10226]: secondary DNS address 160.45.110.10
May 30 19:26:19 konstantin-desktop pppd[10226]: nm-pppd-plugin: didn't receive an Internal IP4 Address from ppp.
May 30 19:26:19 konstantin-desktop NetworkManager: <WARNING>^I nm_vpn_service_process_signal (): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'IPConfigBad', with message 'VPN Connection failed'.
May 30 19:26:19 konstantin-desktop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5.
May 30 19:26:19 konstantin-desktop NetworkManager: <WARNING>^I nm_vpn_service_stop_connection (): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'FU Info' because service was 5.
May 30 19:26:19 konstantin-desktop pptp[10231]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
May 30 19:26:19 konstantin-desktop pptp[10231]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
May 30 19:26:19 konstantin-desktop pptp[10231]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
May 30 19:26:19 konstantin-desktop pppd[10226]: Terminating on signal 15
May 30 19:26:19 konstantin-desktop pppd[10226]: Connect time 0.0 minutes.
May 30 19:26:19 konstantin-desktop pppd[10226]: Sent 0 bytes, received 0 bytes.
May 30 19:26:19 konstantin-desktop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6.
May 30 19:26:19 konstantin-desktop pppd[10226]: MPPE disabled
May 30 19:26:19 konstantin-desktop pppd[10226]: Child process /usr/sbin/pptp 160.45.113.141 --nolaunchpppd (pid 10227) terminated with signal 15
May 30 19:26:19 konstantin-desktop pppd[10226]: Modem hangup
May 30 19:26:19 konstantin-desktop pppd[10226]: Connection terminated.
May 30 19:26:19 konstantin-desktop pppd[10226]: Exit.
```



there is a line > nm-pppd-plugin: didn't receive an Internal IP4 Address from ppp. which sounds to be the bad point, but i am not sure and i do not know what to do against this error. 

2nd try -  pptpconfig from the shell, same settings. output is

> 
Using interface ppp1
pptpconfig: monitoring interface ppp1
Connect: ppp1 <--> /dev/pts/1
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP

then it hangs and nothing happens.

3rd try: cisco vpn client version 4.8.00, patched. output: 

> 
sudo vpnclient connect VPN@ZEDAT-hybrid
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Secure VPN Connection terminated locally by the Client
Reason: Failed to establish a VPN connection.
There are no new notification messages at this time.


this is an error many people seem to have. some got solutions (ifdown etho, then restarting vpnlient) but none of them work for me. 
so i hope, someone of you guys here has at least some ideas what i can try next since it is quite important to set up this stupid vpn connection in the next few days, so please, share your ideas and hints, i would be grateful for your help! 
Many thanks in advance
regards
konstantin

---

### Post by usererror on 2007-09-02
did you ever solve your problem?  I found that my work place's Cisco VPN Concentrator does not recognize a firewall on my Ubuntu laptop so it will not let me connect.  I was going to install Firestarter but i have not tried it yet.  Good luck!

---

### Post by oniichan on 2007-10-30
I had similar problems. This may not be much help but the client 'vpnc'  version 0.4.0-3ubuntu2 works well for Cisco VPN's....better than the Cisco client. But don't use Firestarter until the 1.1 version. Or turn it off during your VPN session. Good luck and I apologize in case it doesn't work.

---

