---
title: "Feisty VPN Error: Didn't receive an Internal IP4 Address from ppp"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by deyoungaza on 2007-05-22
I had VPN working well in Dapper using PPTP Client. Last week, I did a clean install of Feisty for a friend and decided to try out the new VPN feature in network manager on his machine. It worked fine.

So, I installed Feisty on my laptop with a clean install of the root partition, but keeping my old /home partition.

Now, I can't connect to my office VPN.

[LIST]
[*]I used the same configuration as the one on my friends' machine.
[*]I turned the firewall off using Firestarter.
[*]I even took my laptop to his office to try to connect through his network -- the one that works for him.
[/LIST]

Still, no-go.

Here is the output from syslog:


> 
NetworkManager: <information>^IWill activate VPN connection 'Test', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'deyoungaza', vpn_data 'ppp-connection-type / pptp / pptp-remote / vpn.test.com / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
May 22 06:31:57 deyoungaza-laptop NetworkManager: <information>^IVPN Activation (Test) Stage 1 of 4 (Connection Prepare) scheduled... 
May 22 06:31:57 deyoungaza-laptop NetworkManager: <information>^IVPN Activation (Test) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 8780) 
May 22 06:31:57 deyoungaza-laptop NetworkManager: <information>^IVPN Activation (Test) Stage 1 of 4 (Connection Prepare) complete. 
May 22 06:31:57 deyoungaza-laptop NetworkManager: <information>^IVPN Activation (Test) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
May 22 06:31:58 deyoungaza-laptop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
May 22 06:31:58 deyoungaza-laptop NetworkManager: <information>^IVPN Activation (Test) Stage 2 of 4 (Connection Prepare Wait) waiting... 
May 22 06:31:58 deyoungaza-laptop NetworkManager: <information>^IVPN Activation (Test) Stage 2 of 4 (Connection Prepare Wait) complete. 
May 22 06:31:58 deyoungaza-laptop NetworkManager: <information>^IVPN Activation (Test) Stage 3 of 4 (Connect) scheduled... 
May 22 06:31:58 deyoungaza-laptop NetworkManager: <information>^IVPN Activation (Test) Stage 3 of 4 (Connect) sending connect request. 
May 22 06:31:58 deyoungaza-laptop NetworkManager: <information>^IVPN Activation (Test) Stage 3 of 4 (Connect) request sent, waiting for reply... 
May 22 06:31:58 deyoungaza-laptop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
May 22 06:31:58 deyoungaza-laptop pppd[8781]: Plugin nm-pppd-plugin.so loaded.
May 22 06:31:58 deyoungaza-laptop pppd[8781]: nm-pppd-plugin: plugin initialized.
May 22 06:31:58 deyoungaza-laptop NetworkManager: <information>^IVPN Activation (Test) Stage 3 of 4 (Connect) reply received. 
May 22 06:31:58 deyoungaza-laptop NetworkManager: <information>^IVPN Activation (Test) Stage 4 of 4 (IP Config Get) timeout scheduled... 
May 22 06:31:58 deyoungaza-laptop NetworkManager: <information>^IVPN Activation (Test) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
May 22 06:31:58 deyoungaza-laptop pppd[8782]: pppd 2.4.4 started by root, uid 0
May 22 06:31:58 deyoungaza-laptop pptp[8785]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
May 22 06:31:58 deyoungaza-laptop pppd[8782]: Using interface ppp1
May 22 06:31:58 deyoungaza-laptop pppd[8782]: Connect: ppp1 <--> /dev/pts/0
May 22 06:31:58 deyoungaza-laptop pptp[8788]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
May 22 06:31:58 deyoungaza-laptop pptp[8788]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
May 22 06:31:58 deyoungaza-laptop pptp[8788]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
May 22 06:31:59 deyoungaza-laptop pppd[8782]: nm-pppd-plugin: CHAP check hook.
May 22 06:31:59 deyoungaza-laptop pptp[8788]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
May 22 06:31:59 deyoungaza-laptop pptp[8788]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
May 22 06:31:59 deyoungaza-laptop pptp[8788]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 998). 
May 22 06:31:59 deyoungaza-laptop pptp[8788]: anon log[ctrlp_disp:pptp_ctrl.c:949]: PPTP_SET_LINK_INFO received from peer_callid 0
May 22 06:31:59 deyoungaza-laptop pptp[8788]: anon log[ctrlp_disp:pptp_ctrl.c:952]:   send_accm is 00000000, recv_accm is FFFFFFFF
May 22 06:31:59 deyoungaza-laptop pptp[8788]: anon warn[ctrlp_disp:pptp_ctrl.c:955]: Non-zero Async Control Character Maps are not supported!
May 22 06:31:59 deyoungaza-laptop pppd[8782]: nm-pppd-plugin: CHAP credentials requested.
May 22 06:31:59 deyoungaza-laptop pppd[8782]: CHAP authentication succeeded
May 22 06:31:59 deyoungaza-laptop pppd[8782]: MPPE 128-bit stateless compression enabled
May 22 06:32:01 deyoungaza-laptop pppd[8782]: Cannot determine ethernet address for proxy ARP
May 22 06:32:01 deyoungaza-laptop pppd[8782]: local  IP address 192.168.151.13
May 22 06:32:01 deyoungaza-laptop pppd[8782]: remote IP address 192.168.151.1
May 22 06:32:01 deyoungaza-laptop pppd[8782]: primary   DNS address 127.0.0.1
May 22 06:32:01 deyoungaza-laptop pppd[8782]: nm-pppd-plugin: didn't receive an Internal IP4 Address from ppp.
May 22 06:32:01 deyoungaza-laptop NetworkManager: <WARNING>^I nm_vpn_service_process_signal (): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'IPConfigBad', with message 'VPN Connection failed'. 
May 22 06:32:01 deyoungaza-laptop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
May 22 06:32:01 deyoungaza-laptop NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
May 22 06:32:01 deyoungaza-laptop NetworkManager: <WARNING>^I nm_vpn_service_stop_connection (): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'Test' because service was 6. 
May 22 06:32:01 deyoungaza-laptop pptp[8788]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
May 22 06:32:01 deyoungaza-laptop pptp[8788]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
May 22 06:32:01 deyoungaza-laptop pptp[8788]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
May 22 06:32:01 deyoungaza-laptop pppd[8782]: Terminating on signal 15
May 22 06:32:01 deyoungaza-laptop pppd[8782]: Connect time 0.0 minutes.
May 22 06:32:01 deyoungaza-laptop pppd[8782]: Sent 0 bytes, received 0 bytes.
May 22 06:32:01 deyoungaza-laptop pppd[8782]: MPPE disabled
May 22 06:32:01 deyoungaza-laptop pppd[8782]: Modem hangup
May 22 06:32:01 deyoungaza-laptop pppd[8782]: Connection terminated.
May 22 06:32:01 deyoungaza-laptop pppd[8782]: Child process /usr/sbin/pptp 212.199.63.74 --nolaunchpppd (pid 8784) terminated with signal 15
May 22 06:32:02 deyoungaza-laptop pppd[8782]: Exit.


I connect through my ADSL at home via pppoe, or though a local DNS network with gateway  in the office.

I work three days a week over my VPN, so this is kind of critical.

Thanks

---

### Post by innuendosoft on 2007-06-27
Having the exact same issue here :(

---

