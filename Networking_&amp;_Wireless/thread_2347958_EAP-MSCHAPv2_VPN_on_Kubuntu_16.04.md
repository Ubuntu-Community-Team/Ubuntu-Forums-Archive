---
title: "EAP-MSCHAPv2 VPN on Kubuntu 16.04"
date: 2016-12-30
forum: Networking &amp; Wireless
---

### Post by Raiden616 on 2016-12-30
I know there are probably a million threads about this, but I've been through them all and find I'm no closer to solving this problem. Any help or advice would be very welcome!

My office use a windows-hosted VPN which I need to use on occasion when working from home, since various servers of ours are IP-locked, etc. I have been trying for months to get this working from my Kubuntu 16.04 installation and my failure is the only thing keeping my entire office from immediately adopting linux distributions as their primary operating system.

It all works fine from Windows machines. My company provides an exe for installing a Cisco VPN but I can also set up the VPN manually using the details they provide and it works fine. I'm not overly up on different VPN protocols and their requirements, but this suggests to me that there doesn't need to be any certificate or anything installed on the machine. The VPN is set up using EAP-MSCHAPv2.

Setting up a VPN with identical configuration results in no avail on my Kubuntu installation. As I say I am not totally up on VPN protocols, so I'm not sure exactly how I'm supposed to utilise the EAP-MSCHAPv2 protocol, but I have tried with both pptp and sstp connections. I have included the full logs from syslog at the bottom of this post, but they both produce the KDE error "the service providing the VPN was stopped". Checking syslog shows that it appears to resolve the hostname and perform the initial handshake correctly, but PPTP and SSTP produce slightly different errors. PPTP produces simply "Authentication fail", whilst SSTP produces the similar but hopefully more informative "E=649 No dialin permission".

Happy to provide any more information that is required. Please help!

Thanks!



Attempting to connect with PPTP produces this log:

```
[FONT=monospace][COLOR=#000000]Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097491.0188] audit: op="connection-activate" uuid="1317dc9b-23a5-4614-ae40-a0[/COLOR]
e0baa579b6" name=" PPTP" pid=1955 uid=1000 result="success"
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097491.0228] vpn-connection[0x1be4400,1317dc9b-23a5-4614-ae40-a0e0baa579b6,"E
fficio PPTP",0]: Started the VPN service, PID 4451
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097491.0339] vpn-connection[0x1be4400,1317dc9b-23a5-4614-ae40-a0e0baa579b6,"E
fficio PPTP",0]: Saw the service appear; activating connection
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: ** Message: pppd started with pid 4455
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097491.3148] vpn-connection[0x1be4400,1317dc9b-23a5-4614-ae40-a0e0baa579b6,"E
fficio PPTP",0]: VPN plugin: state changed: starting (3)
Dec 30 11:31:31 clark-ThinkPad-P50s pppd[4455]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-pptp-ppp-plugin: (plugin_init): initializing
Dec 30 11:31:31 clark-ThinkPad-P50s pppd[4455]: pppd 2.4.7 started by root, uid 0
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
Dec 30 11:31:31 clark-ThinkPad-P50s pppd[4455]: Using interface ppp0
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: Using interface ppp0
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: Connect: ppp0 <--> /dev/pts/3
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
Dec 30 11:31:31 clark-ThinkPad-P50s pppd[4455]: Connect: ppp0 <--> /dev/pts/3
Dec 30 11:31:31 clark-ThinkPad-P50s pptp[4459]: nm-pptp-service-4451 log[main:pptp.c:350]: The synchronous pptp option is NOT activated
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097491.3657] manager: (ppp0): new Generic device (/org/freedesktop/NetworkMan
ager/Devices/9)
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097491.3811] devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 30 11:31:31 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097491.3811] device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0):
 no ifupdown configuration found.
Dec 30 11:31:31 clark-ThinkPad-P50s pptp[4472]: nm-pptp-service-4451 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 1 'Start-Control-C
onnection-Request'
Dec 30 11:31:31 clark-ThinkPad-P50s pptp[4472]: nm-pptp-service-4451 log[ctrlp_disp:pptp_ctrl.c:781]: Received Start Control Connection Reply
Dec 30 11:31:31 clark-ThinkPad-P50s pptp[4472]: nm-pptp-service-4451 log[ctrlp_disp:pptp_ctrl.c:815]: Client connection established.
Dec 30 11:31:32 clark-ThinkPad-P50s pptp[4472]: nm-pptp-service-4451 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 7 'Outgoing-Call-R
equest'
Dec 30 11:31:33 clark-ThinkPad-P50s pptp[4472]: nm-pptp-service-4451 log[ctrlp_disp:pptp_ctrl.c:900]: Received Outgoing Call Reply.
Dec 30 11:31:33 clark-ThinkPad-P50s pptp[4472]: nm-pptp-service-4451 log[ctrlp_disp:pptp_ctrl.c:939]: Outgoing call established (call ID 64475, pee
r's call ID 22868).
Dec 30 11:31:33 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 6 / phase 'authenticate'
Dec 30 11:31:33 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-pptp-ppp-plugin: (get_credentials): passwd-hook, requesting credentials...
Dec 30 11:31:33 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-pptp-ppp-plugin: (get_credentials): got credentials from NetworkManager-ppt
p
Dec 30 11:31:33 clark-ThinkPad-P50s pppd[4455]: MS-CHAP authentication failed: Authentication Fail!
Dec 30 11:31:33 clark-ThinkPad-P50s NetworkManager[988]: MS-CHAP authentication failed: Authentication Fail!
Dec 30 11:31:33 clark-ThinkPad-P50s NetworkManager[988]: CHAP authentication failed
Dec 30 11:31:33 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 10 / phase 'terminate'
Dec 30 11:31:33 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
Dec 30 11:31:33 clark-ThinkPad-P50s pppd[4455]: CHAP authentication failed
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 11 / phase 'disconnect'
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: Connection terminated.
Dec 30 11:31:34 clark-ThinkPad-P50s pppd[4455]: Connection terminated.
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: ** Message: Terminated ppp daemon with PID 4455.
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: <error> [1483097494.1510] platform-linux: do-change-link[10]: failure changing link: failu
re 19 (No such device)
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: <warn>  [1483097494.1512] device (ppp0): failed to disable userspace IPv6LL address handli
ng
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: <warn>  [1483097494.1549] vpn-connection[0x1be4400,1317dc9b-23a5-4614-ae40-a0e0baa579b6,"E
fficio PPTP",0]: VPN plugin: failed: connect-failed (1)
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097494.1552] vpn-connection[0x1be4400,1317dc9b-23a5-4614-ae40-a0e0baa579b6,"E
fficio PPTP",0]: VPN plugin: state changed: stopping (5)
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097494.1558] vpn-connection[0x1be4400,1317dc9b-23a5-4614-ae40-a0e0baa579b6,"E
fficio PPTP",0]: VPN plugin: state changed: stopped (6)
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097494.1600] vpn-connection[0x1be4400,1317dc9b-23a5-4614-ae40-a0e0baa579b6,"E
fficio PPTP",0]: VPN plugin: state change reason: unknown (0)
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097494.1669] devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp
0)
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097494.1675] vpn-connection[0x1be4400,1317dc9b-23a5-4614-ae40-a0e0baa579b6,"E
fficio PPTP",0]: VPN service disappeared
Dec 30 11:31:34 clark-ThinkPad-P50s pptp[4472]: nm-pptp-service-4451 log[pptp_read_some:pptp_ctrl.c:586]: read returned zero, peer has closed
Dec 30 11:31:34 clark-ThinkPad-P50s pptp[4472]: nm-pptp-service-4451 log[callmgr_main:pptp_callmgr.c:269]: Closing connection (shutdown)
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: Terminating on signal 15
Dec 30 11:31:34 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-pptp-ppp-plugin: (nm_exit_notify): cleaning up
Dec 30 11:31:34 clark-ThinkPad-P50s pptp[4472]: nm-pptp-service-4451 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 12 'Call-Clear-Req
uest'
Dec 30 11:31:34 clark-ThinkPad-P50s pptp[4472]: nm-pptp-service-4451 log[pptp_read_some:pptp_ctrl.c:586]: read returned zero, peer has closed
Dec 30 11:31:34 clark-ThinkPad-P50s pptp[4472]: nm-pptp-service-4451 log[call_callback:pptp_callmgr.c:84]: Closing connection (call state)
Dec 30 11:31:34 clark-ThinkPad-P50s pppd[4455]: Terminating on signal 15
Dec 30 11:31:34 clark-ThinkPad-P50s pppd[4455]: Exit.
Dec 30 11:31:34 clark-ThinkPad-P50s org.kde.kdeconnect[1437]: "No such interface 'org.freedesktop.DBus.Properties' on object at path /org/freedeskt
op/NetworkManager/ActiveConnection/7"

[/FONT]
```

Attempting to connect with SSTP produces this log:

```
[FONT=monospace][COLOR=#000000]Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097531.1325] audit: op="connection-activate" uuid="4375a26e-22b7-4016-b5ce-08[/COLOR]
9cb4d0c808" name="Efficio SSTP" pid=1955 uid=1000 result="success"
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097531.1383] vpn-connection[0x1be4210,4375a26e-22b7-4016-b5ce-089cb4d0c808,"E
fficio SSTP",0]: Started the VPN service, PID 4488
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: ** Message: (nm-sstp-service org.freedesktop.NetworkManager.sstp.Connection_8
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097531.1474] vpn-connection[0x1be4210,4375a26e-22b7-4016-b5ce-089cb4d0c808,"E
fficio SSTP",0]: Saw the service appear; activating connection
Dec 30 11:32:11 clark-ThinkPad-P50s org.kde.kdeconnect[1437]: kdeconnect.core: Broadcasting identity packet
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: ** Message: pppd started with pid 4491
Dec 30 11:32:11 clark-ThinkPad-P50s pppd[4491]: Plugin /usr/lib/pppd/2.4.7/nm-sstp-pppd-plugin.so loaded.
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: Plugin /usr/lib/pppd/2.4.7/nm-sstp-pppd-plugin.so loaded.
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: (plugin_init): initializing
Dec 30 11:32:11 clark-ThinkPad-P50s pppd[4491]: pppd 2.4.7 started by root, uid 0
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
Dec 30 11:32:11 clark-ThinkPad-P50s pppd[4491]: Using interface ppp0
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097531.1833] vpn-connection[0x1be4210,4375a26e-22b7-4016-b5ce-089cb4d0c808,"E
fficio SSTP",0]: VPN plugin: state changed: starting (3)
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: Using interface ppp0
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: Connect: ppp0 <--> /dev/pts/3
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
Dec 30 11:32:11 clark-ThinkPad-P50s pppd[4491]: Connect: ppp0 <--> /dev/pts/3
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097531.1843] manager: (ppp0): new Generic device (/org/freedesktop/NetworkMan
ager/Devices/10)
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097531.1941] devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 30 11:32:11 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097531.1942] device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0):
 no ifupdown configuration found.
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: (nm_phasechange): status 6 / phase 'authenticate'
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: passwd-hook, need credentials...
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: (get_credentials): passwd-hook, requesting credentials...
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: (get_credentials): got credentials from NetworkManager-sst
p
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: (nm_snoop_send): sending mppe keys
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: (nm_sstp_notify): MPPE keys exchanged with sstpc
Dec 30 11:32:12 clark-ThinkPad-P50s pppd[4491]: MS-CHAP authentication failed: E=649 No dialin permission
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: MS-CHAP authentication failed: E=649 No dialin permission
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: CHAP authentication failed
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: (nm_phasechange): status 10 / phase 'terminate'
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
Dec 30 11:32:12 clark-ThinkPad-P50s pppd[4491]: CHAP authentication failed
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: (nm_phasechange): status 11 / phase 'disconnect'
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: Connection terminated.
Dec 30 11:32:12 clark-ThinkPad-P50s pppd[4491]: Connection terminated.
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: ** Message: Terminated ppp daemon with PID 4491.
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: <error> [1483097532.9501] platform-linux: do-change-link[11]: failure changing link: failu
re 19 (No such device)
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: <warn>  [1483097532.9501] device (ppp0): failed to disable userspace IPv6LL address handli
ng
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: <warn>  [1483097532.9509] vpn-connection[0x1be4210,4375a26e-22b7-4016-b5ce-089cb4d0c808,"E
fficio SSTP",0]: VPN plugin: failed: connect-failed (1)
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097532.9543] vpn-connection[0x1be4210,4375a26e-22b7-4016-b5ce-089cb4d0c808,"E
fficio SSTP",0]: VPN plugin: state changed: stopping (5)
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: Terminating on signal 15
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: ** Message: nm-sstp-ppp-plugin: (nm_exit_notify): cleaning up
Dec 30 11:32:12 clark-ThinkPad-P50s pppd[4491]: Terminating on signal 15
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097532.9626] vpn-connection[0x1be4210,4375a26e-22b7-4016-b5ce-089cb4d0c808,"E
fficio SSTP",0]: VPN service disappeared
Dec 30 11:32:12 clark-ThinkPad-P50s pppd[4491]: Exit.
Dec 30 11:32:12 clark-ThinkPad-P50s sstpc[4499]: PPPd terminated
Dec 30 11:32:12 clark-ThinkPad-P50s NetworkManager[988]: <info>  [1483097532.9715] devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp
0)
Dec 30 11:32:13 clark-ThinkPad-P50s org.kde.kdeconnect[1437]: "No such interface 'org.freedesktop.DBus.Properties' on object at path /org/freedeskt
op/NetworkManager/ActiveConnection/8"

[/FONT]
```

---

### Post by chester.mino on 2017-01-19
Hi Raiden, 

I am having quite similar issue. I am trying to setup SSTP VPN towards MS VPN server from Ubuntu 16.04. See below log.

19 09:14:28 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: ** Message: pppd started with pid 1257
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: <info>  [1484813668.6955] vpn-connection[0x1d873d0,d92b7c5e-4e0c-4b7e-b239-c4e2621d44c1,"Bratislava-office",0]: VPN plugin: state changed: starting (3)
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 pppd[1257]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: Plugin /usr/lib/pppd/2.4.7/nm-pptp-pppd-plugin.so loaded.
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: ** Message: nm-pptp-ppp-plugin: (plugin_init): initializing
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 pppd[1257]: pppd 2.4.7 started by root, uid 0
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 pppd[1257]: Using interface ppp1
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: Using interface ppp1
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 pppd[1257]: Connect: ppp1 <--> /dev/pts/20
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: Connect: ppp1 <--> /dev/pts/20
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: <info>  [1484813668.7099] manager: (ppp1): new Generic device (/org/freedesktop/NetworkManager/Devices/8)
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 pptp[1263]: nm-pptp-service-1141 log[main:pptp.c:350]: The synchronous pptp option is NOT activated
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 log[ctrlp_disp:pptp_ctrl.c:781]: Received Start Control Connection Reply
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 log[ctrlp_disp:pptp_ctrl.c:815]: Client connection established.
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: <info>  [1484813668.7499] devices added (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Jan 19 09:14:28 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: <info>  [1484813668.7500] device added (path: /sys/devices/virtual/net/ppp1, iface: ppp1): no ifupdown configuration found.
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 log[ctrlp_disp:pptp_ctrl.c:900]: Received Outgoing Call Reply.
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 log[ctrlp_disp:pptp_ctrl.c:939]: Outgoing call established (call ID 14243, peer's call ID 55718).
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 6 / phase 'authenticate'
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 log[ctrlp_disp:pptp_ctrl.c:1003]: PPTP_SET_LINK_INFO received from peer_callid 14243
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 log[ctrlp_disp:pptp_ctrl.c:1006]:   send_accm is 00000000, recv_accm is FFFFFFFF
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 warn[ctrlp_disp:pptp_ctrl.c:1009]: Non-zero Async Control Character Maps are not supported!
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 pppd[1257]: EAP: unknown authentication type 25; Naking
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: EAP: unknown authentication type 25; Naking
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 log[ctrlp_disp:pptp_ctrl.c:1003]: PPTP_SET_LINK_INFO received from peer_callid 14243
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 pppd[1257]: LCP terminated by peer (+^?mM-^F^@<M-Mt^@^@^C,)
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: LCP terminated by peer (+^?mM-^F^@<M-Mt^@^@^C,)
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 log[ctrlp_disp:pptp_ctrl.c:1006]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 warn[ctrlp_disp:pptp_ctrl.c:1009]: Non-zero Async Control Character Maps are not supported!
Jan 19 09:14:29 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 log[ctrlp_disp:pptp_ctrl.c:954]: Received Call Clear Request.
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 11 / phase 'disconnect'
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: Connection terminated.
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 pppd[1257]: Connection terminated.
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 charon[12153]: 13[KNL] interface ppp1 deleted
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: <error> [1484813672.8095] platform-linux: do-change-link[9]: failure changing link: failure 19 (No such device)
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: <warn>  [1484813672.8096] device (ppp1): failed to disable userspace IPv6LL address handling
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: ** Message: Terminated ppp daemon with PID 1257.
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: <info>  [1484813672.8134] vpn-connection[0x1d873d0,d92b7c5e-4e0c-4b7e-b239-c4e2621d44c1,"Bratislava-office",0]: VPN service disappeared
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: <info>  [1484813672.8171] devices removed (path: /sys/devices/virtual/net/ppp1, iface: ppp1)
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: ** Message: nm-pptp-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: Terminating on signal 15
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: Child process /usr/sbin/pptp 195.20.163.33 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-1141 (pid 1260) terminated with signal 15
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: Modem hangup
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 NetworkManager[984]: ** Message: nm-pptp-ppp-plugin: (nm_exit_notify): cleaning up
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 pptp[1263]: nm-pptp-service-1141 warn[decaps_hdlc:pptp_gre.c:220]: short read (-1): Input/output error
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 pptp[1263]: nm-pptp-service-1141 warn[decaps_hdlc:pptp_gre.c:232]: pppd may have shutdown, see pppd log
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 pppd[1257]: Terminating on signal 15
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 pppd[1257]: Child process /usr/sbin/pptp 195.20.163.33 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-1141 (pid 1260) terminated with signal 15
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 pppd[1257]: Modem hangup
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 log[callmgr_main:pptp_callmgr.c:245]: Closing connection (unhandled)
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 pptp[1286]: nm-pptp-service-1141 log[ctrlp_rep:pptp_ctrl.c:259]: Sent control packet type is 12 'Call-Clear-Request'
Jan 19 09:14:32 dominiq-HP-EliteBook-840-G1 pppd[1257]: Exit.

Did you managed to make it running ?

---

