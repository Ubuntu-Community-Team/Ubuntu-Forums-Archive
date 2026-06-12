---
title: "Absolute Complete Removal of PPTP settings/ configurations"
date: 2015-06-03
forum: Networking &amp; Wireless
---

### Post by maildtfam-ljx on 2015-06-03
Hello! May I seek your help to provide instructions on how to completely remove settings/ configurations for pptp when commands like [remove --purge network-manager-pptp] followed by [autoremove] still do not do the trick? Thank you!

Background info - I'm a user of Ubuntu since 2008, on my work PC as well as personal laptop PC. I have dualboot on both PCs, with Windows as the alternative OS but Ubuntu is the OS of choice for most  use. I recently encountered a sudden loss of pptp vpn on the work PC that was running 12.04 LTS. Access to pptp works fine when booting into Windows. Decided to verify if 14.04 LTS would work if I'd upgraded so used a Live CD for 14.04 LTS and it did work on the Live CD. However, after the upgrade to 14.04LTS, pptp is still not working. I'm now convinced a fresh install is perhaps the simplest way to get pptp working again but all efforts have been in vain so far. Removal, re-installations and looking up solutions offered for pptp issues have not be successful.

Steps taken so far for complete removal of pptp

^ sudo apt-get remove --purge network-manager-pptp
^ sudo apt-get autoremove

However, after a reboot, a search for "pptp" related files in the system still yielded many files which are locked and not possible to delete manually, as follows


[ATTACH=CONFIG]262382[/ATTACH]


I've also included a section from the Syslog as additional information :

> Jun  3 12:57:29 R66 NetworkManager[886]: <info> Starting VPN service 'pptp'...
Jun  3 12:57:29 R66 NetworkManager[886]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 2581
Jun  3 12:57:29 R66 NetworkManager[886]: <info> VPN service 'pptp' appeared; activating connections
Jun  3 12:57:29 R66 NetworkManager[886]: <info> VPN plugin state changed: starting (3)
Jun  3 12:57:29 R66 NetworkManager[886]: <info> VPN connection 'Japan' (Connect) reply received.
Jun  3 12:57:29 R66 pppd[2585]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Jun  3 12:57:29 R66 pppd[2585]: pppd 2.4.5 started by root, uid 0
Jun  3 12:57:29 R66 pppd[2585]: Using interface ppp0
Jun  3 12:57:29 R66 pptp[2588]: nm-pptp-service-2581 log[main: pptp.c:314]: The synchronous pptp option is NOT activated
Jun  3 12:57:29 R66 pppd[2585]: Connect: ppp0 <--> /dev/pts/0
Jun  3 12:57:29 R66 NetworkManager[886]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun  3 12:57:29 R66 NetworkManager[886]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jun  3 12:57:29 R66 NetworkManager[886]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Jun  3 12:57:29 R66 pptp[2605]: nm-pptp-service-2581 log[ctrlp_rep:  pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jun  3 12:57:30 R66 pptp[2605]: nm-pptp-service-2581 log[ctrlp_disp:  pptp_ctrl.c:739]: Received Start Control Connection Reply
Jun  3 12:57:30 R66 pptp[2605]: nm-pptp-service-2581 log[ctrlp_disp:  pptp_ctrl.c:773]: Client connection established.
Jun  3 12:57:30 R66 pptp[2605]: nm-pptp-service-2581 log[ctrlp_rep:  pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jun  3 12:57:31 R66 pptp[2605]: nm-pptp-service-2581 log[ctrlp_disp:  pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jun  3 12:57:31 R66 pptp[2605]: nm-pptp-service-2581 log[ctrlp_disp:   pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 15744).
Jun  3 12:57:34 R66 kernel: [  312.499331] [UFW BLOCK] IN=eth0 OUT= MAC=b8:ac:6f:c2:0a:80:bc:f1:f2:6c:fb:48:08:00 SRC=43.224.32.2 DST=192.168.1.199 LEN=61 TOS=0x00 PREC=0x00 TTL=41 ID=45633 DF PROTO=47 
Jun  3 12:57:36 R66 kernel: [  315.174278] [UFW BLOCK] IN=eth0 OUT= MAC=b8:ac:6f:c2:0a:80:bc:f1:f2:6c:fb:48:08:00 SRC=43.224.32.2 DST=192.168.1.199 LEN=60 TOS=0x00 PREC=0x00 TTL=41 ID=45801 DF PROTO=47 
Jun  3 12:57:40 R66 kernel: [  318.481394] [UFW BLOCK] IN=eth0 OUT= MAC=b8:ac:6f:c2:0a:80:bc:f1:f2:6c:fb:48:08:00 SRC=43.224.32.2 DST=192.168.1.199 LEN=61 TOS=0x00 PREC=0x00 TTL=41 ID=45935 DF PROTO=47 
Jun  3 12:57:42 R66 kernel: [  321.164297] [UFW BLOCK] IN=eth0 OUT= MAC=b8:ac:6f:c2:0a:80:bc:f1:f2:6c:fb:48:08:00 SRC=43.224.32.2 DST=192.168.1.199 LEN=60 TOS=0x00 PREC=0x00 TTL=41 ID=46182 DF PROTO=47 
Jun  3 12:57:43 R66 kernel: [  321.485795] [UFW BLOCK] IN=eth0 OUT= MAC=b8:ac:6f:c2:0a:80:bc:f1:f2:6c:fb:48:08:00 SRC=43.224.32.2 DST=192.168.1.199 LEN=61 TOS=0x00 PREC=0x00 TTL=41 ID=46228 DF PROTO=47 
Jun  3 12:57:45 R66 kernel: [  324.134625] [UFW BLOCK] IN=eth0 OUT= MAC=b8:ac:6f:c2:0a:80:bc:f1:f2:6c:fb:48:08:00 SRC=43.224.32.2 DST=192.168.1.199 LEN=60 TOS=0x00 PREC=0x00 TTL=41 ID=46352 DF PROTO=47 
Jun  3 12:58:00 R66 pppd[2585]: LCP: timeout sending Config-Requests
Jun  3 12:58:00 R66 pppd[2585]: Connection terminated.
Jun  3 12:58:00 R66 NetworkManager[886]: <warn> VPN plugin failed: 1
Jun  3 12:58:00 R66 NetworkManager[886]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun  3 12:58:00 R66 pppd[2585]: Modem hangup
Jun  3 12:58:00 R66 pptp[2588]: nm-pptp-service-2581 warn[decaps_hdlc:  pptp_gre.c:204]: short read (-1): Input/output error
Jun  3 12:58:00 R66 pptp[2588]: nm-pptp-service-2581 warn[decaps_hdlc:   pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jun  3 12:58:00 R66 pptp[2605]: nm-pptp-service-2581 log[callmgr_main:   pptp_callmgr.c:234]: Closing connection (unhandled)
Jun  3 12:58:00 R66 pptp[2605]: nm-pptp-service-2581 log[ctrlp_rep:   pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jun  3 12:58:00 R66 pptp[2605]: nm-pptp-service-2581 log[call_callback:   pptp_callmgr.c:79]: Closing connection (call state)
Jun  3 12:58:00 R66 pppd[2585]: Exit.
Jun  3 12:58:00 R66 NetworkManager[886]: <warn> VPN plugin failed: 1
Jun  3 12:58:00 R66 NetworkManager[886]: <info> VPN plugin state changed: stopped (6)
Jun  3 12:58:00 R66 NetworkManager[886]: <info> VPN plugin state change reason: 0
Jun  3 12:58:00 R66 NetworkManager[886]: <info> Policy set 'Desk' (eth0) as default for IPv4 routing and DNS.
Jun  3 12:58:00 R66 NetworkManager[886]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Jun  3 12:58:05 R66 NetworkManager[886]: <info> VPN service 'pptp' disappeared


Thank you and please excuse the lack of experience in posting a support request in this forum. :)

Have a great day!

---

### Post by NoWayWin8 on 2015-06-03
Can't it be removed using the Network Manager? Click the Network Manager icon then "Edit Connections" and see if it's listed.

---

### Post by maildtfam-ljx on 2015-06-03
My apologies. I wasn't clear enough. I meant to remove pptp capabilities and all related settings/ configurations of pptp so that I can do a fresh install of pptp.

Yes, under Network Manager, I can remove all individual pptp Connections I've made but it does not remove pptp capabilities. I've actually tried removing pptp capabilities using the Synaptic Package Manager and the Terminal to no avail, well, not completely anyway.

I guess what I'm trying to say is my goal is really to just get pptp to work again, and unfortunately the method I can think of is a fresh install of pptp.

Thank you.

---

### Post by NoWayWin8 on 2015-06-03
I don't think you would need to reinstall something like pptp since it is built-in with Network Manager.

Your firewall is blocking the connections - why is that?
> 
Jun  3 12:57:34 R66 kernel: [  312.499331] [UFW BLOCK] IN=eth0 OUT=  MAC=b8:ac:6f:c2:0a:80:bc:f1:f2:6c:fb:48:08:00 SRC=43.224.32.2  DST=192.168.1.199 LEN=61 TOS=0x00 PREC=0x00 TTL=41 ID=45633 DF PROTO=47 
Jun  3 12:57:36 R66 kernel: [  315.174278] [UFW BLOCK] IN=eth0 OUT=  MAC=b8:ac:6f:c2:0a:80:bc:f1:f2:6c:fb:48:08:00 SRC=43.224.32.2  DST=192.168.1.199 LEN=60 TOS=0x00 PREC=0x00 TTL=41 ID=45801 DF PROTO=47 
Jun  3 12:57:40 R66 kernel: [  318.481394] [UFW BLOCK] IN=eth0 OUT=  MAC=b8:ac:6f:c2:0a:80:bc:f1:f2:6c:fb:48:08:00 SRC=43.224.32.2  DST=192.168.1.199 LEN=61 TOS=0x00 PREC=0x00 TTL=41 ID=45935 DF PROTO=47 
Jun  3 12:57:42 R66 kernel: [  321.164297] [UFW BLOCK] IN=eth0 OUT=  MAC=b8:ac:6f:c2:0a:80:bc:f1:f2:6c:fb:48:08:00 SRC=43.224.32.2  DST=192.168.1.199 LEN=60 TOS=0x00 PREC=0x00 TTL=41 ID=46182 DF PROTO=47 
Jun  3 12:57:43 R66 kernel: [  321.485795] [UFW BLOCK] IN=eth0 OUT=  MAC=b8:ac:6f:c2:0a:80:bc:f1:f2:6c:fb:48:08:00 SRC=43.224.32.2  DST=192.168.1.199 LEN=61 TOS=0x00 PREC=0x00 TTL=41 ID=46228 DF PROTO=47 
Jun  3 12:57:45 R66 kernel: [  324.134625] [UFW BLOCK] IN=eth0 OUT=  MAC=b8:ac:6f:c2:0a:80:bc:f1:f2:6c:fb:48:08:00 SRC=43.224.32.2  DST=192.168.1.199 LEN=60 TOS=0x00 PREC=0x00 TTL=41 ID=46352 DF PROTO=47


---

### Post by maildtfam-ljx on 2015-06-03
@NoWayWin8

Thank you, thank you!!!

I disabled the UFW and voila! The pptp works now. Now I need to research how to activate the UFW again and put in a rule to allow incoming traffic for pptp. :)

---

