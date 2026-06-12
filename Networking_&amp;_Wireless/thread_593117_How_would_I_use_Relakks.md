---
title: "How would I use Relakks?"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by bionnaki on 2007-10-26
[https://www.relakks.com](https://www.relakks.com)

A friend of mine would like to use this service for anonymous bittorrent useage. More info on how this would is here: [http://torrentfreak.com/how-relakksed-is-relakks](http://torrentfreak.com/how-relakksed-is-relakks)

So, how exactly would my friend use this service with ubuntu? Essentially it is a VPN service (but  is pay-as-you-go and keeps no logs). There is a tutorial for Windows and OSX, but not linux. Here's the XP one: [https://www.relakks.com/faq/guides/connectionxp](https://www.relakks.com/faq/guides/connectionxp) 

Thanks

---

### Post by PartisanEntity on 2007-10-31
Hi, I have been using Relakks since Feisty and it works quite nicely with Network Manager:
[http://www.cognitivecombine.com/?p=134](http://www.cognitivecombine.com/?p=134)

I am having some trouble connecting to Relakks in Gutsy using wireless mode, but it works perfectly in wired more.

---

### Post by yetihehe on 2008-01-21
I can't connect with wired connection too. syslog:
```
Jan 21 21:22:34 yetihehe-desktop NetworkManager: <info>  Will activate VPN connection 'relakks', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'yetihehe', vpn_data 'ppp-connection-type / pptp / pptp-remote / pptp.relakks.com / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / yes / encrypt-mppe-stateful / no / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Jan 21 21:22:34 yetihehe-desktop NetworkManager: <info>  VPN Activation (relakks) Stage 1 of 4 (Connection Prepare) scheduled... 
Jan 21 21:22:34 yetihehe-desktop NetworkManager: <info>  VPN Activation (relakks) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 6170) 
Jan 21 21:22:34 yetihehe-desktop NetworkManager: <info>  VPN Activation (relakks) Stage 1 of 4 (Connection Prepare) complete. 
Jan 21 21:22:34 yetihehe-desktop NetworkManager: <info>  VPN Activation (relakks) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Jan 21 21:22:34 yetihehe-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Jan 21 21:22:35 yetihehe-desktop NetworkManager: <info>  VPN Activation (relakks) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Jan 21 21:22:35 yetihehe-desktop NetworkManager: <info>  VPN Activation (relakks) Stage 2 of 4 (Connection Prepare Wait) complete. 
Jan 21 21:22:35 yetihehe-desktop NetworkManager: <info>  VPN Activation (relakks) Stage 3 of 4 (Connect) scheduled... 
Jan 21 21:22:35 yetihehe-desktop NetworkManager: <info>  VPN Activation (relakks) Stage 3 of 4 (Connect) sending connect request. 
Jan 21 21:22:35 yetihehe-desktop NetworkManager: <info>  VPN Activation (relakks) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Jan 21 21:22:35 yetihehe-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Jan 21 21:22:35 yetihehe-desktop NetworkManager: <info>  VPN Activation (relakks) Stage 3 of 4 (Connect) reply received. 
Jan 21 21:22:35 yetihehe-desktop NetworkManager: <info>  VPN Activation (relakks) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Jan 21 21:22:35 yetihehe-desktop NetworkManager: <info>  VPN Activation (relakks) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Jan 21 21:22:35 yetihehe-desktop pppd[6171]: Plugin nm-pppd-plugin.so loaded.
Jan 21 21:22:35 yetihehe-desktop pppd[6171]: nm-pppd-plugin: plugin initialized.
Jan 21 21:22:35 yetihehe-desktop kernel: [   97.567309] PPP generic driver version 2.4.2
Jan 21 21:22:35 yetihehe-desktop pppd[6182]: pppd 2.4.4 started by root, uid 0
Jan 21 21:22:35 yetihehe-desktop pptp[6184]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Jan 21 21:22:35 yetihehe-desktop pppd[6182]: Using interface ppp0
Jan 21 21:22:35 yetihehe-desktop pppd[6182]: Connect: ppp0 <--> /dev/pts/0
Jan 21 21:22:35 yetihehe-desktop pptp[6195]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Jan 21 21:22:36 yetihehe-desktop pppd[6182]: nm-pppd-plugin: CHAP check hook.
Jan 21 21:22:46 yetihehe-desktop NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Jan 21 21:22:46 yetihehe-desktop pppd[6182]: Terminating on signal 15
Jan 21 21:22:46 yetihehe-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Jan 21 21:22:46 yetihehe-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
Jan 21 21:22:46 yetihehe-desktop NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'relakks' because service was 6. 
Jan 21 21:22:46 yetihehe-desktop pppd[6182]: Child process /usr/sbin/pptp 83.233.183.2 --nolaunchpppd (pid 6183) terminated with signal 15
Jan 21 21:22:46 yetihehe-desktop pppd[6182]: Modem hangup
Jan 21 21:22:46 yetihehe-desktop pppd[6182]: Connection terminated.
Jan 21 21:22:46 yetihehe-desktop pppd[6182]: Exit.
```
Settings the same as in earlier link, ubuntu 7.10 amd64. What can be wrong?

---

### Post by PartisanEntity on 2008-01-21
Here is the solution:
[http://ubuntuforums.org/showthread.php?t=601671](http://ubuntuforums.org/showthread.php?t=601671)

---

### Post by yetihehe on 2008-01-21
Thanks, it worked now.

---

### Post by andy17 on 2008-01-24
What kind of modem do you use to connect with Relakks???

My D-Link 320T keeps losing the signal :-(((

---

