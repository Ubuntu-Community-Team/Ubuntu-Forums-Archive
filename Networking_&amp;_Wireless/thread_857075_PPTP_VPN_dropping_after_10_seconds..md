---
title: "PPTP VPN dropping after 10 seconds."
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by paperkut on 2008-07-12
I'm having some strange issues with my VPN, I'm able to connect but then the connection drops after 10 seconds. I'm using network-manager-pptp and the 'connected' image (the little lock) stays even though in /var/log/syslog it says that the connection was dropped.

Here's a paste from the VPN part of my syslog. I think the problem starts towards the end (with "short read (-1): Message too long")

```
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 1 of 4 (Connection Prepare) scheduled...
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 30450)
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 1 of 4 (Connection Prepare) complete.
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 2 of 4 (Connection Prepare Wait) scheduled...
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6.
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 2 of 4 (Connection Prepare Wait) waiting...
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 2 of 4 (Connection Prepare Wait) complete.
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 3 of 4 (Connect) scheduled...
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 3 of 4 (Connect) sending connect request.
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 3 of 4 (Connect) request sent, waiting for reply...
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3.
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 3 of 4 (Connect) reply received.
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 4 of 4 (IP Config Get) timeout scheduled...
Jul 12 10:57:10 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 3 of 4 (Connect) complete, waiting for IP configuration...
Jul 12 10:57:10 shakDB pppd[30459]: Plugin nm-pppd-plugin.so loaded.
Jul 12 10:57:10 shakDB pppd[30459]: nm-pppd-plugin: plugin initialized.
Jul 12 10:57:10 shakDB pppd[30459]: pppd options in effect:
Jul 12 10:57:10 shakDB pppd[30459]: debug^I^I# (from /etc/ppp/options)
Jul 12 10:57:10 shakDB pppd[30459]: dump^I^I# (from /etc/ppp/options)
Jul 12 10:57:10 shakDB pppd[30459]: plugin nm-pppd-plugin.so^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: noauth^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: refuse-chap^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: remotename shak.homeip.net^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: ^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: pty /usr/sbin/pptp 24.14.128.211 --nolaunchpppd^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: crtscts^I^I# (from /etc/ppp/options)
Jul 12 10:57:10 shakDB pppd[30459]: ^I^I# (from /etc/ppp/options)
Jul 12 10:57:10 shakDB pppd[30459]: asyncmap 0^I^I# (from /etc/ppp/options)
Jul 12 10:57:10 shakDB pppd[30459]: mru 1500^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: mtu 1500^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: lcp-echo-failure 10^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: lcp-echo-interval 10^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: hide-password^I^I# (from /etc/ppp/options)
Jul 12 10:57:10 shakDB pppd[30459]: ipparam NetworkManager^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: proxyarp^I^I# (from /etc/ppp/options)
Jul 12 10:57:10 shakDB pppd[30459]: usepeerdns^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: nobsdcomp^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: nodeflate^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: require-mppe-128^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: mppe-stateful^I^I# (from command line)
Jul 12 10:57:10 shakDB pppd[30459]: noipx^I^I# (from /etc/ppp/options)
Jul 12 10:57:10 shakDB pppd[30461]: pppd 2.4.4 started by root, uid 0
Jul 12 10:57:10 shakDB pppd[30461]: using channel 20
Jul 12 10:57:10 shakDB pppd[30461]: Using interface ppp0
Jul 12 10:57:10 shakDB pppd[30461]: Connect: ppp0 <--> /dev/pts/0
Jul 12 10:57:10 shakDB pptp[30464]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated
Jul 12 10:57:11 shakDB pptp[30466]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jul 12 10:57:11 shakDB pptp[30466]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Jul 12 10:57:11 shakDB pptp[30466]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Jul 12 10:57:11 shakDB pppd[30461]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Jul 12 10:57:11 shakDB pppd[30461]: nm-pppd-plugin: CHAP check hook.
Jul 12 10:57:11 shakDB pppd[30461]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xc292ab62> <pcomp> <accomp>]
Jul 12 10:57:12 shakDB pptp[30466]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jul 12 10:57:12 shakDB pptp[30466]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Jul 12 10:57:12 shakDB pptp[30466]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 5632).
Jul 12 10:57:12 shakDB pppd[30461]: rcvd [LCP ConfReq id=0x1 <mru 1450> <asyncmap 0x0> <auth chap MS-v2> <magic 0xc644c805> <pcomp> <accomp>]
Jul 12 10:57:12 shakDB pppd[30461]: sent [LCP ConfAck id=0x1 <mru 1450> <asyncmap 0x0> <auth chap MS-v2> <magic 0xc644c805> <pcomp> <accomp>]
Jul 12 10:57:12 shakDB pppd[30461]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xc292ab62> <pcomp> <accomp>]
Jul 12 10:57:12 shakDB pppd[30461]: sent [LCP EchoReq id=0x0 magic=0xc292ab62]
Jul 12 10:57:12 shakDB pppd[30461]: rcvd [LCP EchoReq id=0x0 magic=0xc644c805]
Jul 12 10:57:12 shakDB pppd[30461]: sent [LCP EchoRep id=0x0 magic=0xc292ab62]
Jul 12 10:57:12 shakDB pppd[30461]: rcvd [CHAP Challenge id=0x3a <e51c7f9ce260d7db72d7eeb2789d0e00>, name = "*"]
Jul 12 10:57:12 shakDB pppd[30461]: nm-pppd-plugin: CHAP credentials requested.
Jul 12 10:57:12 shakDB pppd[30461]: sent [CHAP Response id=0x3a <df12ab76d6e9895cbfdf3195a5288a9f0000000000000000a81370fb84e9824b52932a9f2501741baecea5e9bf2685e000>, name = "paperkut"]
Jul 12 10:57:12 shakDB pppd[30461]: rcvd [LCP EchoRep id=0x0 magic=0xc644c805]
Jul 12 10:57:13 shakDB pppd[30461]: rcvd [CHAP Success id=0x3a "S=52D598941D372FE442F6E7B891691646FC8EB0F6 M=Access granted"]
Jul 12 10:57:13 shakDB pppd[30461]: CHAP authentication succeeded
Jul 12 10:57:13 shakDB pppd[30461]: sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
Jul 12 10:57:13 shakDB pppd[30461]: rcvd [CCP ConfReq id=0x1 <mppe -H -M -S -L -D +C> <bsd v1 15>]
Jul 12 10:57:13 shakDB pppd[30461]: sent [CCP ConfRej id=0x1 <bsd v1 15>]
Jul 12 10:57:13 shakDB pppd[30461]: rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.1.1>]
Jul 12 10:57:13 shakDB pppd[30461]: sent [IPCP TermAck id=0x1]
Jul 12 10:57:13 shakDB pppd[30461]: rcvd [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
Jul 12 10:57:13 shakDB pppd[30461]: rcvd [CCP ConfReq id=0x2 <mppe -H -M -S -L -D +C>]
Jul 12 10:57:13 shakDB pppd[30461]: sent [CCP ConfNak id=0x2 <mppe +H -M +S -L -D -C>]
Jul 12 10:57:13 shakDB pppd[30461]: rcvd [CCP ConfReq id=0x3 <mppe +H -M +S -L -D -C>]
Jul 12 10:57:13 shakDB pppd[30461]: sent [CCP ConfAck id=0x3 <mppe +H -M +S -L -D -C>]
Jul 12 10:57:13 shakDB pppd[30461]: MPPE 128-bit stateless compression enabled
Jul 12 10:57:13 shakDB pppd[30461]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Jul 12 10:57:13 shakDB pppd[30461]: rcvd [IPCP ConfNak id=0x1 <addr 192.168.1.50> <ms-dns1 192.168.1.1> <ms-dns3 192.168.1.1>]
Jul 12 10:57:13 shakDB pppd[30461]: sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 192.168.1.50> <ms-dns1 192.168.1.1> <ms-dns3 192.168.1.1>]
Jul 12 10:57:14 shakDB pppd[30461]: rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 192.168.1.50> <ms-dns1 192.168.1.1> <ms-dns3 192.168.1.1>]
Jul 12 10:57:16 shakDB pppd[30461]: rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.1.1>]
Jul 12 10:57:16 shakDB pppd[30461]: sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 192.168.1.1>]
Jul 12 10:57:16 shakDB pppd[30461]: found interface wlan0 for proxy arp
Jul 12 10:57:16 shakDB pppd[30461]: local  IP address 192.168.1.50
Jul 12 10:57:16 shakDB pppd[30461]: remote IP address 192.168.1.1
Jul 12 10:57:16 shakDB pppd[30461]: primary   DNS address 192.168.1.1
Jul 12 10:57:16 shakDB pppd[30461]: secondary DNS address 192.168.1.1
Jul 12 10:57:16 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 4 of 4 (IP Config Get) reply received.
Jul 12 10:57:16 shakDB pppd[30461]: Script /etc/ppp/ip-up started (pid 30475)
Jul 12 10:57:16 shakDB pppd[30461]: Script /etc/ppp/ip-up finished (pid 30475), status = 0x0
Jul 12 10:57:17 shakDB NetworkManager: <info>  DHCP returned name servers but system has disabled dynamic modification!
Jul 12 10:57:17 shakDB NetworkManager: <info>  VPN Activation (Buffalo) Stage 4 of 4 (IP Config Get) complete.
Jul 12 10:57:17 shakDB NetworkManager: <info>  VPN Activation (Buffalo) successful.
Jul 12 10:57:17 shakDB NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 4.
Jul 12 10:57:20 shakDB pptp[30464]: anon warn[decaps_gre:pptp_gre.c:324]: short read (-1): Message too long
Jul 12 10:57:20 shakDB pptp[30466]: anon log[callmgr_main:pptp_callmgr.c:231]: Closing connection (unhandled)
Jul 12 10:57:20 shakDB pptp[30466]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jul 12 10:57:20 shakDB pptp[30466]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Jul 12 10:57:20 shakDB pppd[30461]: Script /usr/sbin/pptp 24.14.128.211 --nolaunchpppd finished (pid 30462), status = 0x0
Jul 12 10:57:20 shakDB pppd[30461]: Modem hangup
Jul 12 10:57:20 shakDB pppd[30461]: Connect time 0.1 minutes.
Jul 12 10:57:20 shakDB pppd[30461]: Sent 1412 bytes, received 0 bytes.
Jul 12 10:57:20 shakDB pppd[30461]: Script /etc/ppp/ip-down started (pid 30512)
Jul 12 10:57:20 shakDB pppd[30461]: MPPE disabled
Jul 12 10:57:20 shakDB pppd[30461]: sent [LCP TermReq id=0x2 "MPPE disabled"]
Jul 12 10:57:20 shakDB pppd[30461]: Connection terminated.
Jul 12 10:57:20 shakDB pppd[30461]: Waiting for 1 child processes...
Jul 12 10:57:20 shakDB pppd[30461]:   script /etc/ppp/ip-down, pid 30512
Jul 12 10:57:20 shakDB pppd[30461]: Script /etc/ppp/ip-down finished (pid 30512), status = 0x0
Jul 12 10:57:20 shakDB pppd[30461]: Exit.
```

I should note that it was working fine before.. problem just started happening for no reason.

Any help would be greatly appreciated.

---

### Post by paperkut on 2008-07-12
I figured it out folks, turns out my MTU setting on the card was a bit too high. Lowering it fixed the issue.

---

