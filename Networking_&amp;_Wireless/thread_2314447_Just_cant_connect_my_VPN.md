---
title: "Just cant connect my VPN"
date: 2016-02-21
forum: Networking &amp; Wireless
---

### Post by lennox2 on 2016-02-21
Here is my log....
Somebody help me.....help!

```
lennox@lennox-MacBookPro:~$ tail -f /var/log/syslog
Feb 21 20:04:19 lennox-MacBookPro NetworkManager[690]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
Feb 21 20:04:19 lennox-MacBookPro NetworkManager[690]: Modem hangup
Feb 21 20:04:19 lennox-MacBookPro NetworkManager[690]: ** Message: nm-pptp-ppp-plugin: (nm_exit_notify): cleaning up
Feb 21 20:04:19 lennox-MacBookPro NetworkManager[690]: ** (nm-pptp-service:2594): WARNING **: pppd exited with error code 16
Feb 21 20:04:19 lennox-MacBookPro NetworkManager[690]: <warn>  VPN plugin failed: connect-failed (1)
Feb 21 20:04:19 lennox-MacBookPro NetworkManager[690]: <warn>  VPN plugin failed: connect-failed (1)
Feb 21 20:04:19 lennox-MacBookPro NetworkManager[690]: <info>  VPN plugin state changed: stopped (6)
Feb 21 20:04:19 lennox-MacBookPro NetworkManager[690]: <info>  VPN plugin state change reason: unknown (0)
Feb 21 20:04:19 lennox-MacBookPro NetworkManager[690]: <warn>  error disconnecting VPN: Could not process the request because no VPN connection was active.
Feb 21 20:04:39 lennox-MacBookPro NetworkManager[690]: <info>  VPN service 'pptp' disappeared
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: <info>  Starting VPN service 'pptp'...
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: <info>  VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 2665
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: <info>  VPN service 'pptp' appeared; activating connections
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: <info>  VPN connection 'PPTP HK' (ConnectInteractive) reply received.
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: <info>  VPN plugin state changed: starting (3)
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: ** Message: pppd started with pid 2666
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: <info>  VPN connection 'PPTP HK' (Connect) reply received.
Feb 21 20:05:20 lennox-MacBookPro pppd[2666]: Plugin /usr/lib/pppd/2.4.6/nm-pptp-pppd-plugin.so loaded.
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: Plugin /usr/lib/pppd/2.4.6/nm-pptp-pppd-plugin.so loaded.
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: ** Message: nm-pptp-ppp-plugin: (plugin_init): initializing
Feb 21 20:05:20 lennox-MacBookPro pppd[2666]: pppd 2.4.6 started by root, uid 0
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
Feb 21 20:05:20 lennox-MacBookPro pppd[2666]: Using interface ppp0
Feb 21 20:05:20 lennox-MacBookPro pppd[2666]: Connect: ppp0 <--> /dev/pts/5
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: <info>  (ppp0): new Generic device (carrier: UNKNOWN, driver: 'unknown', ifindex: 7)
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: Using interface ppp0
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: Connect: ppp0 <--> /dev/pts/5
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
Feb 21 20:05:20 lennox-MacBookPro pptp[2671]: nm-pptp-service-2665 log[main:pptp.c:350]: The synchronous pptp option is NOT activated
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: <info>  devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb 21 20:05:20 lennox-MacBookPro NetworkManager[690]: <info>  device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Feb 21 20:05:21 lennox-MacBookPro pptp[2682]: nm-pptp-service-2665 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 1 'Start-Control-Connection-Request'
Feb 21 20:05:21 lennox-MacBookPro pptp[2682]: nm-pptp-service-2665 log[ctrlp_disp:pptp_ctrl.c:781]: Received Start Control Connection Reply
Feb 21 20:05:21 lennox-MacBookPro pptp[2682]: nm-pptp-service-2665 log[ctrlp_disp:pptp_ctrl.c:815]: Client connection established.
Feb 21 20:05:22 lennox-MacBookPro pptp[2682]: nm-pptp-service-2665 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 7 'Outgoing-Call-Request'
Feb 21 20:05:22 lennox-MacBookPro pptp[2682]: nm-pptp-service-2665 log[ctrlp_disp:pptp_ctrl.c:900]: Received Outgoing Call Reply.
Feb 21 20:05:22 lennox-MacBookPro pptp[2682]: nm-pptp-service-2665 log[ctrlp_disp:pptp_ctrl.c:939]: Outgoing call established (call ID 51100, peer's call ID 29234).
Feb 21 20:05:51 lennox-MacBookPro pppd[2666]: LCP: timeout sending Config-Requests
Feb 21 20:05:51 lennox-MacBookPro pppd[2666]: Connection terminated.
Feb 21 20:05:51 lennox-MacBookPro avahi-daemon[638]: Withdrawing workstation service for ppp0.
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: LCP: timeout sending Config-Requests
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 11 / phase 'disconnect'
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: Connection terminated.
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: <warn>  VPN plugin failed: connect-failed (1)
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: <info>  devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: <warn>  (ppp0): failed to disable userspace IPv6LL address handling
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
Feb 21 20:05:51 lennox-MacBookPro pppd[2666]: Modem hangup
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: Modem hangup
Feb 21 20:05:51 lennox-MacBookPro pptp[2671]: nm-pptp-service-2665 warn[decaps_hdlc:pptp_gre.c:220]: short read (-1): Input/output error
Feb 21 20:05:51 lennox-MacBookPro pptp[2671]: nm-pptp-service-2665 warn[decaps_hdlc:pptp_gre.c:232]: pppd may have shutdown, see pppd log
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: <warn>  VPN plugin failed: connect-failed (1)
Feb 21 20:05:51 lennox-MacBookPro pptp[2682]: nm-pptp-service-2665 log[callmgr_main:pptp_callmgr.c:245]: Closing connection (unhandled)
Feb 21 20:05:51 lennox-MacBookPro pptp[2682]: nm-pptp-service-2665 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 12 'Call-Clear-Request'
Feb 21 20:05:51 lennox-MacBookPro pptp[2682]: nm-pptp-service-2665 log[call_callback:pptp_callmgr.c:84]: Closing connection (call state)
Feb 21 20:05:51 lennox-MacBookPro pppd[2666]: Exit.
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: ** Message: nm-pptp-ppp-plugin: (nm_exit_notify): cleaning up
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: ** (nm-pptp-service:2665): WARNING **: pppd exited with error code 16
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: <warn>  VPN plugin failed: connect-failed (1)
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: <info>  VPN plugin state changed: stopped (6)
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: <info>  VPN plugin state change reason: unknown (0)
Feb 21 20:05:51 lennox-MacBookPro NetworkManager[690]: <warn>  error disconnecting VPN: Could not process the request because no VPN connection was active.
^[[BFeb 21 20:06:11 lennox-MacBookPro NetworkManager[690]: <info>  VPN service 'pptp' disappeared

```

---

