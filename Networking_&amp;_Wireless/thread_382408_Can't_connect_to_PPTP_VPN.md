---
title: "Can't connect to PPTP VPN"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by Reedbeta on 2007-03-12
Hi,

I've got the pptp plugin for network-manager installed in Edgy, but can't get connected to the (Microsoft) VPN server.  The connection fails with a generic "connection error" message.  /var/log/messages contains:
```

Mar 11 22:49:13 miniman pppd[6360]: Plugin nm-pppd-plugin.so loaded.
Mar 11 22:49:13 miniman pppd[6360]: nm-pppd-plugin: plugin initialized.
Mar 11 22:49:13 miniman pppd[6360]: nm-pppd-plugin: CHAP check hook.
Mar 11 22:49:13 miniman pppd[6363]: pppd 2.4.4 started by root, uid 0
Mar 11 22:49:13 miniman pppd[6363]: Using interface ppp0
Mar 11 22:49:13 miniman pppd[6363]: Connect: ppp0 <--> /dev/pts/2
Mar 11 22:49:14 miniman pppd[6363]: nm-pppd-plugin: CHAP check hook.
Mar 11 22:49:14 miniman pppd[6363]: nm-pppd-plugin: CHAP check hook.
Mar 11 22:49:23 miniman pppd[6363]: Terminating on signal 15
Mar 11 22:49:23 miniman pppd[6363]: Modem hangup
Mar 11 22:49:23 miniman pppd[6363]: Connection terminated.
Mar 11 22:49:23 miniman pppd[6363]: Child process /usr/sbin/pptp 134.173.72.2 --nolaunchpppd (pid 6364) terminated with signal 15
Mar 11 22:49:23 miniman pppd[6363]: Exit.

```
and /var/log/daemon.log contains
```

Mar 11 22:49:12 miniman NetworkManager: <information>^IWill activate VPN connection 'Pomona VPN', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'reedbeta', vpn_data 'ppp-connection-type / pptp / pptp-remote / vpn.pomona.edu / usepeerdns / yes / encrypt-mppe / yes / encrypt-mppe-128 / no / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / yes / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / yes / routes / 134.173.0.0/16 / use-routes / yes', route '134.173.0.0/16'. 
Mar 11 22:49:13 miniman pptp[6365]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Mar 11 22:49:13 miniman pptp[6370]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Mar 11 22:49:13 miniman pptp[6370]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Mar 11 22:49:13 miniman pptp[6370]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Mar 11 22:49:14 miniman pptp[6370]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Mar 11 22:49:14 miniman pptp[6370]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Mar 11 22:49:14 miniman pptp[6370]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 62951). 
Mar 11 22:49:20 miniman pptp[6370]: anon log[ctrlp_disp:pptp_ctrl.c:911]: Received Call Clear Request.
Mar 11 22:49:23 miniman pptp[6370]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
Mar 11 22:49:23 miniman pptp[6370]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Mar 11 22:49:23 miniman pptp[6370]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)

```

I can connect fine from Windows on the same machine, but haven't been able to get it to work in Ubuntu.  It seems as if the server disconnects me as soon as I am connected.  I also tried the pptpconfig utility and had problems with that as well; it would appear to connect but I could not ping anything on the remote LAN.  (Plus, I don't like pptpconfig very much; I hate having to run it with gksudo.)

Has *anyone* managed to get VPN working with network-manager?  Wanna tell us how you did it? :)

---

### Post by Lmax on 2007-05-03
I had a similar problem with the exact same errors and log output and I was able to fix it by changing the default MTU/MRU to 1500.

---

### Post by crb on 2007-05-13
Also ensure "refuse EAP, refuse CHAP and refuse MS CHAP"  are enabled, and require 128-bit MPPE/enable stateful MPPE are enabled. 

Failing that, test the new package here:
[http://craig.dubculture.co.nz/blog/2007/05/13/new-networkmanager-pptp-package-fixes-amd64-crashes/](http://craig.dubculture.co.nz/blog/2007/05/13/new-networkmanager-pptp-package-fixes-amd64-crashes/)

Contact me on that page with suggestions.

Craig

---

### Post by crb on 2007-05-20
Another suggestion - just enable 'refuse-eap', leaving refuse-chap and refuse-mschap unticked.

---

