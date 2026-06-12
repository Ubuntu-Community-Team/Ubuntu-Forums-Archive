---
title: "VPN Connection problem"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by dukejib on 2008-03-09
Hi,
I have tried each and everything to make this vpn connection able to work, but is in vein
Also, I have installed pptpconfig , so that i can easily make the configuration changes, but it is not even showing up, i have tried gksu pptpconfig , but it is not working.
The connection is connecting to server, but there is no browsing what so ever.

Here is the syslog entry.

```
Mar  9 22:16:01 starblazer NetworkManager: <info>  Will activate VPN connection 'VPN', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'ali', vpn_data 'ppp-connection-type / pptp / pptp-remote / crras.connect.net.pk / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / no / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 1 of 4 (Connection Prepare) scheduled... 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 6559) 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 1 of 4 (Connection Prepare) complete. 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 2 of 4 (Connection Prepare Wait) complete. 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 3 of 4 (Connect) scheduled... 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 3 of 4 (Connect) sending connect request. 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 3 of 4 (Connect) reply received. 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Mar  9 22:16:01 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Mar  9 22:16:01 starblazer pppd[6560]: Plugin nm-pppd-plugin.so loaded.
Mar  9 22:16:01 starblazer pppd[6560]: nm-pppd-plugin: plugin initialized.
Mar  9 22:16:01 starblazer pppd[6564]: pppd 2.4.4 started by root, uid 0
Mar  9 22:16:01 starblazer pptp[6566]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Mar  9 22:16:01 starblazer pptp[6569]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Mar  9 22:16:01 starblazer pptp[6569]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Mar  9 22:16:01 starblazer pptp[6569]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Mar  9 22:16:01 starblazer pppd[6564]: Using interface ppp0
Mar  9 22:16:01 starblazer pppd[6564]: Connect: ppp0 <--> /dev/pts/0
Mar  9 22:16:02 starblazer pptp[6569]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Mar  9 22:16:02 starblazer pppd[6564]: nm-pppd-plugin: CHAP check hook.
Mar  9 22:16:02 starblazer pptp[6569]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Mar  9 22:16:02 starblazer pptp[6569]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 32858). 
Mar  9 22:16:05 starblazer pptp[6569]: anon log[ctrlp_disp:pptp_ctrl.c:949]: PPTP_SET_LINK_INFO received from peer_callid 0
Mar  9 22:16:05 starblazer pptp[6569]: anon log[ctrlp_disp:pptp_ctrl.c:952]:   send_accm is 00000000, recv_accm is FFFFFFFF
Mar  9 22:16:05 starblazer pptp[6569]: anon warn[ctrlp_disp:pptp_ctrl.c:955]: Non-zero Async Control Character Maps are not supported!
Mar  9 22:16:05 starblazer pppd[6564]: nm-pppd-plugin: CHAP credentials requested.
Mar  9 22:16:05 starblazer pppd[6564]: CHAP authentication succeeded
Mar  9 22:16:08 starblazer pppd[6564]: Cannot determine ethernet address for proxy ARP
Mar  9 22:16:08 starblazer pppd[6564]: local  IP address 118.103.225.199
Mar  9 22:16:08 starblazer pppd[6564]: remote IP address 118.103.224.1
Mar  9 22:16:08 starblazer pppd[6564]: primary   DNS address 10.101.10.1
Mar  9 22:16:08 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 4 of 4 (IP Config Get) reply received. 
Mar  9 22:16:09 starblazer NetworkManager: <info>  Clearing nscd hosts cache. 
Mar  9 22:16:09 starblazer NetworkManager: <info>  VPN Activation (VPN) Stage 4 of 4 (IP Config Get) complete. 
Mar  9 22:16:09 starblazer NetworkManager: <info>  VPN Activation (VPN) successful. 
Mar  9 22:16:09 starblazer NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 4. 


```

Help me out please

---

### Post by dukejib on 2008-03-09
One More Thing

I can connect to my vista Vpn connection only using;

UserName
Password
Server name
No Encryption

Thanks in Advance for your help.:)

---

### Post by dukejib on 2008-03-22
Hello!
Isn't there any one to help me out :(

---

### Post by farahbod on 2008-03-24
Hi dukejib

You said that you successfully connected to the server?

What do you mean by "The connection is connecting to server, but there is no browsing what so ever"?
After connecting and before sending data, you have to set up routes!
If you use the connection to browse internet you should execute the following command:

sudo route add default gw 118.103.224.1

note that 118.103.224.1 is the IP address of your server. However you could create a script to automate the task.

dukejib@system>sudo -i
root@system#touch /etc/ppp/ip-up.d/ConnectionName

then open it (with vi, nano, ...) and put the following  2 lines in there:
#!/bin/bash
route add default gw 118.103.224.1

save and close.

root@system#chmod a+x /etc/ppp/ip-up.d/ConnectionName


Connect:
root@system# pon ConnectionName

Disconnect:
root@system# poff ConnectionName


where the ConnectionName is the name of connection you made by pptpconfig.
Hope be useful

---

### Post by dukejib on 2008-04-21
> **farahbod said:**
> Hi dukejib

You said that you successfully connected to the server?

What do you mean by "The connection is connecting to server, but there is no browsing what so ever"?
After connecting and before sending data, you have to set up routes!
If you use the connection to browse internet you should execute the following command:

sudo route add default gw 118.103.224.1

note that 118.103.224.1 is the IP address of your server. However you could create a script to automate the task.

dukejib@system>sudo -i
root@system#touch /etc/ppp/ip-up.d/ConnectionName

then open it (with vi, nano, ...) and put the following  2 lines in there:
#!/bin/bash
route add default gw 118.103.224.1

save and close.

root@system#chmod a+x /etc/ppp/ip-up.d/ConnectionName


Connect:
root@system# pon ConnectionName

Disconnect:
root@system# poff ConnectionName


where the ConnectionName is the name of connection you made by pptpconfig.
Hope be useful
Thanks for Reply Farahbod
I mean to say that I can check out the host by typing [www.yahoo.com](www.yahoo.com) [www.google.com](www.google.com) but i cannot browse the same domains via firefox or lynx etc.
Also, there is no activity for gaim too.
Ok, I will try to do the steps as mentioned by you, then i will get back to you again.

---

### Post by teledyn on 2008-07-17
This is really quite embarrassing.  I installed the pptpd-server on one of our server-farm machines (debian) and one of the developers was able to connect to it immediately using a Windows XP machine, but I cannot find the magic combination to make Ubuntu Gutsy connect with the NetworkManager wizard. I have all the options set very plain and ordinary except the network routing where I had to limit the connection to three external networks (do I need to add the pptp LAN network to that list?)

but it will not go.  I notice the default on the pptpd server config is to refuse eap, chap and mschap and to require mschap-v2, but the NetworkManager does not provide for mschap-v2 -- I tried adding "require-mschap-v2" into /etc/ppp/options.pptp but it had no effect.  I tried adding it into the custom PPP options dialog, but it was rejected as invalid.

the dialog says any entered options are checked against "allowed" options, but it does not say where that list lives  or if it can be extended.

the log is not very informative:

Jul 17 14:45:54 uhuru pptp[31297]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 512). 
Jul 17 14:45:55 uhuru pptp[31297]: anon log[pptp_read_some:pptp_ctrl.c:543]: read returned zero, peer has closed
Jul 17 14:45:55 uhuru pptp[31297]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
Jul 17 14:45:55 uhuru pptp[31297]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Jul 17 14:45:55 uhuru pptp[31297]: anon log[pptp_read_some:pptp_ctrl.c:543]: read returned zero, peer has closed

the server log only says "Connection closed"

---

### Post by teledyn on 2008-07-17
to follow up that last post, the /etc/pptpd.conf on the server side contains only 

option /etc/ppp/pptpd-options
logwtmp
localip 192.168.0.1
remoteip 192.168.0.234-238,192.168.0.245

 and the /etc/ppp/pptpd-options is very plain:

name pptpd
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
proxyarp
nodefaultroute
lock
nobsdcomp

---

