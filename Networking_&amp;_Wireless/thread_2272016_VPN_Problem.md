---
title: "VPN Problem"
date: 2015-04-03
forum: Networking &amp; Wireless
---

### Post by cetoka on 2015-04-03
I was connecting to VPN Reactor(PPTP) since last week without any problems.But now I can not connect.Ubuntu 14.04 LTS Unity(ALL UPDATED), only system  on dell optiplex 390   OS type  64 -bit              Processor &#304;ntel core i3-2120 CPU@3.30 GHZ x4      Graphics intel  sandybridge desktop  RAM 8GB                 
This is the  tail -f /var/log/syslog   :
```

 tail-f /var/log/syslogApr 2 18:42:00 ceylan-OptiPlex-390 NetworkManager[970]: <info>Starting VPN service 'pptp'...
Apr 2 18:42:00 ceylan-OptiPlex-390 NetworkManager[970]: <info> VPNservice 'pptp' started (org.freedesktop.NetworkManager.pptp), PID24785
Apr 2 18:42:00 ceylan-OptiPlex-390 NetworkManager[970]: <info> VPNservice 'pptp' appeared; activating connections
Apr 2 18:42:00 ceylan-OptiPlex-390 NetworkManager[970]: <info> VPNplugin state changed: starting (3)
Apr 2 18:42:00 ceylan-OptiPlex-390 NetworkManager[970]: <info> VPNconnection 'VPN Reactor' (Connect) reply received.
Apr 2 18:42:00 ceylan-OptiPlex-390 pppd[24789]: Plugin/usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Apr 2 18:42:00 ceylan-OptiPlex-390 pppd[24789]: pppd 2.4.5 started byroot, uid 0
Apr 2 18:42:00 ceylan-OptiPlex-390 pppd[24789]: Using interface ppp0
Apr 2 18:42:00 ceylan-OptiPlex-390 pppd[24789]: Connect: ppp0 <-->/dev/pts/9
Apr 2 18:42:00 ceylan-OptiPlex-390 pptp[24793]: nm-pptp-service-24785log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Apr 2 18:42:00 ceylan-OptiPlex-390 NetworkManager[970]:   SCPlugin-Ifupdown: devices added (path:/sys/devices/virtual/net/ppp0, iface: ppp0)
Apr 2 18:42:00 ceylan-OptiPlex-390 NetworkManager[970]:   SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0,iface: ppp0): no ifupdown configuration found.
Apr 2 18:42:00 ceylan-OptiPlex-390 NetworkManager[970]: <warn>/sys/devices/virtual/net/ppp0: couldn't determine device driver;ignoring...
Apr 2 18:42:00 ceylan-OptiPlex-390 pptp[24807]: nm-pptp-service-24785log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1'Start-Control-Connection-Request'
Apr 2 18:42:00 ceylan-OptiPlex-390 pptp[24807]: nm-pptp-service-24785log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control ConnectionReply
Apr 2 18:42:00 ceylan-OptiPlex-390 pptp[24807]: nm-pptp-service-24785log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Apr 2 18:42:01 ceylan-OptiPlex-390 pptp[24807]: nm-pptp-service-24785log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7'Outgoing-Call-Request'
Apr 2 18:42:01 ceylan-OptiPlex-390 pptp[24807]: nm-pptp-service-24785log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Apr 2 18:42:01 ceylan-OptiPlex-390 pptp[24807]: nm-pptp-service-24785log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID0, peer's call ID 4736).
Apr 2 18:42:16 ceylan-OptiPlex-390 kernel: [16830.871009] [UFW BLOCK]IN=eth0 OUT= MAC=d4:be:d9:e0:26:85:18:28:61:2b:ae:88:08:00SRC=50.7.49.82 DST=192.168.2.37 LEN=60 TOS=0x00 PREC=0x00 TTL=49ID=32077 DF PROTO=47 
Apr 2 18:42:16 ceylan-OptiPlex-390 kernel: [16831.058691] [UFW BLOCK]IN=eth0 OUT= MAC=d4:be:d9:e0:26:85:18:28:61:2b:ae:88:08:00SRC=50.7.49.82 DST=192.168.2.37 LEN=61 TOS=0x00 PREC=0x00 TTL=49ID=32078 DF PROTO=47 
Apr 2 18:42:19 ceylan-OptiPlex-390 kernel: [16833.878946] [UFW BLOCK]IN=eth0 OUT= MAC=d4:be:d9:e0:26:85:18:28:61:2b:ae:88:08:00SRC=50.7.49.82 DST=192.168.2.37 LEN=60 TOS=0x00 PREC=0x00 TTL=49ID=32079 DF PROTO=47 
Apr 2 18:42:19 ceylan-OptiPlex-390 kernel: [16834.058780] [UFW BLOCK]IN=eth0 OUT= MAC=d4:be:d9:e0:26:85:18:28:61:2b:ae:88:08:00SRC=50.7.49.82 DST=192.168.2.37 LEN=61 TOS=0x00 PREC=0x00 TTL=49ID=32080 DF PROTO=47 
Apr 2 18:42:22 ceylan-OptiPlex-390 kernel: [16837.058872] [UFW BLOCK]IN=eth0 OUT= MAC=d4:be:d9:e0:26:85:18:28:61:2b:ae:88:08:00SRC=50.7.49.82 DST=192.168.2.37 LEN=61 TOS=0x00 PREC=0x00 TTL=49ID=32082 DF PROTO=47 
Apr 2 18:42:25 ceylan-OptiPlex-390 kernel: [16839.888530] [UFW BLOCK]IN=eth0 OUT= MAC=d4:be:d9:e0:26:85:18:28:61:2b:ae:88:08:00SRC=50.7.49.82 DST=192.168.2.37 LEN=60 TOS=0x00 PREC=0x00 TTL=49ID=32083 DF PROTO=47 
Apr 2 18:42:25 ceylan-OptiPlex-390 kernel: [16840.058651] [UFW BLOCK]IN=eth0 OUT= MAC=d4:be:d9:e0:26:85:18:28:61:2b:ae:88:08:00SRC=50.7.49.82 DST=192.168.2.37 LEN=61 TOS=0x00 PREC=0x00 TTL=49ID=32084 DF PROTO=47 
Apr 2 18:42:28 ceylan-OptiPlex-390 kernel: [16842.886350] [UFW BLOCK]IN=eth0 OUT= MAC=d4:be:d9:e0:26:85:18:28:61:2b:ae:88:08:00SRC=50.7.49.82 DST=192.168.2.37 LEN=60 TOS=0x00 PREC=0x00 TTL=49ID=32085 DF PROTO=47 
Apr 2 18:42:28 ceylan-OptiPlex-390 kernel: [16843.058254] [UFW BLOCK]IN=eth0 OUT= MAC=d4:be:d9:e0:26:85:18:28:61:2b:ae:88:08:00SRC=50.7.49.82 DST=192.168.2.37 LEN=61 TOS=0x00 PREC=0x00 TTL=49ID=32086 DF PROTO=47 
Apr 2 18:42:31 ceylan-OptiPlex-390 pppd[24789]: LCP: timeout sendingConfig-Requests
Apr 2 18:42:31 ceylan-OptiPlex-390 pppd[24789]: Connection terminated.
Apr 2 18:42:31 ceylan-OptiPlex-390 NetworkManager[970]: <warn> VPNplugin failed: 1
Apr 2 18:42:31 ceylan-OptiPlex-390 NetworkManager[970]:   SCPlugin-Ifupdown: devices removed (path:/sys/devices/virtual/net/ppp0, iface: ppp0)
Apr 2 18:42:31 ceylan-OptiPlex-390 pptp[24793]: nm-pptp-service-24785warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Apr 2 18:42:31 ceylan-OptiPlex-390 pptp[24793]: nm-pptp-service-24785warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppdlog
Apr 2 18:42:31 ceylan-OptiPlex-390 pppd[24789]: Modem hangup
Apr 2 18:42:31 ceylan-OptiPlex-390 pptp[24807]: nm-pptp-service-24785log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Apr 2 18:42:31 ceylan-OptiPlex-390 pptp[24807]: nm-pptp-service-24785log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12'Call-Clear-Request'
Apr 2 18:42:31 ceylan-OptiPlex-390 pptp[24807]: nm-pptp-service-24785log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Apr 2 18:42:31 ceylan-OptiPlex-390 pppd[24789]: Exit.
Apr 2 18:42:31 ceylan-OptiPlex-390 NetworkManager[970]: <warn> VPNplugin failed: 1
Apr 2 18:42:31 ceylan-OptiPlex-390 NetworkManager[970]: <warn> VPNplugin failed: 1
Apr 2 18:42:31 ceylan-OptiPlex-390 NetworkManager[970]: <info> VPNplugin state changed: stopped (6)
Apr 2 18:42:31 ceylan-OptiPlex-390 NetworkManager[970]: <info> VPNplugin state change reason: 0
Apr 2 18:42:31 ceylan-OptiPlex-390 NetworkManager[970]: <info>Policy set 'Wired connection 1' (eth0) as default for IPv4 routingand DNS.
Apr 2 18:42:31 ceylan-OptiPlex-390 NetworkManager[970]: <warn>error disconnecting VPN: Could not process the request because no VPNconnection was active.
Apr 2 18:42:36 ceylan-OptiPlex-390 NetworkManager[970]: <info> VPNservice 'pptp' disappeared

```

---

### Post by cetoka on 2015-04-03
Ok I found the solution and it worked.I hope this helps others too.[COLOR=#333333][FONT=UbuntuRegular]I have to run in terminal: [/FONT][/COLOR]sudo modprobe nf_conntrack_pptp       In order not to run this command everytime:

[COLOR=#333333][FONT=UbuntuRegular]Open your terminal and type as[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]gedit /etc/rc.local[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Then add following line at ending[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]nohup sudo modprobe nf_conntrack_pptp[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Then save and close your file.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Restart your Ubuntu and check.[/FONT][/COLOR]

---

