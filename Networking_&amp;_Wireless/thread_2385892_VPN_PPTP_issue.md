---
title: "VPN PPTP issue"
date: 2018-02-26
forum: Networking &amp; Wireless
---

### Post by chargecz on 2018-02-26
Hello i ran into issue possibly well known across distributions and  versions, so i tried possible solutions found before posting here.  basically i cant connect to VPN using network manager in ubuntu 16.04  getting errors described in log file below. I also bolded hints that its  going halw way torugh.
I tried to add netfilter.conf to */etc/modules-load.d* and reboot
with:

[I]nf_nat_pptp
nf_conntrack_pptp
nf_conntrack_proto_gre

[/I]I also tried some other less likely to help methods, installing 

*apt-get install pptpd pptp-linux*

tried manualy to load modules

[I]modprobe ppp_mppe
modprobe nf_conntrack_pptp nf_conntrack_proto_gre[/I]

and also disabling LCP checks in */etc/ppp/options*

Nothing helped, a lot of it were longshots, but i do not even know where  to begin with such a basic function malufanctioning, while finding its  rather not unusuall issue as well

My settings are simple IP as gateway, name and psw...i tried to enable/disable usage of MPPE in GUI as well.

```
úno 26 16:18:45 bernat NetworkManager[966]: <info>   [1519658325.6090] audit: op="connection-activate"  uuid="9d76cb9c-4c42-408a-8066-af179e4f1fc1" name="VPN connection 1"  pid=2025 uid=1000 result="success"
úno 26 16:18:45 bernat  NetworkManager[966]: <info>  [1519658325.6130]  vpn-connection[0x2a0f610,9d76cb9c-4c42-408a-8066-af179e4f1fc1,"VPN  connection 1",0]: Started the VPN service, PID 3458
úno 26 16:18:45  bernat NetworkManager[966]: <info>  [1519658325.6206]  vpn-connection[0x2a0f610,9d76cb9c-4c42-408a-8066-af179e4f1fc1,"VPN  connection 1",0]: Saw the service appear; activating connection
úno  26 16:18:45 bernat NetworkManager[966]: <info>  [1519658325.6928]  vpn-connection[0x2a0f610,9d76cb9c-4c42-408a-8066-af179e4f1fc1,"VPN  connection 1",0]: VPN connection: (ConnectInteractive) reply received
úno 26 16:18:45 bernat NetworkManager[966]: ** Message: pppd started with pid 3467
úno  26 16:18:45 bernat NetworkManager[966]: <info>  [1519658325.6977]  vpn-connection[0x2a0f610,9d76cb9c-4c42-408a-8066-af179e4f1fc1,"VPN  connection 1",0]: VPN plugin: state changed: starting (3)
úno 26 16:18:45 bernat pppd[3467]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
úno 26 16:18:45 bernat NetworkManager[966]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
úno 26 16:18:45 bernat NetworkManager[966]: ** Message: nm-pptp-ppp-plugin: (plugin_init): initializing
úno 26 16:18:45 bernat pppd[3467]: pppd 2.4.7 started by root, uid 0
úno  26 16:18:45 bernat NetworkManager[966]: ** Message: nm-pptp-ppp-plugin:  (nm_phasechange): status 3 / phase 'serial connection'
[COLOR=#ff0000]úno 26 16:18:45 bernat NetworkManager[966]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed[/COLOR]
úno  26 16:18:45 bernat NetworkManager[966]: <info>  [1519658325.7039]  manager: (ppp0): new Generic device  (/org/freedesktop/NetworkManager/Devices/7)
úno 26 16:18:45 bernat pppd[3467]: Using interface ppp0
úno 26 16:18:45 bernat NetworkManager[966]: Using interface ppp0
úno 26 16:18:45 bernat pppd[3467]: Connect: ppp0 <--> /dev/pts/0
úno 26 16:18:45 bernat NetworkManager[966]: Connect: ppp0 <--> /dev/pts/0
úno 26 16:18:45 bernat NetworkManager[966]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
úno 26 16:18:45 bernat pptp[3472]: nm-pptp-service-3458 log[main:pptp.c:350]: The synchronous pptp option is NOT activated
úno  26 16:18:45 bernat pptp[3487]: nm-pptp-service-3458  log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 1  'Start-Control-Connection-Request'
**úno 26 16:18:45 bernat pptp[3487]: nm-pptp-service-3458 log[ctrlp_disp:pptp_ctrl.c:781]: Received Start Control Connection Reply**
**úno 26 16:18:45 bernat pptp[3487]: nm-pptp-service-3458 log[ctrlp_disp:pptp_ctrl.c:815]: Client connection established.**
úno  26 16:18:45 bernat NetworkManager[966]: <info>  [1519658325.7164]  devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
úno  26 16:18:45 bernat NetworkManager[966]: <info>  [1519658325.7164]  device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no  ifupdown configuration found.
úno 26 16:18:46 bernat pptp[3487]:  nm-pptp-service-3458 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet  type is 7 'Outgoing-Call-Request'
**úno 26 16:18:46 bernat pptp[3487]: nm-pptp-service-3458 log[ctrlp_disp:pptp_ctrl.c:900]: Received Outgoing Call Reply.**
**úno  26 16:18:46 bernat pptp[3487]: nm-pptp-service-3458  log[ctrlp_disp:pptp_ctrl.c:939]: Outgoing call established (call ID  40419, peer's call ID 23680).**
[I]MODIFIED BY HAND
úno 26  16:19:07 bernat kernel: [UFW BLOCK] IN=enp0s31f6 OUT= MAC=50 SRC=212.  DST=10. LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=15460 DF PROTO=47 
úno 26 16:19:07 bernat kernel: [UFW BLOCK] IN=enp0s31f6 OUT= MAC=50  SRC=212. DST=10. LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=15460 DF PROTO=47
úno 26 16:19:07 bernat kernel: [UFW BLOCK] IN=enp0s31f6 OUT= MAC=50  SRC=212. DST=10. LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=15460 DF PROTO=47
úno 26 16:19:07 bernat kernel: [UFW BLOCK] IN=enp0s31f6 OUT= MAC=50  SRC=212. DST=10. LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=15460 DF PROTO=47
úno 26 16:19:07 bernat kernel: [UFW BLOCK] IN=enp0s31f6 OUT= MAC=50  SRC=212. DST=10. LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=15460 DF PROTO=47
úno 26 16:19:07 bernat kernel: [UFW BLOCK] IN=enp0s31f6 OUT= MAC=50  SRC=212. DST=10. LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=15460 DF PROTO=47
úno 26 16:19:07 bernat kernel: [UFW BLOCK] IN=enp0s31f6 OUT= MAC=50  SRC=212. DST=10. LEN=61 TOS=0x00 PREC=0x00 TTL=64 ID=15460 DF PROTO=47
MODIFIED BY HAND[/I]
úno 26 16:19:16 bernat pppd[3467]: LCP: timeout sending Config-Requests
úno 26 16:19:16 bernat NetworkManager[966]: LCP: timeout sending Config-Requests
úno 26 16:19:16 bernat NetworkManager[966]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 11 / phase 'disconnect'
úno 26 16:19:16 bernat NetworkManager[966]: Connection terminated.
úno 26 16:19:16 bernat pppd[3467]: Connection terminated.
úno 26 16:19:16 bernat NetworkManager[966]: ** Message: Terminated ppp daemon with PID 3467.
[COLOR=#ff0000]úno  26 16:19:16 bernat NetworkManager[966]: <error> [1519658356.7535]  platform-linux: do-change-link[8]: failure changing link: failure 19  (No such device)[/COLOR]
úno 26 16:19:16 bernat NetworkManager[966]:  <warn>  [1519658356.7545] device (ppp0): failed to disable  userspace IPv6LL address handling
úno 26 16:19:16 bernat pptp[3487]: nm-pptp-service-3458 log[pptp_read_some:pptp_ctrl.c:586]: read returned zero, peer has closed
úno 26 16:19:16 bernat pptp[3487]: nm-pptp-service-3458 log[callmgr_main:pptp_callmgr.c:269]: Closing connection (shutdown)
úno  26 16:19:16 bernat NetworkManager[966]: <info>  [1519658356.7556]  vpn-connection[0x2a0f610,9d76cb9c-4c42-408a-8066-af179e4f1fc1,"VPN  connection 1",0]: VPN service disappeared
úno 26 16:19:16 bernat  pptp[3487]: nm-pptp-service-3458 log[ctrlp_rep:pptp_ctrl.c:259]: Sent  control packet type is 12 'Call-Clear-Request'
úno 26 16:19:16 bernat pptp[3487]: nm-pptp-service-3458 log[pptp_read_some:pptp_ctrl.c:586]: read returned zero, peer has closed
úno 26 16:19:16 bernat pptp[3487]: nm-pptp-service-3458 log[call_callback:pptp_callmgr.c:84]: Closing connection (call state)
úno  26 16:19:16 bernat NetworkManager[966]: <info>  [1519658356.7643]  devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
úno 26 16:19:16 bernat NetworkManager[966]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
úno 26 16:19:16 bernat NetworkManager[966]: Terminating on signal 15
úno 26 16:19:16 bernat NetworkManager[966]: Modem hangup
úno 26 16:19:16 bernat NetworkManager[966]: ** Message: nm-pptp-ppp-plugin: (nm_exit_notify): cleaning up
úno 26 16:19:16 bernat pppd[3467]: Terminating on signal 15
úno 26 16:19:16 bernat pppd[3467]: Modem hangup
úno 26 16:19:16 bernat pppd[3467]: Exit.
```

---

### Post by chargecz on 2018-02-26
So..AS ALWAYS, after writing this post for some time and posting it after some heavy googling, i found solution in 5mins now

*ufw allow proto gre from IP-OF-GATEWAY*

and it works...well, the UFW block started bugging be after editing it, so there is this...hope it helps someone in the future

---

