---
title: "VPN PPTP Connection Fails with Network Manager"
date: 2015-01-10
forum: Networking &amp; Wireless
---

### Post by Sebastian_Robitzsch on 2015-01-10
Dear all,

I set up my own VPN server at home (PPTP) using Rasbian and was successful in getting the server, my Android phone and my iPad set up and running (so the server is set up correctly). However, when trying to establish a VPN PPTP connection with my Kubuntu 14.10-based laptop, the Network Manager (as well as KVPN) fails and produces the following trace:

```
Jan 10 19:07:30 latitude-6430u NetworkManager[1016]: <info> Starting VPN service 'pptp'...
Jan 10 19:07:30 latitude-6430u NetworkManager[1016]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 14103
Jan 10 19:07:30 latitude-6430u NetworkManager[1016]: <info> VPN service 'pptp' appeared; activating connections
Jan 10 19:07:30 latitude-6430u NetworkManager[1016]: <info> VPN plugin state changed: starting (3)
Jan 10 19:07:30 latitude-6430u pppd[14104]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Jan 10 19:07:30 latitude-6430u NetworkManager[1016]: <info> VPN connection 'myWay' (Connect) reply received.
Jan 10 19:07:30 latitude-6430u pppd[14104]: pppd 2.4.5 started by root, uid 0
Jan 10 19:07:30 latitude-6430u pppd[14104]: Using interface ppp0
Jan 10 19:07:30 latitude-6430u pppd[14104]: Connect: ppp0 <--> /dev/pts/13
Jan 10 19:07:30 latitude-6430u pptp[14107]: nm-pptp-service-14103 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan 10 19:07:30 latitude-6430u NetworkManager[1016]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 10 19:07:30 latitude-6430u NetworkManager[1016]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan 10 19:07:30 latitude-6430u NetworkManager[1016]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Jan 10 19:07:30 latitude-6430u pptp[14122]: nm-pptp-service-14103 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan 10 19:07:30 latitude-6430u pptp[14122]: nm-pptp-service-14103 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan 10 19:07:30 latitude-6430u pptp[14122]: nm-pptp-service-14103 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan 10 19:07:31 latitude-6430u pptp[14122]: nm-pptp-service-14103 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan 10 19:07:31 latitude-6430u pptp[14122]: nm-pptp-service-14103 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan 10 19:07:31 latitude-6430u pptp[14122]: nm-pptp-service-14103 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 0).
Jan 10 19:08:01 latitude-6430u pppd[14104]: LCP: timeout sending Config-Requests
Jan 10 19:08:01 latitude-6430u pppd[14104]: Connection terminated.
Jan 10 19:08:01 latitude-6430u NetworkManager[1016]: <warn> VPN plugin failed: 1
Jan 10 19:08:01 latitude-6430u NetworkManager[1016]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 10 19:08:01 latitude-6430u pptp[14107]: nm-pptp-service-14103 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Jan 10 19:08:01 latitude-6430u pptp[14107]: nm-pptp-service-14103 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jan 10 19:08:01 latitude-6430u pppd[14104]: Modem hangup
Jan 10 19:08:01 latitude-6430u pptp[14122]: nm-pptp-service-14103 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Jan 10 19:08:01 latitude-6430u pptp[14122]: nm-pptp-service-14103 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jan 10 19:08:01 latitude-6430u pptp[14122]: nm-pptp-service-14103 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jan 10 19:08:01 latitude-6430u pppd[14104]: Exit.
Jan 10 19:08:01 latitude-6430u NetworkManager[1016]: <warn> VPN plugin failed: 1
Jan 10 19:08:01 latitude-6430u NetworkManager[1016]: <warn> VPN plugin failed: 1
Jan 10 19:08:01 latitude-6430u NetworkManager[1016]: <info> VPN plugin state changed: stopped (6)
Jan 10 19:08:01 latitude-6430u NetworkManager[1016]: <info> VPN plugin state change reason: 0
Jan 10 19:08:01 latitude-6430u NetworkManager[1016]: <info> Policy set 'DCU (S334)' (em1) as default for IPv4 routing and DNS.
Jan 10 19:08:01 latitude-6430u NetworkManager[1016]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Jan 10 19:08:06 latitude-6430u NetworkManager[1016]: <info> VPN service 'pptp' disappeared

```

The corresponding log of the server:
```
Jan 10 19:07:32 myWay pptpd[3027]: CTRL: Client 136.206.37.185 control connection started
Jan 10 19:07:33 myWay pptpd[3027]: CTRL: Starting call (launching pppd, opening GRE)
Jan 10 19:07:33 myWay pppd[3028]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jan 10 19:07:33 myWay kernel: [  154.070934] PPP generic driver version 2.4.2
Jan 10 19:07:33 myWay pppd[3028]: pppd 2.4.5 started by root, uid 0
Jan 10 19:07:33 myWay pppd[3028]: Using interface ppp0
Jan 10 19:07:33 myWay pppd[3028]: Connect: ppp0 <--> /dev/pts/1
Jan 10 19:07:33 myWay pptpd[3027]: GRE: Bad checksum from pppd.
Jan 10 19:07:33 myWay ifplugd(ppp0)[3046]: ifplugd 0.28 initializing.
Jan 10 19:07:33 myWay ifplugd(ppp0)[3046]: Using interface ppp0/00:00:00:00:00:00
Jan 10 19:07:33 myWay ifplugd(ppp0)[3046]: Using detection mode: IFF_RUNNING
Jan 10 19:07:33 myWay ifplugd(ppp0)[3046]: Initialization complete, link beat detected.
Jan 10 19:07:33 myWay ifplugd(ppp0)[3046]: Executing '/etc/ifplugd/ifplugd.action ppp0 up'.
Jan 10 19:07:33 myWay ifplugd(ppp0)[3046]: client: Ignoring unknown interface ppp0=ppp0.
Jan 10 19:07:33 myWay ifplugd(ppp0)[3046]: Program executed successfully.
Jan 10 19:08:03 myWay pptpd[3027]: CTRL: Reaping child PPP[3028]
Jan 10 19:08:03 myWay pppd[3028]: Hangup (SIGHUP)
Jan 10 19:08:03 myWay pppd[3028]: Modem hangup
Jan 10 19:08:03 myWay pppd[3028]: Connection terminated.
Jan 10 19:08:03 myWay pppd[3028]: Exit.
Jan 10 19:08:03 myWay pptpd[3027]: CTRL: Client 136.206.37.185 control connection finished
Jan 10 19:08:03 myWay ifplugd(ppp0)[3046]: Link beat lost.
Jan 10 19:08:03 myWay ifplugd(ppp0)[3046]: Exiting.
```

I browsed the web for solutions and found [this thread]("http://ubuntuforums.org/showthread.php?t=1095546&highlight=LCP+terminated+peer+VPN+PPTP") talking about the "The synchronous pptp option is NOT activated" log which I have addressed by disabling EAP (refuse-EAP) in the client - only MSCHAP2 is allowed/ticked. And based on the traces above this is not the issue. If I'm no wrong the problem is where the client indicates that there's no configuration available for ppp0 that also appears on the server side in the "client: Ignoring unknown interface ppp0=ppp0." line. 

Any help is much appreciated :)
Cheers

---

### Post by TheFu on 2015-01-11
I cannot help other than to say that pptp is NOT a real VPN. It has been hacked, repeatedly, over the years. If you want a secure VPN, pptp is NOT it.

---

### Post by Sebastian_Robitzsch on 2015-01-11
I'm aware that PPTP is as secure as WEP is and shouldn't be really used for any serious VPN connection. But if the option is available in the *Ubuntu network manager it should be working. But thanks for the hint anyway!

---

### Post by Sebastian_Robitzsch on 2015-01-11
with a fresh mind I figured out why it is not working. Had nothing to do with the network manager implementation. Realised that the client log says: [FONT=courier new]LCP: timeout sending Config-Requests[/FONT]. So I captured all sent packets on the client side and received packets on the server and figured out that the PPP LCP Config-Request was receive and the Ack had been sent out. Based on [this thread]("http://ubuntuforums.org/showthread.php?t=1423194") I concluded that my employers firefall must drop this ACK coming from the server. I can confirm that the PPTP VPN does work after using our eduroam Wi-Fi AP.

Sorry for the noise :)

---

