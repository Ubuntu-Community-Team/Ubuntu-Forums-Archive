---
title: "Relakks VPN"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by jrwr on 2008-07-30
After searching all day for a answer here is what i have 
My Ethernet is on eth0,
the VPN is configured the right way...
here is the log from the syslog

```

Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  Will activate VPN connection 'Main VPN', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'jrwr', vpn_data 'ppp-connection-type / pptp / pptp-remote / pptp.relakks.com / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / no / encrypt-mppe-stateful / no / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / no / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''.
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN Activation (Main VPN) Stage 1 of 4 (Connection Prepare) scheduled...
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN Activation (Main VPN) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 5783)
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN Activation (Main VPN) Stage 1 of 4 (Connection Prepare) complete.
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN Activation (Main VPN) Stage 2 of 4 (Connection Prepare Wait) scheduled...
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6.
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN Activation (Main VPN) Stage 2 of 4 (Connection Prepare Wait) waiting...
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN Activation (Main VPN) Stage 2 of 4 (Connection Prepare Wait) complete.
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN Activation (Main VPN) Stage 3 of 4 (Connect) scheduled...
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN Activation (Main VPN) Stage 3 of 4 (Connect) sending connect request.
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN Activation (Main VPN) Stage 3 of 4 (Connect) request sent, waiting for reply...
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3.
Jul 30 11:17:27 jrwr-desktop pppd[5784]: Plugin nm-pppd-plugin.so loaded.
Jul 30 11:17:27 jrwr-desktop pppd[5784]: nm-pppd-plugin: plugin initialized.
Jul 30 11:17:27 jrwr-desktop pppd[5785]: pppd 2.4.4 started by root, uid 0
Jul 30 11:17:27 jrwr-desktop pptp[5788]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN Activation (Main VPN) Stage 3 of 4 (Connect) reply received.
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN Activation (Main VPN) Stage 4 of 4 (IP Config Get) timeout scheduled...
Jul 30 11:17:27 jrwr-desktop NetworkManager: <info>  VPN Activation (Main VPN) Stage 3 of 4 (Connect) complete, waiting for IP configuration...
Jul 30 11:17:27 jrwr-desktop pppd[5785]: using channel 5
Jul 30 11:17:27 jrwr-desktop pppd[5785]: Using interface ppp0
Jul 30 11:17:27 jrwr-desktop pppd[5785]: Connect: ppp0 <--> /dev/pts/0
Jul 30 11:17:28 jrwr-desktop pptp[5791]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jul 30 11:17:28 jrwr-desktop pppd[5785]: nm-pppd-plugin: CHAP check hook.
Jul 30 11:17:28 jrwr-desktop pppd[5785]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0xa98eb3b1> <pcomp> <accomp>]
Jul 30 11:17:37 jrwr-desktop last message repeated 3 times
Jul 30 11:17:38 jrwr-desktop pppd[5785]: Terminating on signal 15
Jul 30 11:17:38 jrwr-desktop pppd[5785]: sent [LCP TermReq id=0x2 "User request"]
Jul 30 11:17:38 jrwr-desktop NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'.
Jul 30 11:17:38 jrwr-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5.
Jul 30 11:17:38 jrwr-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6.
Jul 30 11:17:38 jrwr-desktop NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'Main VPN' because service was 6.
Jul 30 11:17:38 jrwr-desktop pppd[5785]: Child process /usr/sbin/pptp 83.233.182.2 --nolaunchpppd (pid 5787) terminated with signal 15
Jul 30 11:17:38 jrwr-desktop pppd[5785]: Modem hangup
Jul 30 11:17:38 jrwr-desktop pppd[5785]: Connection terminated.
Jul 30 11:17:38 jrwr-desktop pppd[5785]: Exit.


```

It just fails to connect, also ive tried to connect on the same router with windows, it works fine, i'm Using Hardy

---

### Post by jrwr on 2008-07-30
Eh, Anyone have any clues,

---

### Post by arno_de_Parno on 2008-07-31
Although I'm not familiar with Relakks VPN, I believe it's identical to a PPTP (windows) VPN. 
It helped me to add the domainname in the username field of the authorisationwindow. The domain I'm connecting to is called "DEOMBUDSMAN". 
So instead of only the username ("arno") I used "DEOMBUDSMAN\arno" as username

Did it for me!

My Config is:


```
Jul 31 16:24:58 ubuntuStudio NetworkManager: <info>  Will activate VPN connection 'ombudsman', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'arno', vpn_data 'ppp-connection-type / pptp / pptp-remote / ip.ad.dr.ess / usepeerdns / no / encrypt-mppe / no / encrypt-mppe-128 / yes / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / yes / compress-bsd / yes / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / no / ppp-refuse-chap / yes / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / no / routes / 172.16.0.0/16 / use-routes / yes', route '172.16.0.0/16'.
```

---

### Post by arno_de_Parno on 2008-08-08
I've been having these troubles over again. The description in my previous post isn't accurate. I'm sorry I've pointed you in the wrong direction.
Now for the good news (at least for me ;) ): The troubles I've had, had to do with my router/firewall. I've got an ubuntu server as router/firewall. This machine actually caused the problem. The (Windows) PPTP VPN I'm connecting to had troubles reaching me behind my router.

I did a nice google and came up with [Virtual Private Networking - the FireStarter way]("http://www.fs-security.com/docs/vpn.php"). 
The top solution on that page is the answer to my (and your?) problem and worked for me. 
The next lines are meant for the router/firewall, not for the VPN-client.
I've changed the variables for my network.
My **external** interface is **eth0**
My **internal** interface is **eth1**
Here's what I've come up with:
```
sudo iptables -A FORWARD -i eth1 -o eth0 -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -i eth1 -o eth0 -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -i eth0 -o eth1 -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
```

Now **this** did it really for me :P

Arno

---

