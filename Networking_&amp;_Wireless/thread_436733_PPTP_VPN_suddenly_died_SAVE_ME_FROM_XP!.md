---
title: "PPTP VPN suddenly died: SAVE ME FROM XP!"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by TonyS on 2007-05-08
Hi everyone,

Man, I LIKE Feisty. SO much I was seriously considering nuking the XP partition once and for all. Even my PPTP VPN was quick to set up and worked beautifully...

But only for the first week! Then, for no reason I can figure, its started consistently failing. It goes through the routine as it should, but just doesn't sort out a connection and fails after about 5 seconds.

Argh! Now I'm dragged kicking and screaming back toward the deathly embrace of Evil Bill when I have to connect to the office - NNNNNOOOO!!!!

This from /var/log/syslog:-

====

May  8 20:50:12 my-laptop NetworkManager: <information> Will activate VPN connection 'My Company Name', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'my-login', vpn_data 'ppp-connection-type / pptp / pptp-remote / mycompany.com / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / no / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN Activation (My Company Name) Stage 1 of 4 (Connection Prepare) scheduled... 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN Activation (My Company Name) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 6879) 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN Activation (My Company Name) Stage 1 of 4 (Connection Prepare) complete. 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN Activation (My Company Name) Stage 2 of 4 (Connection Prepare Wait) scheduled... 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN Activation (My Company Name) Stage 2 of 4 (Connection Prepare Wait) waiting... 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN Activation (My Company Name) Stage 2 of 4 (Connection Prepare Wait) complete. 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN Activation (My Company Name) Stage 3 of 4 (Connect) scheduled... 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN Activation (My Company Name) Stage 3 of 4 (Connect) sending connect request. 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN Activation (My Company Name) Stage 3 of 4 (Connect) request sent, waiting for reply... 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN Activation (My Company Name) Stage 3 of 4 (Connect) reply received. 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN Activation (My Company Name) Stage 4 of 4 (IP Config Get) timeout scheduled... 

May  8 20:50:13 my-laptop NetworkManager: <information> VPN Activation (My Company Name) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 

May  8 20:50:13 my-laptop pppd[6880]: Plugin nm-pppd-plugin.so loaded.

May  8 20:50:13 my-laptop pppd[6880]: nm-pppd-plugin: plugin initialized.

May  8 20:50:13 my-laptop pppd[6883]: pppd 2.4.4 started by root, uid 0

May  8 20:50:13 my-laptop pptp[6885]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 

May  8 20:50:13 my-laptop pppd[6883]: using channel 2

May  8 20:50:13 my-laptop pppd[6883]: Using interface ppp0

May  8 20:50:13 my-laptop pppd[6883]: Connect: ppp0 <--> /dev/pts/0

May  8 20:50:13 my-laptop pptp[6890]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 

May  8 20:50:13 my-laptop pptp[6890]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply

May  8 20:50:13 my-laptop pptp[6890]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.

May  8 20:50:14 my-laptop pppd[6883]: nm-pppd-plugin: CHAP check hook.

May  8 20:50:14 my-laptop pppd[6883]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0xac20a79c> <pcomp> <accomp>]

May  8 20:50:14 my-laptop pptp[6890]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 

May  8 20:50:14 my-laptop pptp[6890]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.

May  8 20:50:14 my-laptop pptp[6890]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 9856). 

May  8 20:50:17 my-laptop pppd[6883]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0xac20a79c> <pcomp> <accomp>]

May  8 20:50:23 my-laptop last message repeated 2 times

May  8 20:50:24 my-laptop pppd[6883]: Terminating on signal 15

May  8 20:50:24 my-laptop pppd[6883]: sent [LCP TermReq id=0x2 "User request"]

May  8 20:50:24 my-laptop NetworkManager: <WARNING>  nm_vpn_service_process_signal (): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 

May  8 20:50:24 my-laptop NetworkManager: <information> VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 

May  8 20:50:24 my-laptop NetworkManager: <information> VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 

May  8 20:50:24 my-laptop NetworkManager: <WARNING>  nm_vpn_service_stop_connection (): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'My Company Name' because service was 6. 

May  8 20:50:24 my-laptop pptp[6890]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)

May  8 20:50:24 my-laptop pptp[6890]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 

May  8 20:50:24 my-laptop pptp[6890]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)

May  8 20:50:24 my-laptop pppd[6883]: Modem hangup

May  8 20:50:24 my-laptop pppd[6883]: Connection terminated.

May  8 20:50:24 my-laptop pppd[6883]: Child process /usr/sbin/pptp 60.234.236.212 --nolaunchpppd (pid 6884) terminated with signal 15

May  8 20:50:24 my-laptop pppd[6883]: Exit.


====

So, "Terminating on Signal 15". Oddly the solution doesn't seem to be hitting me between the eyes. Whats going on here? 

Cheers all... any assistence GREATLY appreciated.

Tony

---

### Post by kzip on 2007-05-10
I had the same problem. I installed firestarter then disabled the firewall service using that GUI and I could connect no problem then. 

I'm sure there's a more elegant solution - but that worked for me :)

---

### Post by kzip on 2007-05-10
Ah, it seems I fixed my initial connection problem - but now the tunnel seems to fail after about 30 seconds (though Network Manager still thinks it's connected)...  :(

---

### Post by TonyS on 2007-05-11
Gurus, is there a bug? Something broken in a Feisty post-release upgrade?

Please, this problem is a real show-stopper for anyone trying to use Feisty to communicate with a Windows corporate environment.

Cheers,

Tony

---

### Post by TonyS on 2007-05-11
Further to mt last, I note there have been quite a few similar PPTP breakages reported in the forums over in the last fortnight. This does look like a bug... anyone know if its been reported already?

Anyone got a stable workaround?

Cheers,

Tony

---

### Post by crb on 2007-05-13
You can try a new package I've just built, from a more recent SVN release:
[http://craig.dubculture.co.nz/blog/2007/05/13/new-networkmanager-pptp-package-fixes-amd64-crashes/](http://craig.dubculture.co.nz/blog/2007/05/13/new-networkmanager-pptp-package-fixes-amd64-crashes/)

Otherwise, my suggestion is your default route over PPTP is stopping keepalives getting to your regular modem, and your connection dies.  You could try only routing for the networks you need, in the "Routing" tab of the properties box.

Craig

---

### Post by crb on 2007-05-13
(By the way, I don't tend to read this forum, so please feel free to comment on the blog linked above.)

---

### Post by crb on 2007-05-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/87870](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/87870) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is the relevant bug.

You may also like to try going through the help at [http://pptpclient.sourceforge.net/howto-diagnosis.phtml](http://pptpclient.sourceforge.net/howto-diagnosis.phtml) - NetworkManager just calls the pptp client.  If you get anywhere, please post here.

You're specifically having LCP timeouts, which normally means PPTP and/or GRE are firewalled.  See [http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lcp_timeout](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lcp_timeout)

For reference, the options I use (that allow me to connect to a Windows 2003 VPN server) should be the default options in the new package - refuse-eap, refuse-chap, refuse-mschap

---

### Post by Millenniumman on 2007-05-20
I am having a similar problem, but the log is slightly different. This is it:

]: pppd 2.4.4 started by root, uid 0
May 20 13:26:53 Penguin pppd[11584]: Using interface ppp0
May 20 13:26:53 Penguin pppd[11584]: Connect: ppp0 <--> /dev/pts/1
May 20 13:26:53 Penguin pptp[11588]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
May 20 13:26:53 Penguin pptp[11590]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
May 20 13:26:53 Penguin pptp[11590]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
May 20 13:26:53 Penguin pptp[11590]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
May 20 13:26:54 Penguin pppd[11584]: nm-pppd-plugin: CHAP check hook.
May 20 13:26:54 Penguin pptp[11590]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
May 20 13:26:54 Penguin pptp[11590]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
May 20 13:26:54 Penguin pptp[11590]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 12516). 
May 20 13:27:04 Penguin pppd[11584]: Terminating on signal 15

Is there any workaround? I have tried everything posted above, though I don't really understand most of that stuff on the pptpclient sourceforge page.

---

### Post by crb on 2007-05-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/87870](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/87870) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				(I see everywhere you post, millenniumman.  once would have been enough :p)

Another suggestion - just enable 'refuse-eap', leaving refuse-chap and refuse-mschap unticked.

Otherwise, please tick debug in the interface and re-post the log on the bug.

---

### Post by Millenniumman on 2007-05-22
I have done that, and here is the log:
```
May 22 17:35:45 Hostname NetworkManager: <information>^IWill activate VPN connection 'TheConnection', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'username', vpn_data 'ppp-connection-type / pptp / pptp-remote / TheIP / usepeerdns / yes / encrypt-mppe / yes / encrypt-mppe-128 / no / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
May 22 17:35:45 Hostname NetworkManager: <information>^IVPN Activation (TheConnection) Stage 1 of 4 (Connection Prepare) scheduled... 
May 22 17:35:45 Hostname NetworkManager: <information>^IVPN Activation (TheConnection) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 5251) 
May 22 17:35:45 Hostname NetworkManager: <information>^IVPN Activation (TheConnection) Stage 1 of 4 (Connection Prepare) complete. 
May 22 17:35:45 Hostname NetworkManager: <information>^IVPN Activation (TheConnection) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
May 22 17:35:45 Hostname NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
May 22 17:35:46 Hostname NetworkManager: <information>^IVPN Activation (TheConnection) Stage 2 of 4 (Connection Prepare Wait) waiting... 
May 22 17:35:46 Hostname NetworkManager: <information>^IVPN Activation (TheConnection) Stage 2 of 4 (Connection Prepare Wait) complete. 
May 22 17:35:46 Hostname NetworkManager: <information>^IVPN Activation (TheConnection) Stage 3 of 4 (Connect) scheduled... 
May 22 17:35:46 Hostname NetworkManager: <information>^IVPN Activation (TheConnection) Stage 3 of 4 (Connect) sending connect request. 
May 22 17:35:46 Hostname NetworkManager: <information>^IVPN Activation (TheConnection) Stage 3 of 4 (Connect) request sent, waiting for reply... 
May 22 17:35:46 Hostname NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
May 22 17:35:46 Hostname NetworkManager: <information>^IVPN Activation (TheConnection) Stage 3 of 4 (Connect) reply received. 
May 22 17:35:46 Hostname NetworkManager: <information>^IVPN Activation (TheConnection) Stage 4 of 4 (IP Config Get) timeout scheduled... 
May 22 17:35:46 Hostname NetworkManager: <information>^IVPN Activation (TheConnection) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
May 22 17:35:46 Hostname pppd[5252]: Plugin nm-pppd-plugin.so loaded.
May 22 17:35:46 Hostname pppd[5252]: nm-pppd-plugin: plugin initialized.
May 22 17:35:46 Hostname kernel: [ 4722.245519] PPP generic driver version 2.4.2
May 22 17:35:46 Hostname pppd[5263]: pppd 2.4.4 started by root, uid 0
May 22 17:35:46 Hostname pppd[5263]: using channel 1
May 22 17:35:46 Hostname pppd[5263]: Using interface ppp0
May 22 17:35:46 Hostname pppd[5263]: Connect: ppp0 <--> /dev/pts/1
May 22 17:35:46 Hostname pptp[5267]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
May 22 17:35:46 Hostname pptp[5276]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
May 22 17:35:46 Hostname pptp[5276]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
May 22 17:35:46 Hostname pptp[5276]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
May 22 17:35:47 Hostname pppd[5263]: nm-pppd-plugin: CHAP check hook.
May 22 17:35:47 Hostname pppd[5263]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0xf2c04828> <pcomp> <accomp>]
May 22 17:35:47 Hostname pptp[5276]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
May 22 17:35:47 Hostname pptp[5276]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
May 22 17:35:47 Hostname pptp[5276]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 48192). 
May 22 17:35:50 Hostname pppd[5263]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0xf2c04828> <pcomp> <accomp>]
May 22 17:35:56 Hostname last message repeated 2 times
May 22 17:35:57 Hostname pppd[5263]: Terminating on signal 15
May 22 17:35:57 Hostname pppd[5263]: sent [LCP TermReq id=0x2 "User request"]
May 22 17:35:57 Hostname NetworkManager: <WARNING>^I nm_vpn_service_process_signal (): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
May 22 17:35:57 Hostname NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
May 22 17:35:57 Hostname NetworkManager: <information>^IVPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
May 22 17:35:57 Hostname NetworkManager: <WARNING>^I nm_vpn_service_stop_connection (): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'TheConnection' because service was 6. 
May 22 17:35:57 Hostname pptp[5276]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
May 22 17:35:57 Hostname pptp[5276]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
May 22 17:35:57 Hostname pptp[5276]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
May 22 17:35:57 Hostname pppd[5263]: Modem hangup
May 22 17:35:57 Hostname pppd[5263]: Connection terminated.
May 22 17:35:57 Hostname pppd[5263]: Child process /usr/sbin/pptp TheIP --nolaunchpppd (pid 5264) terminated with signal 15
May 22 17:35:57 Hostname pppd[5263]: Exit.
```

I'm trying to do the stuff on that diagnostic page, but I can't figure out how to monitor GRE packet transmission. I've read their stuff on watching the packets with tcpdump, and that is simple enough, but I cannot differentiate GRE packets, or tell where they are going from the tcpdump output. Am I missing something on their page?

---

