---
title: "Need some VPN help"
date: 2014-05-14
forum: Networking &amp; Wireless
---

### Post by cannon_dt on 2014-05-14
Hi,

I used the vpn portion of the guide over at [http://digitalstudio7.blogspot.in/2013/08/how-to-install-spotify-in-other.html](http://digitalstudio7.blogspot.in/2013/08/how-to-install-spotify-in-other.html). However after successful establishment of the vpn connection, it drops off in a matter of seconds rendering it dead. Below is the snapshot of my syslog, can someone please help

Thanks,
Ananth

```
May 14 15:14:21 ananthakrishnan-desktop pppd[14538]: Using interface ppp0
May 14 15:14:21 ananthakrishnan-desktop pppd[14538]: Connect: ppp0 <--> /dev/pts/3
May 14 15:14:21 ananthakrishnan-desktop NetworkManager[858]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 14 15:14:21 ananthakrishnan-desktop NetworkManager[858]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 14 15:14:21 ananthakrishnan-desktop pptp[14542]: nm-pptp-service-14536 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
May 14 15:14:21 ananthakrishnan-desktop NetworkManager[858]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
May 14 15:14:21 ananthakrishnan-desktop pptp[14554]: nm-pptp-service-14536 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
May 14 15:14:21 ananthakrishnan-desktop pptp[14554]: nm-pptp-service-14536 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
May 14 15:14:21 ananthakrishnan-desktop pptp[14554]: nm-pptp-service-14536 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
May 14 15:14:22 ananthakrishnan-desktop pptp[14554]: nm-pptp-service-14536 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
May 14 15:14:22 ananthakrishnan-desktop pptp[14554]: nm-pptp-service-14536 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
May 14 15:14:22 ananthakrishnan-desktop pptp[14554]: nm-pptp-service-14536 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 41344).
May 14 15:14:23 ananthakrishnan-desktop pppd[14538]: CHAP authentication succeeded
May 14 15:14:23 ananthakrishnan-desktop pppd[14538]: MPPE 128-bit stateless compression enabled
May 14 15:14:24 ananthakrishnan-desktop pppd[14538]: local  IP address 172.16.36.246
May 14 15:14:24 ananthakrishnan-desktop pppd[14538]: remote IP address 172.16.36.1
May 14 15:14:24 ananthakrishnan-desktop pppd[14538]: primary   DNS address 8.8.8.8
May 14 15:14:24 ananthakrishnan-desktop pppd[14538]: secondary DNS address 8.8.4.4
May 14 15:14:24 ananthakrishnan-desktop NetworkManager[858]: <info> VPN connection 'US' (IP4 Config Get) reply received from old-style plugin.
May 14 15:14:24 ananthakrishnan-desktop NetworkManager[858]: <info> VPN Gateway: 198.7.62.204
May 14 15:14:24 ananthakrishnan-desktop NetworkManager[858]: <info> Tunnel Device: ppp0
May 14 15:14:24 ananthakrishnan-desktop NetworkManager[858]: <info> IPv4 configuration:
May 14 15:14:24 ananthakrishnan-desktop NetworkManager[858]: <info>   Internal Address: 172.16.36.246
May 14 15:14:24 ananthakrishnan-desktop NetworkManager[858]: <info>   Internal Prefix: 32
May 14 15:14:24 ananthakrishnan-desktop NetworkManager[858]: <info>   Internal Point-to-Point Address: 172.16.36.1
May 14 15:14:24 ananthakrishnan-desktop NetworkManager[858]: <info>   Maximum Segment Size (MSS): 0
May 14 15:14:24 ananthakrishnan-desktop NetworkManager[858]: <info>   Forbid Default Route: no
May 14 15:14:24 ananthakrishnan-desktop NetworkManager[858]: <info>   Internal DNS: 8.8.8.8
May 14 15:14:24 ananthakrishnan-desktop NetworkManager[858]: <info>   Internal DNS: 8.8.4.4
May 14 15:14:24 ananthakrishnan-desktop NetworkManager[858]: <info>   DNS Domain: '(none)'
May 14 15:14:24 ananthakrishnan-desktop NetworkManager[858]: <info> No IPv6 configuration
May 14 15:14:25 ananthakrishnan-desktop NetworkManager[858]: <info> VPN connection 'US' (IP Config Get) complete.
May 14 15:14:25 ananthakrishnan-desktop NetworkManager[858]: <info> Policy set 'US' (ppp0) as default for IPv4 routing and DNS.
May 14 15:14:25 ananthakrishnan-desktop NetworkManager[858]: <info> Writing DNS information to /sbin/resolvconf
May 14 15:14:25 ananthakrishnan-desktop dnsmasq[1434]: setting upstream servers from DBus
May 14 15:14:25 ananthakrishnan-desktop dnsmasq[1434]: using nameserver 8.8.4.4#53
May 14 15:14:25 ananthakrishnan-desktop dnsmasq[1434]: using nameserver 8.8.8.8#53
May 14 15:14:25 ananthakrishnan-desktop dbus[743]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 14 15:14:25 ananthakrishnan-desktop NetworkManager[858]: <info> VPN plugin state changed: started (4)
May 14 15:14:25 ananthakrishnan-desktop dbus[743]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 14 15:14:33 ananthakrishnan-desktop ntpdate[14598]: no server suitable for synchronization found
May 14 15:14:37 ananthakrishnan-desktop pptp[14542]: nm-pptp-service-14536 warn[decaps_gre:pptp_gre.c:331]: short read (-1): Message too long
May 14 15:14:37 ananthakrishnan-desktop pptp[14554]: nm-pptp-service-14536 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
May 14 15:14:37 ananthakrishnan-desktop pptp[14554]: nm-pptp-service-14536 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
May 14 15:14:37 ananthakrishnan-desktop pptp[14554]: nm-pptp-service-14536 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
May 14 15:14:37 ananthakrishnan-desktop pppd[14538]: Modem hangup
May 14 15:14:37 ananthakrishnan-desktop pppd[14538]: Connect time 0.3 minutes.
May 14 15:14:37 ananthakrishnan-desktop pppd[14538]: Sent 3839 bytes, received 213 bytes.
May 14 15:14:37 ananthakrishnan-desktop pppd[14538]: MPPE disabled
May 14 15:14:37 ananthakrishnan-desktop pppd[14538]: Connection terminated.
May 14 15:14:37 ananthakrishnan-desktop NetworkManager[858]: <info> VPN plugin state changed: stopping (5)
May 14 15:14:37 ananthakrishnan-desktop NetworkManager[858]: <info> VPN plugin state changed: stopped (6)
May 14 15:14:37 ananthakrishnan-desktop NetworkManager[858]: <info> VPN plugin state change reason: 0
May 14 15:14:37 ananthakrishnan-desktop avahi-daemon[827]: Withdrawing workstation service for ppp0.
May 14 15:14:37 ananthakrishnan-desktop avahi-daemon[827]: Withdrawing address record for 10.0.0.2 on eth0.
May 14 15:14:37 ananthakrishnan-desktop avahi-daemon[827]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.0.0.2.
May 14 15:14:37 ananthakrishnan-desktop avahi-daemon[827]: Interface eth0.IPv4 no longer relevant for mDNS.
May 14 15:14:37 ananthakrishnan-desktop avahi-daemon[827]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.0.2.
May 14 15:14:37 ananthakrishnan-desktop avahi-daemon[827]: New relevant interface eth0.IPv4 for mDNS.
May 14 15:14:37 ananthakrishnan-desktop avahi-daemon[827]: Registering new address record for 10.0.0.2 on eth0.IPv4.
May 14 15:14:37 ananthakrishnan-desktop pppd[14538]: Exit.
May 14 15:14:38 ananthakrishnan-desktop NetworkManager[858]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
May 14 15:14:38 ananthakrishnan-desktop NetworkManager[858]: <info> Writing DNS information to /sbin/resolvconf
May 14 15:14:38 ananthakrishnan-desktop dnsmasq[1434]: setting upstream servers from DBus
May 14 15:14:38 ananthakrishnan-desktop dnsmasq[1434]: using nameserver 10.0.0.1#53
May 14 15:14:38 ananthakrishnan-desktop dbus[743]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 14 15:14:38 ananthakrishnan-desktop NetworkManager[858]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
May 14 15:14:38 ananthakrishnan-desktop NetworkManager[858]: <warn> (32) failed to find interface name for index
May 14 15:14:38 ananthakrishnan-desktop NetworkManager[858]: nm_system_iface_flush_routes: assertion 'iface != NULL' failed
May 14 15:14:38 ananthakrishnan-desktop NetworkManager[858]: <warn> (32) failed to find interface name for index
May 14 15:14:38 ananthakrishnan-desktop NetworkManager[858]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 14 15:14:38 ananthakrishnan-desktop dbus[743]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 14 15:14:43 ananthakrishnan-desktop NetworkManager[858]: <info> VPN service 'pptp' disappeared
```

---

### Post by Nimigean_Horatiu on 2014-05-14
try this 
[http://i-heart-geek.blogspot.ro/2011/06/solved-vpn-short-read-1-message-too.html](http://i-heart-geek.blogspot.ro/2011/06/solved-vpn-short-read-1-message-too.html)

---

### Post by cannon_dt on 2014-05-14
Thanks Nimigean. I already did try setting the MTU, did not help

I am trying to get openvpn to work with vpnbook. Will update you once I get it done

Peace

---

