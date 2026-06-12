---
title: "Network Manager shows error icon after successfully connecting to a VPN"
date: 2015-02-16
forum: Networking &amp; Wireless
---

### Post by joxeankoret on 2015-02-16
Hi,


I'm suspicious about this behaviour. Today I noticed that NM is showing an error icon in the notification area after successfully connecting to a VPN. It's the first time I see this icon and, I repeat, the VPN connection works. The following is what I have in my /var/log/syslog:


```

Feb 16 10:49:35 backup-server nm-openvpn[32310]: OpenVPN 2.2.1 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Dec  1 2014
Feb 16 10:49:35 backup-server nm-openvpn[32310]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Feb 16 10:49:35 backup-server nm-openvpn[32310]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Feb 16 10:49:35 backup-server nm-openvpn[32310]: LZO compression initialized
Feb 16 10:49:35 backup-server nm-openvpn[32310]: UDPv4 link local: [undef]
Feb 16 10:49:35 backup-server nm-openvpn[32310]: UDPv4 link remote: [AF_INET]VPN.IP.ADDRESS:1194
Feb 16 10:49:41 backup-server nm-openvpn[32310]: [XXXCOMPANY] Peer Connection Initiated with [AF_INET]VPN.IP.ADDRESS:1194
Feb 16 10:49:44 backup-server nm-openvpn[32310]: TUN/TAP device tun0 opened
Feb 16 10:49:44 backup-server nm-openvpn[32310]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper tun0 1500 1542 192.168.88.38 192.168.88.37 init
Feb 16 10:49:44 backup-server NetworkManager[1413]: <info> VPN connection 'XXXCOMPANY (openvpn)' (IP Config Get) reply received.
Feb 16 10:49:44 backup-server NetworkManager[1413]: <info> VPN Gateway: VPN.IP.ADDRESS
Feb 16 10:49:44 backup-server NetworkManager[1413]: <info> Internal Gateway: 192.168.88.37
Feb 16 10:49:44 backup-server NetworkManager[1413]: <info> Tunnel Device: tun0
Feb 16 10:49:44 backup-server NetworkManager[1413]: <info> Internal IP4 Address: 192.168.88.38
Feb 16 10:49:44 backup-server NetworkManager[1413]: <info> Internal IP4 Prefix: 32
Feb 16 10:49:44 backup-server NetworkManager[1413]: <info> Internal IP4 Point-to-Point Address: 192.168.88.37
Feb 16 10:49:44 backup-server NetworkManager[1413]: <info> Maximum Segment Size (MSS): 0
Feb 16 10:49:44 backup-server NetworkManager[1413]: <info> Static Route: 192.168.88.1/32   Next Hop: 192.168.88.1
Feb 16 10:49:44 backup-server NetworkManager[1413]: <info> Forbid Default Route: no
Feb 16 10:49:44 backup-server NetworkManager[1413]: <info> DNS Domain: '(none)'
Feb 16 10:49:44 backup-server nm-openvpn[32310]: Initialization Sequence Completed
Feb 16 10:49:45 backup-server NetworkManager[1413]: <info> (tun0): writing resolv.conf to /sbin/resolvconf
Feb 16 10:49:45 backup-server dnsmasq[1629]: se establecen los servidores superiores desde DBus
Feb 16 10:49:45 backup-server dnsmasq[1629]: se usa el servidor 192.168.1.1#53
Feb 16 10:49:45 backup-server NetworkManager[1413]: <info> VPN connection 'XXXCOMPANY (openvpn)' (IP Config Get) complete.
Feb 16 10:49:45 backup-server NetworkManager[1413]: <info> Policy set 'Conexión cableada 1' (eth1) as default for IPv4 routing and DNS.
Feb 16 10:49:45 backup-server dbus[1293]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb 16 10:49:45 backup-server NetworkManager[1413]: <info> VPN plugin state changed: started (4)
Feb 16 10:49:45 backup-server NetworkManager[1413]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Feb 16 10:49:45 backup-server NetworkManager[1413]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Feb 16 10:49:45 backup-server dbus[1293]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb 16 10:49:45 backup-server nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.

```


I suspect the culprit is the last line where 01ifupdown fails. Any idea about what is happening? I updated my x86_64 Ubuntu 12.04.5 LTS today and, also, the company updated (apt-get upgrade) the VPN server recently.


Thanks in advance!

---

