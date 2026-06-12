---
title: "VPN failing to connect Ubuntu 15.10"
date: 2015-12-09
forum: Networking &amp; Wireless
---

### Post by Amanajs on 2015-12-09
Hi guys,

I'm trying to connect my VPN in this Ubuntu's version, but it's failing all the time, and it works in the previous version of the SO.
It's returns this message: [B]the VPN connection failed because the VPN service returned invalid configuration 
[/B]Does anyone knows how to fix it?

> 
Dec  9 16:01:12 <info>  Starting VPN service 'pptp'...
Dec  9 16:01:12 <info>  VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 8898
Dec  9 16:01:12 <info>  VPN service 'pptp' appeared; activating connections
Dec  9 16:01:12 <info>  VPN connection 'test' (ConnectInteractive) reply received.
Dec  9 16:01:12 <info>  VPN plugin state changed: starting (3)
Dec  9 16:01:12 ** Message: pppd started with pid 8899
Dec  9 16:01:12 <info>  VPN connection 'test' (Connect) reply received.
Dec  9 16:01:12  Plugin /usr/lib/pppd/2.4.6/nm-pptp-pppd-plugin.so loaded.
Dec  9 16:01:12 Plugin /usr/lib/pppd/2.4.6/nm-pptp-pppd-plugin.so loaded.
Dec  9 16:01:12 ** Message: nm-pptp-ppp-plugin: (plugin_init): initializing
Dec  9 16:01:12  pppd 2.4.6 started by root, uid 0
Dec  9 16:01:12 ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
Dec  9 16:01:12  Using interface ppp0
Dec  9 16:01:12  Connect: ppp0 <--> /dev/pts/2
Dec  9 16:01:12 nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Dec  9 16:01:12 <info>  (ppp0): new Generic device (carrier: UNKNOWN, driver: 'unknown', ifindex: 21)
Dec  9 16:01:12  nm-pptp-service-8898 log[main:pptp.c:350]: The synchronous pptp option is NOT activated
Dec  9 16:01:12 Using interface ppp0
Dec  9 16:01:12 Connect: ppp0 <--> /dev/pts/2
Dec  9 16:01:12 ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
Dec  9 16:01:12 <info>  devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec  9 16:01:12 <info>  device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Dec  9 16:01:12  nm-pptp-service-8898 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 1 'Start-Control-Connection-Request'
Dec  9 16:01:12  nm-pptp-service-8898 log[ctrlp_disp:pptp_ctrl.c:781]: Received Start Control Connection Reply
Dec  9 16:01:12  nm-pptp-service-8898 log[ctrlp_disp:pptp_ctrl.c:815]: Client connection established.
Dec  9 16:01:13  nm-pptp-service-8898 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 7 'Outgoing-Call-Request'
Dec  9 16:01:13  nm-pptp-service-8898 log[ctrlp_disp:pptp_ctrl.c:900]: Received Outgoing Call Reply.
Dec  9 16:01:13  nm-pptp-service-8898 log[ctrlp_disp:pptp_ctrl.c:939]: Outgoing call established (call ID 29924, peer's call ID 10722).
Dec  9 16:01:13 ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 6 / phase 'authenticate'
Dec  9 16:01:13 ** Message: nm-pptp-ppp-plugin: (get_credentials): passwd-hook, requesting credentials...
Dec  9 16:01:13 ** Message: nm-pptp-ppp-plugin: (get_credentials): got credentials from NetworkManager-pptp
Dec  9 16:01:13  CHAP authentication succeeded
Dec  9 16:01:13 CHAP authentication succeeded
Dec  9 16:01:13 ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 8 / phase 'network'
Dec  9 16:01:13  MPPE 128-bit stateless compression enabled
Dec  9 16:01:13 MPPE 128-bit stateless compression enabled
Dec  9 16:01:13 ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 9 / phase 'running'
Dec  9 16:01:13 ** Message: nm-pptp-ppp-plugin: (nm_ip_up): ip-up event
Dec  9 16:01:13 ** Message: nm-pptp-ppp-plugin: (nm_ip_up): sending Ip4Config to NetworkManager-pptp...
Dec  9 16:01:13 <info>  (ppp0): device state change: unmanaged -> unavailable (reason 'connection-assumed') [10 20 41]
Dec  9 16:01:13 <info>  (ppp0): device state change: unavailable -> disconnected (reason 'connection-assumed') [20 30 41]
Dec  9 16:01:13 <info>  Device 'ppp0' has no connection; scheduling activate_check in 0 seconds.
Dec  9 16:01:13 <info>  (ppp0): Activation: starting connection 'ppp0' (0b31e69c-4abe-4702-bc40-426b9a60feba)
Dec  9 16:01:13 <info>  VPN connection 'test' (IP4 Config Get) reply received from old-style plugin.
Dec  9 16:01:13 <info>  Tunnel Device: ppp0
Dec  9 16:01:13 <info>    DNS Domain: '(none)'
Dec  9 16:01:13 <info>  No IPv6 configuration
Dec  9 16:01:13 <info>  VPN plugin state changed: started (4)
Dec  9 16:01:13 ** Message: PPTP service (IP Config Get) reply received.
Dec  9 16:01:13 <info>  (ppp0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec  9 16:01:13 <warn>  platform-linux: do-add-ip4-route: failure adding ip4-route '21: 10.10.0.0/16 1': Unspecific failure (1)
Dec  9 16:01:13 <warn>  VPN connection 'test' did not receive valid IP config information.
Dec  9 16:01:13 ** Message: Terminated ppp daemon with PID 8899.
Dec  9 16:01:13  Terminating on signal 15
Dec  9 16:01:13  Connect time 0.0 minutes.
Dec  9 16:01:13  Sent 0 bytes, received 0 bytes.
Dec  9 16:01:13 Terminating on signal 15
Dec  9 16:01:13 ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 10 / phase 'terminate'
Dec  9 16:01:13 ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 8 / phase 'network'
Dec  9 16:01:13 Connect time 0.0 minutes.
Dec  9 16:01:13 Sent 0 bytes, received 0 bytes.
Dec  9 16:01:13  MPPE disabled
Dec  9 16:01:13 MPPE disabled
Dec  9 16:01:13 ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 10 / phase 'terminate'
Dec  9 16:01:13 ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
Dec  9 16:01:13  Child process /usr/sbin/pptp --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-8898 (pid 8901) terminated with signal 15
Dec  9 16:01:13 ** Message: nm-pptp-ppp -plugin: (nm_phasechange): status 5 / phase 'establish'
Dec  9 16:01:13 Child process /usr/sbin/pptp --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-8898 (pid 8901) terminated with signal 15
Dec  9 16:01:13 <info>  (ppp0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec  9 16:01:13 <info>  (ppp0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec  9 16:01:13 <warn>  (ppp0): interface ppp0 not up for IP configuration
Dec  9 16:01:13 <info>  (ppp0): device state change: ip-config -> ip-check (reason 'ip-config-unavailable') [70 80 5]
Dec  9 16:01:13 <info>  (ppp0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Dec  9 16:01:13 <info>  (ppp0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Dec  9 16:01:13 <info>  (ppp0): Activation: successful, device activated.
Dec  9 16:01:13 [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Dec  9 16:01:13  Starting Network Manager Script Dispatcher Service...
Dec  9 16:01:13 ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 11 / phase 'disconnect'
Dec  9 16:01:13  Connection terminated.
Dec  9 16:01:13 Connection terminated.


> Dec  9 16:01:12  <info>  Starting VPN service 'pptp'...Dec  9 16:01:12  <info>  VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 8898
Dec  9 16:01:12  <info>  VPN service 'pptp' appeared; activating connections
Dec  9 16:01:12  <info>  VPN connection 'test' (ConnectInteractive) reply received.
Dec  9 16:01:12  <info>  VPN plugin state changed: starting (3)
Dec  9 16:01:12  <info>  VPN connection 'test' (Connect) reply received.
Dec  9 16:01:13  <info>  VPN connection 'test' (IP4 Config Get) reply received from old-style plugin.
Dec  9 16:01:13  <info>  VPN plugin state changed: started (4)
Dec  9 16:01:13  <warn>  VPN connection 'test' did not receive valid IP config information.
Dec  9 16:01:33  <info>  VPN service 'pptp' disappeared


---

### Post by Amanajs on 2015-12-11
It seems that it's fixed! I found a similar issue in another forum: [https://bbs.archlinux.org/viewtopic.php?id=186213](https://bbs.archlinux.org/viewtopic.php?id=186213)
Basically you create a file called** netfilter.conf **inside the directory **/**[COLOR=#333333][FONT=sans-serif]**etc/modules-load.d** and put these lines below in the file:
[/FONT][/COLOR]
> [COLOR=#333333][FONT=sans-serif]nf_nat_pptp[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]nf_conntrack_pptp[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]nf_conntrack_proto_gre[/FONT][/COLOR]

[COLOR=#333333][FONT=sans-serif]After this you need to reboot and it's fixed.

[/FONT][/COLOR]

---

