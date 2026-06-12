---
title: "VPN connection access failed"
date: 2016-04-05
forum: Networking &amp; Wireless
---

### Post by carlos_sierra on 2016-04-05
I tried to configure a VPN access but it does not work. I tested the user and password of the VPN access under MAC OS and Windows and working fine.

I really appreciate it your help in order to solve it

```

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

```


```

/var/log/syslog

Apr  5 12:07:54 xubuntu NetworkManager[949]: <info> Starting VPN service 'pptp'...
Apr  5 12:07:54 xubuntu NetworkManager[949]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 3251
Apr  5 12:07:54 xubuntu NetworkManager[949]: <info> VPN service 'pptp' appeared; activating connections
Apr  5 12:07:54 xubuntu NetworkManager[949]: <info> VPN plugin state changed: init (1)
Apr  5 12:08:13 xubuntu NetworkManager[949]: <info> VPN plugin state changed: starting (3)
Apr  5 12:08:13 xubuntu NetworkManager[949]: <info> VPN connection 'CSC - Soledad' (Connect) reply received.
Apr  5 12:08:13 xubuntu pppd[3256]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Apr  5 12:08:13 xubuntu pppd[3256]: pppd 2.4.5 started by root, uid 0
Apr  5 12:08:13 xubuntu pppd[3256]: Using interface ppp0
Apr  5 12:08:13 xubuntu pppd[3256]: Connect: ppp0 <--> /dev/pts/1
Apr  5 12:08:13 xubuntu pptp[3259]: nm-pptp-service-3251 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Apr  5 12:08:13 xubuntu NetworkManager[949]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr  5 12:08:13 xubuntu NetworkManager[949]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Apr  5 12:08:14 xubuntu pptp[3267]: nm-pptp-service-3251 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Apr  5 12:08:14 xubuntu pptp[3267]: nm-pptp-service-3251 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Apr  5 12:08:14 xubuntu pptp[3267]: nm-pptp-service-3251 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Apr  5 12:08:15 xubuntu pptp[3267]: nm-pptp-service-3251 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Apr  5 12:08:15 xubuntu pptp[3267]: nm-pptp-service-3251 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Apr  5 12:08:15 xubuntu pptp[3267]: nm-pptp-service-3251 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 1668).
Apr  5 12:08:20 xubuntu pptp[3267]: nm-pptp-service-3251 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Apr  5 12:08:20 xubuntu pptp[3267]: nm-pptp-service-3251 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Apr  5 12:08:20 xubuntu pptp[3267]: nm-pptp-service-3251 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Apr  5 12:08:20 xubuntu pppd[3256]: Modem hangup
Apr  5 12:08:20 xubuntu pppd[3256]: Connection terminated.
Apr  5 12:08:20 xubuntu NetworkManager[949]: <warn> VPN plugin failed: 1
Apr  5 12:08:20 xubuntu NetworkManager[949]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr  5 12:08:20 xubuntu pptp[3267]: nm-pptp-service-3251 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Apr  5 12:08:20 xubuntu pptp[3267]: nm-pptp-service-3251 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Apr  5 12:08:20 xubuntu NetworkManager[949]: <warn> VPN plugin failed: 1
Apr  5 12:08:20 xubuntu pppd[3256]: Exit.
Apr  5 12:08:20 xubuntu NetworkManager[949]: <warn> VPN plugin failed: 1
Apr  5 12:08:20 xubuntu NetworkManager[949]: <info> VPN plugin state changed: stopped (6)
Apr  5 12:08:20 xubuntu NetworkManager[949]: <info> VPN plugin state change reason: 0
Apr  5 12:08:20 xubuntu NetworkManager[949]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Apr  5 12:08:20 xubuntu NetworkManager[949]: <info> Policy set 'Cableada automática' (eth0) as default for IPv4 routing and DNS.
Apr  5 12:08:25 xubuntu NetworkManager[949]: <info> VPN service 'pptp' disappeared
Apr  5 12:08:29 xubuntu dhclient: DHCPREQUEST of 192.168.62.200 on eth0 to 192.168.62.254 port 67
Apr  5 12:08:29 xubuntu dhclient: DHCPACK of 192.168.62.200 from 192.168.62.254
Apr  5 12:08:29 xubuntu dhclient: bound to 192.168.62.200 -- renewal in 838 seconds.

```

---

