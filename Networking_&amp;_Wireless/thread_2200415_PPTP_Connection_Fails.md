---
title: "PPTP Connection Fails"
date: 2014-01-19
forum: Networking &amp; Wireless
---

### Post by Toorel on 2014-01-19
Is there anyone who can help me out with my VPN connection. All my Windows Machines are connecting ok, but only my VPN connection is giving me the following in the syslog:

```

Jan 19 14:49:19 UBRRLPT NetworkManager[899]: <info> Starting VPN service 'pptp'...
Jan 19 14:49:19 UBRRLPT NetworkManager[899]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 4851
Jan 19 14:49:19 UBRRLPT NetworkManager[899]: <info> VPN service 'pptp' appeared; activating connections
Jan 19 14:49:19 UBRRLPT NetworkManager[899]: <info> VPN plugin state changed: starting (3)
Jan 19 14:49:19 UBRRLPT NetworkManager[899]: <info> VPN connection 'Home' (Connect) reply received.
Jan 19 14:49:19 UBRRLPT pppd[4855]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Jan 19 14:49:19 UBRRLPT pppd[4855]: pppd 2.4.5 started by root, uid 0
Jan 19 14:49:19 UBRRLPT pppd[4855]: Using interface ppp0
Jan 19 14:49:19 UBRRLPT pppd[4855]: Connect: ppp0 <--> /dev/pts/6
Jan 19 14:49:19 UBRRLPT pptp[4858]: nm-pptp-service-4851 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan 19 14:49:19 UBRRLPT NetworkManager[899]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 19 14:49:19 UBRRLPT NetworkManager[899]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan 19 14:49:19 UBRRLPT NetworkManager[899]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Jan 19 14:49:19 UBRRLPT pptp[4871]: nm-pptp-service-4851 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan 19 14:49:19 UBRRLPT pptp[4871]: nm-pptp-service-4851 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan 19 14:49:19 UBRRLPT pptp[4871]: nm-pptp-service-4851 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan 19 14:49:20 UBRRLPT pptp[4871]: nm-pptp-service-4851 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan 19 14:49:20 UBRRLPT pptp[4871]: nm-pptp-service-4851 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan 19 14:49:20 UBRRLPT pptp[4871]: nm-pptp-service-4851 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 1792).
Jan 19 14:49:23 UBRRLPT pppd[4855]: CHAP authentication succeeded
Jan 19 14:49:23 UBRRLPT pppd[4855]: LCP terminated by peer (MPPE required but peer negotiation failed)
Jan 19 14:49:23 UBRRLPT pptp[4871]: nm-pptp-service-4851 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Jan 19 14:49:23 UBRRLPT pptp[4871]: nm-pptp-service-4851 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Jan 19 14:49:23 UBRRLPT pptp[4871]: nm-pptp-service-4851 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jan 19 14:49:23 UBRRLPT pptp[4871]: nm-pptp-service-4851 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Jan 19 14:49:23 UBRRLPT pptp[4871]: nm-pptp-service-4851 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jan 19 14:49:23 UBRRLPT pppd[4855]: Modem hangup
Jan 19 14:49:23 UBRRLPT pppd[4855]: Connection terminated.
Jan 19 14:49:23 UBRRLPT avahi-daemon[846]: Withdrawing workstation service for ppp0.
Jan 19 14:49:23 UBRRLPT NetworkManager[899]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 19 14:49:23 UBRRLPT NetworkManager[899]: <warn> VPN plugin failed: 1
Jan 19 14:49:23 UBRRLPT pppd[4855]: Exit.
Jan 19 14:49:23 UBRRLPT NetworkManager[899]: <warn> VPN plugin failed: 1
Jan 19 14:49:23 UBRRLPT NetworkManager[899]: <warn> VPN plugin failed: 1
Jan 19 14:49:23 UBRRLPT NetworkManager[899]: <info> VPN plugin state changed: stopped (6)
Jan 19 14:49:23 UBRRLPT NetworkManager[899]: <info> VPN plugin state change reason: 0
Jan 19 14:49:23 UBRRLPT NetworkManager[899]: <info> Policy set 'SSIDNAME' (wlan0) as default for IPv4 routing and DNS.
Jan 19 14:49:23 UBRRLPT NetworkManager[899]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Jan 19 14:49:29 UBRRLPT NetworkManager[899]: <info> VPN service 'pptp' disappeared

```

Running Ubuntu 13.10
Laptop is a Samsung NP900X4D-A02NL with a [COLOR=#333333][FONT=arial]Intel Centrino Advanced-N 6235 network card

Please let me know when you need additional information[/FONT][/COLOR]

---

### Post by Toorel on 2014-01-19
I had to enable MPPE encryption under the advanced settings and now it is working

---

