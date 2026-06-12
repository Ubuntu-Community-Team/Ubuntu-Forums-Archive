---
title: "vpn fails after upgrade from ubuntu 15.04 to 15.10"
date: 2015-11-06
forum: Networking &amp; Wireless
---

### Post by EXPORTSAVVY on 2015-11-06
vpn fails after upgrade from ubuntu 15.04 to 15.10 
tried re-installing network manager and pptp client - no result
configuration of sstp fails too network-manager-sstp-gnome_0.9.4-0ubuntu1_i386.deb  and network-manager-sstp_0.9.4-0ubuntu1_i386.deb would not get installed error: no dependencies
SYS.LOG:
8 06:00:27 exportsavvy-m NetworkManager[914]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
Nov  8 06:00:27 exportsavvy-m NetworkManager[914]: Modem hangup
Nov  8 06:00:27 exportsavvy-m NetworkManager[914]: ** Message: nm-pptp-ppp-plugin: (nm_exit_notify): cleaning up
Nov  8 06:00:27 exportsavvy-m NetworkManager[914]: ** (nm-pptp-service:2452): WARNING **: pppd exited with error code 16
Nov  8 06:00:27 exportsavvy-m NetworkManager[914]: <info>  devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov  8 06:00:27 exportsavvy-m NetworkManager[914]: <warn>  VPN plugin failed: connect-failed (1)
Nov  8 06:00:27 exportsavvy-m NetworkManager[914]: message repeated 2 times: [ <warn>  VPN plugin failed: connect-failed (1)]
Nov  8 06:00:27 exportsavvy-m NetworkManager[914]: <info>  VPN plugin state changed: stopped (6)
Nov  8 06:00:27 exportsavvy-m NetworkManager[914]: <info>  VPN plugin state change reason: unknown (0)
Nov  8 06:00:27 exportsavvy-m NetworkManager[914]: <warn>  error disconnecting VPN: Could not process the request because no VPN connection was active.

---

