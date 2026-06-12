---
title: "Problem to connect to VPN-PPTP using Wired newtwork"
date: 2013-10-16
forum: Networking &amp; Wireless
---

### Post by Leandro_Rudolph_Araujo on 2013-10-16
Hi,


I'm trying to connect to VPN-PPTP and it does not work if I use my Eth0 - Wired network

Works fine if I connect using my WiFi adapter

The IP of the server was changed, not allowed to publish it.

Can someone tell me what should I look for?


eth0      Link encap:Ethernet  HWaddr 00:1d:60:fe:19:c9  
          inet addr:192.168.2.115  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fefe:19c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46407 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17561678 (17.5 MB)  TX bytes:9575578 (9.5 MB)
          Interrupt:19 




tail -f /var/log/syslog

Oct 16 16:59:23 desktop-Ubuntu NetworkManager[888]: <info> Starting VPN service 'pptp'...
Oct 16 16:59:23 desktop-Ubuntu NetworkManager[888]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 12576
Oct 16 16:59:23 desktop-Ubuntu NetworkManager[888]: <info> VPN service 'pptp' appeared; activating connections
Oct 16 16:59:23 desktop-Ubuntu NetworkManager[888]: <info> VPN plugin state changed: starting (3)
Oct 16 16:59:23 desktop-Ubuntu NetworkManager[888]: <info> VPN connection '91.85.209.214' (Connect) reply received.
Oct 16 16:59:23 desktop-Ubuntu pppd[12580]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Oct 16 16:59:23 desktop-Ubuntu pppd[12580]: pppd 2.4.5 started by root, uid 0
Oct 16 16:59:23 desktop-Ubuntu pppd[12580]: Using interface ppp0
Oct 16 16:59:23 desktop-Ubuntu NetworkManager[888]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct 16 16:59:23 desktop-Ubuntu NetworkManager[888]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Oct 16 16:59:23 desktop-Ubuntu NetworkManager[888]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Oct 16 16:59:23 desktop-Ubuntu pppd[12580]: Connect: ppp0 <--> /dev/pts/6
Oct 16 16:59:23 desktop-Ubuntu pptp[12583]: nm-pptp-service-12576 log[mainptp.c:314]: The synchronous pptp option is NOT activated
Oct 16 16:59:23 desktop-Ubuntu pptp[12592]: nm-pptp-service-12576 log[ctrlp_repptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Oct 16 16:59:23 desktop-Ubuntu pptp[12592]: nm-pptp-service-12576 log[ctrlp_dispptp_ctrl.c:739]: Received Start Control Connection Reply
Oct 16 16:59:23 desktop-Ubuntu pptp[12592]: nm-pptp-service-12576 log[ctrlp_dispptp_ctrl.c:773]: Client connection established.
Oct 16 16:59:24 desktop-Ubuntu pptp[12592]: nm-pptp-service-12576 log[ctrlp_repptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Oct 16 16:59:24 desktop-Ubuntu pptp[12592]: nm-pptp-service-12576 log[ctrlp_dispptp_ctrl.c:858]: Received Outgoing Call Reply.
Oct 16 16:59:24 desktop-Ubuntu pptp[12592]: nm-pptp-service-12576 log[ctrlp_dispptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 10010).
Oct 16 16:59:24 desktop-Ubuntu kernel: [29355.769103] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=55 TOS=0x00 PREC=0x00 TTL=121 ID=30175 DF PROTO=47 
Oct 16 16:59:24 desktop-Ubuntu kernel: [29355.782068] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=54 TOS=0x00 PREC=0x00 TTL=121 ID=30176 DF PROTO=47 
Oct 16 16:59:27 desktop-Ubuntu kernel: [29358.487916] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=51 TOS=0x00 PREC=0x00 TTL=121 ID=30181 DF PROTO=47 
Oct 16 16:59:27 desktop-Ubuntu kernel: [29358.736203] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=54 TOS=0x00 PREC=0x00 TTL=121 ID=30182 DF PROTO=47 
Oct 16 16:59:30 desktop-Ubuntu kernel: [29361.491236] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=51 TOS=0x00 PREC=0x00 TTL=121 ID=30185 DF PROTO=47 
Oct 16 16:59:30 desktop-Ubuntu kernel: [29361.736699] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=54 TOS=0x00 PREC=0x00 TTL=121 ID=30186 DF PROTO=47 
Oct 16 16:59:33 desktop-Ubuntu kernel: [29364.494073] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=51 TOS=0x00 PREC=0x00 TTL=121 ID=30189 DF PROTO=47 
Oct 16 16:59:33 desktop-Ubuntu kernel: [29364.739658] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=54 TOS=0x00 PREC=0x00 TTL=121 ID=30190 DF PROTO=47 
Oct 16 16:59:36 desktop-Ubuntu kernel: [29367.497519] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=51 TOS=0x00 PREC=0x00 TTL=121 ID=30191 DF PROTO=47 
Oct 16 16:59:36 desktop-Ubuntu kernel: [29367.742913] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=54 TOS=0x00 PREC=0x00 TTL=121 ID=30193 DF PROTO=47 
Oct 16 16:59:39 desktop-Ubuntu kernel: [29370.499992] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=51 TOS=0x00 PREC=0x00 TTL=121 ID=30197 DF PROTO=47 
Oct 16 16:59:39 desktop-Ubuntu kernel: [29370.746024] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=54 TOS=0x00 PREC=0x00 TTL=121 ID=30198 DF PROTO=47 
Oct 16 16:59:42 desktop-Ubuntu kernel: [29373.503703] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=51 TOS=0x00 PREC=0x00 TTL=121 ID=30199 DF PROTO=47 
Oct 16 16:59:42 desktop-Ubuntu kernel: [29373.748236] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=54 TOS=0x00 PREC=0x00 TTL=121 ID=30200 DF PROTO=47 
Oct 16 16:59:45 desktop-Ubuntu kernel: [29376.506628] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=51 TOS=0x00 PREC=0x00 TTL=121 ID=30202 DF PROTO=47 
Oct 16 16:59:45 desktop-Ubuntu kernel: [29376.751741] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=54 TOS=0x00 PREC=0x00 TTL=121 ID=30203 DF PROTO=47 
Oct 16 16:59:48 desktop-Ubuntu kernel: [29379.509074] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=51 TOS=0x00 PREC=0x00 TTL=121 ID=30206 DF PROTO=47 
Oct 16 16:59:48 desktop-Ubuntu kernel: [29379.751727] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=54 TOS=0x00 PREC=0x00 TTL=121 ID=30207 DF PROTO=47 
Oct 16 16:59:48 desktop-Ubuntu pptp[12592]: nm-pptp-service-12576 log[logechoptp_ctrl.c:677]: Echo Request received.
Oct 16 16:59:48 desktop-Ubuntu pptp[12592]: nm-pptp-service-12576 log[ctrlp_repptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply'
Oct 16 16:59:51 desktop-Ubuntu kernel: [29382.512058] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=51 TOS=0x00 PREC=0x00 TTL=121 ID=30212 DF PROTO=47 
Oct 16 16:59:51 desktop-Ubuntu kernel: [29382.751917] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=54 TOS=0x00 PREC=0x00 TTL=121 ID=30213 DF PROTO=47 
Oct 16 16:59:54 desktop-Ubuntu kernel: [29385.515242] Inbound IN=eth0 OUT= MAC=00:1d:60:fe:19:c9:64:70:02:5d:a5:a9:08:00 SRC=91.85.209.214 DST=192.168.2.115 LEN=51 TOS=0x00 PREC=0x00 TTL=121 ID=30215 DF PROTO=47 
Oct 16 16:59:54 desktop-Ubuntu pppd[12580]: LCP: timeout sending Config-Requests
Oct 16 16:59:54 desktop-Ubuntu pppd[12580]: Connection terminated.
Oct 16 16:59:54 desktop-Ubuntu avahi-daemon[822]: Withdrawing workstation service for ppp0.
Oct 16 16:59:54 desktop-Ubuntu NetworkManager[888]: <warn> VPN plugin failed: 1
Oct 16 16:59:54 desktop-Ubuntu NetworkManager[888]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct 16 16:59:54 desktop-Ubuntu pptp[12583]: nm-pptp-service-12576 warn[decaps_hdlcptp_gre.c:204]: short read (-1): Input/output error
Oct 16 16:59:54 desktop-Ubuntu pptp[12583]: nm-pptp-service-12576 warn[decaps_hdlcptp_gre.c:216]: pppd may have shutdown, see pppd log
Oct 16 16:59:54 desktop-Ubuntu pppd[12580]: Modem hangup
Oct 16 16:59:54 desktop-Ubuntu pptp[12592]: nm-pptp-service-12576 log[callmgr_mainptp_callmgr.c:234]: Closing connection (unhandled)
Oct 16 16:59:54 desktop-Ubuntu pptp[12592]: nm-pptp-service-12576 log[ctrlp_repptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Oct 16 16:59:54 desktop-Ubuntu pptp[12592]: nm-pptp-service-12576 log[call_callbackptp_callmgr.c:79]: Closing connection (call state)
Oct 16 16:59:54 desktop-Ubuntu NetworkManager[888]: <warn> VPN plugin failed: 1
Oct 16 16:59:54 desktop-Ubuntu pppd[12580]: Exit.
Oct 16 16:59:54 desktop-Ubuntu NetworkManager[888]: <warn> VPN plugin failed: 1
Oct 16 16:59:54 desktop-Ubuntu NetworkManager[888]: <info> VPN plugin state changed: stopped (6)
Oct 16 16:59:54 desktop-Ubuntu NetworkManager[888]: <info> VPN plugin state change reason: 0
Oct 16 16:59:54 desktop-Ubuntu NetworkManager[888]: <info> Policy set 'Ethernet connection 1' (eth0) as default for IPv4 routing and DNS.
Oct 16 16:59:54 desktop-Ubuntu NetworkManager[888]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Oct 16 16:59:59 desktop-Ubuntu NetworkManager[888]: <info> VPN service 'pptp' disappeared

---

### Post by Leandro_Rudolph_Araujo on 2013-10-31
Upgrade to Ubuntu 3.10 today, now the I'm able to connect to VPN using my wired network.

Oct 31 14:08:36  whoopsie[1146]: last message repeated 4 times
Oct 31 14:08:36 desktop-Ubuntu NetworkManager[768]: <info> Starting VPN service 'pptp'...
Oct 31 14:08:36 desktop-Ubuntu NetworkManager[768]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 8056
Oct 31 14:08:36 desktop-Ubuntu NetworkManager[768]: <info> VPN service 'pptp' appeared; activating connections
Oct 31 14:08:36 desktop-Ubuntu NetworkManager[768]: <info> VPN plugin state changed: starting (3)
Oct 31 14:08:36 desktop-Ubuntu NetworkManager[768]: <info> VPN connection '91.85.209.214' (Connect) reply received.
Oct 31 14:08:36 desktop-Ubuntu pppd[8060]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Oct 31 14:08:36 desktop-Ubuntu pppd[8060]: pppd 2.4.5 started by root, uid 0
Oct 31 14:08:36 desktop-Ubuntu pppd[8060]: Using interface ppp0
Oct 31 14:08:36 desktop-Ubuntu pppd[8060]: Connect: ppp0 <--> /dev/pts/2
Oct 31 14:08:36 desktop-Ubuntu NetworkManager[768]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct 31 14:08:36 desktop-Ubuntu pptp[8063]: nm-pptp-service-8056 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Oct 31 14:08:36 desktop-Ubuntu NetworkManager[768]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Oct 31 14:08:36 desktop-Ubuntu NetworkManager[768]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Oct 31 14:08:36 desktop-Ubuntu whoopsie[1146]: online
Oct 31 14:08:36 desktop-Ubuntu pptp[8077]: nm-pptp-service-8056 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Oct 31 14:08:36 desktop-Ubuntu pptp[8077]: nm-pptp-service-8056 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Oct 31 14:08:36 desktop-Ubuntu pptp[8077]: nm-pptp-service-8056 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Oct 31 14:08:37 desktop-Ubuntu whoopsie[1146]: online
Oct 31 14:08:37 desktop-Ubuntu pptp[8077]: nm-pptp-service-8056 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Oct 31 14:08:41 desktop-Ubuntu pptp[8077]: nm-pptp-service-8056 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Oct 31 14:08:41 desktop-Ubuntu pptp[8077]: nm-pptp-service-8056 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 10010).
Oct 31 14:08:43 desktop-Ubuntu pppd[8060]: CHAP authentication succeeded
Oct 31 14:08:43 desktop-Ubuntu pppd[8060]: local  IP address 192.168.1.11
Oct 31 14:08:43 desktop-Ubuntu pppd[8060]: remote IP address 192.168.1.1
Oct 31 14:08:43 desktop-Ubuntu pppd[8060]: primary   DNS address 8.8.8.8
Oct 31 14:08:43 desktop-Ubuntu pppd[8060]: secondary DNS address 8.8.4.4
Oct 31 14:08:43 desktop-Ubuntu NetworkManager[768]: <info> VPN connection '91.85.209.214' (IP4 Config Get) reply received from old-style plugin.
Oct 31 14:08:43 desktop-Ubuntu NetworkManager[768]: <info> VPN Gateway: 91.85.209.214
Oct 31 14:08:43 desktop-Ubuntu NetworkManager[768]: <info> Tunnel Device: ppp0
Oct 31 14:08:43 desktop-Ubuntu NetworkManager[768]: <info> IPv4 configuration:
Oct 31 14:08:43 desktop-Ubuntu NetworkManager[768]: <info>   Internal Address: 192.168.1.11
Oct 31 14:08:43 desktop-Ubuntu NetworkManager[768]: <info>   Internal Prefix: 32
Oct 31 14:08:43 desktop-Ubuntu NetworkManager[768]: <info>   Internal Point-to-Point Address: 192.168.1.1
Oct 31 14:08:43 desktop-Ubuntu NetworkManager[768]: <info>   Maximum Segment Size (MSS): 0
Oct 31 14:08:43 desktop-Ubuntu NetworkManager[768]: <info>   Forbid Default Route: no
Oct 31 14:08:43 desktop-Ubuntu NetworkManager[768]: <info>   Internal DNS: 8.8.8.8
Oct 31 14:08:43 desktop-Ubuntu NetworkManager[768]: <info>   Internal DNS: 8.8.4.4
Oct 31 14:08:43 desktop-Ubuntu NetworkManager[768]: <info>   DNS Domain: '(none)'
Oct 31 14:08:43 desktop-Ubuntu NetworkManager[768]: <info> No IPv6 configuration
Oct 31 14:08:43 desktop-Ubuntu whoopsie[1146]: online
Oct 31 14:08:43 desktop-Ubuntu whoopsie[1146]: online
Oct 31 14:08:44 desktop-Ubuntu NetworkManager[768]: <info> VPN connection '91.85.209.214' (IP Config Get) complete.
Oct 31 14:08:44 desktop-Ubuntu NetworkManager[768]: <info> Policy set '91.85.209.214' (ppp0) as default for IPv4 routing and DNS.
Oct 31 14:08:44 desktop-Ubuntu NetworkManager[768]: <info> Writing DNS information to /sbin/resolvconf
Oct 31 14:08:44 desktop-Ubuntu dnsmasq[799]: setting upstream servers from DBus
Oct 31 14:08:44 desktop-Ubuntu dnsmasq[799]: using nameserver 8.8.4.4#53
Oct 31 14:08:44 desktop-Ubuntu dnsmasq[799]: using nameserver 8.8.8.8#53
Oct 31 14:08:44 desktop-Ubuntu NetworkManager[768]: <info> VPN plugin state changed: started (4)
Oct 31 14:08:44 desktop-Ubuntu dbus[668]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct 31 14:08:44 desktop-Ubuntu dbus[668]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 31 14:08:45 desktop-Ubuntu whoopsie[1146]: online

---

