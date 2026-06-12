---
title: "VPN drops immediately after connecting"
date: 2013-11-24
forum: Networking &amp; Wireless
---

### Post by gerteix on 2013-11-24
Hi All,

My VPN disconnects immediately after connecting successfully. 

I am lost at the moment and can't figure out what could be the issue, this is the log. 

Nov 24 12:35:37 ubuntu NetworkManager[943]: <info> Starting VPN service 'vpnc'...
Nov 24 12:35:37 ubuntu NetworkManager[943]: <info> VPN service 'vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 7480
Nov 24 12:35:37 ubuntu NetworkManager[943]: <info> VPN service 'vpnc' appeared; activating connections
Nov 24 12:35:37 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1236] Insert information about connection active in listInfoConnection
Nov 24 12:35:37 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1253] Production_VPN in authentification
Nov 24 12:35:37 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1267] Production_VPN connecting
Nov 24 12:35:37 ubuntu NetworkManager[943]: <info> VPN plugin state changed: starting (3)
Nov 24 12:35:37 ubuntu NetworkManager[943]: <info> VPN connection 'Production_VPN' (Connect) reply received.
Nov 24 12:35:37 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1278] Production_VPN getting ip
Nov 24 12:35:37 ubuntu NetworkManager[943]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Nov 24 12:35:37 ubuntu NetworkManager[943]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Nov 24 12:35:40 ubuntu NetworkManager[943]: <info> VPN connection 'Production_VPN' (IP Config Get) reply received.
Nov 24 12:35:40 ubuntu NetworkManager[943]: <info> VPN Gateway: 217.171.137.239
Nov 24 12:35:40 ubuntu NetworkManager[943]: <info> Tunnel Device: tun0
Nov 24 12:35:40 ubuntu NetworkManager[943]: <info> Internal IP4 Address: 192.168.163.111
Nov 24 12:35:40 ubuntu NetworkManager[943]: <info> Internal IP4 Prefix: 24
Nov 24 12:35:40 ubuntu NetworkManager[943]: <info> Internal IP4 Point-to-Point Address: 192.168.163.111
Nov 24 12:35:40 ubuntu NetworkManager[943]: <info> Maximum Segment Size (MSS): 0
Nov 24 12:35:40 ubuntu NetworkManager[943]: <info> Forbid Default Route: no
Nov 24 12:35:40 ubuntu NetworkManager[943]: <info> DNS Domain: '(none)'
Nov 24 12:35:41 ubuntu NetworkManager[943]: <info> (tun0): writing resolv.conf to /sbin/resolvconf
Nov 24 12:35:41 ubuntu dnsmasq[1490]: setting upstream servers from DBus
Nov 24 12:35:41 ubuntu NetworkManager[943]: <info> VPN connection 'Production_VPN' (IP Config Get) complete.
Nov 24 12:35:41 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1287] Production_VPN connected
Nov 24 12:35:41 ubuntu NetworkManager[943]: <info> Policy set 'Production_VPN' (tun0) as default for IPv4 routing and DNS.
Nov 24 12:35:41 ubuntu NetworkManager[943]: <info> VPN plugin state changed: started (4)
Nov 24 12:35:41 ubuntu dbus[660]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Nov 24 12:35:41 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1659] New connection UP Production_VPN but already seen before
Nov 24 12:35:41 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1676] reconnect VPN attached by this connection (Production_VPN)
Nov 24 12:35:41 ubuntu dbus[660]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov 24 12:35:41 ubuntu ntpdate[7529]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Nov 24 12:35:41 ubuntu ntpdate[7529]: no servers can be used, exiting

Nov 24 12:35:45 ubuntu lvpnc[2155]: [linkState.c:143] Send message to daemon to deconnect
Nov 24 12:35:45 ubuntu NetworkManager[943]: <info> (tun0): writing resolv.conf to /sbin/resolvconf
Nov 24 12:35:45 ubuntu dnsmasq[1490]: setting upstream servers from DBus
Nov 24 12:35:45 ubuntu dnsmasq[1490]: using nameserver 192.168.43.1#53
Nov 24 12:35:45 ubuntu avahi-daemon[819]: Withdrawing workstation service for tun0.
Nov 24 12:35:46 ubuntu NetworkManager[943]: <info> Policy set 'Nexus5-GT' (wlan0) as default for IPv4 routing and DNS.
Nov 24 12:35:46 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1153] Production_VPN has stopped forceReconnect flag is set on
Nov 24 12:35:46 ubuntu NetworkManager[943]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Nov 24 12:35:46 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1364] Production_VPN disconnected
Nov 24 12:35:46 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1372] Force reconnect is on reconnect Production_VPN
Nov 24 12:35:46 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1056] Error not unable to remove object infoConnection activeID:20
Nov 24 12:35:46 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1092] Reconnection in progress
Nov 24 12:35:46 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1236] Insert information about connection active in listInfoConnection
Nov 24 12:35:46 ubuntu lvpnc[2155]: [DBUSMessageLoop.c:1253] Production_VPN in authentification


Cheers for the help.
br

---

### Post by gerteix on 2013-11-24
Hi,
If I kill this process then the vpn connection is maintaned:

ubuntu:~$ ps -ef | grep vpnc
    2144     1  0 13:22 ?        00:00:01 /usr/bin/lvpnc

Any ideas as to why?

---

