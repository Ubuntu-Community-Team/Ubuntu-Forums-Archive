---
title: "Openconnect kills networkmanager"
date: 2015-10-27
forum: Networking &amp; Wireless
---

### Post by Akegata on 2015-10-27
I have a vpn connection set up that used to work flawlessly in 14.10, using openconnect through the nm-applet.

After upgrading to 15.10, networkmanager is killed every time I establish a vpn connection.
```
Oct 27 22:26:57 alucard NetworkManager[814]: <info> VPN connection 'VPN connection 2' (ConnectInteractive) reply received.
Oct 27 22:26:57 alucard NetworkManager[814]: ** (nm-openconnect-service:2322): WARNING **: property 'cookie-flags' unknown
Oct 27 22:26:57 alucard NetworkManager[814]: ** (nm-openconnect-service:2322): WARNING **: property 'certsigs-flags' unknown
Oct 27 22:26:57 alucard NetworkManager[814]: ** (nm-openconnect-service:2322): WARNING **: property 'lasthost-flags' unknown
Oct 27 22:26:57 alucard NetworkManager[814]: ** (nm-openconnect-service:2322): WARNING **: property 'autoconnect-flags' unknown
Oct 27 22:26:57 alucard NetworkManager[814]: ** (nm-openconnect-service:2322): WARNING **: property 'gateway-flags' unknown
Oct 27 22:26:57 alucard NetworkManager[814]: ** (nm-openconnect-service:2322): WARNING **: property 'gwcert-flags' unknown
Oct 27 22:26:57 alucard NetworkManager[814]: ** (nm-openconnect-service:2322): WARNING **: property 'xmlconfig-flags' unknown
Oct 27 22:26:57 alucard NetworkManager[814]: ** (nm-openconnect-service:2322): WARNING **: property 'xmlconfig' unknown
Oct 27 22:26:57 alucard NetworkManager[814]: ** (nm-openconnect-service:2322): WARNING **: property 'lasthost' unknown
Oct 27 22:26:57 alucard NetworkManager[814]: ** (nm-openconnect-service:2322): WARNING **: property 'certificate:<ip>:443' unknown
Oct 27 22:26:57 alucard NetworkManager[814]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Oct 27 22:26:57 alucard NetworkManager[814]: <info> (vpn0): carrier is OFF
Oct 27 22:26:57 alucard NetworkManager[814]: <info> (vpn0): new Tun device (driver: 'unknown' ifindex: 8)
Oct 27 22:26:57 alucard NetworkManager[814]: <info> (vpn0): exported as /org/freedesktop/NetworkManager/Devices/4
Oct 27 22:26:57 alucard NetworkManager[814]: <info> VPN plugin state changed: starting (3)
Oct 27 22:26:57 alucard NetworkManager[814]: ** (nm-openconnect-service:2322): WARNING **: Created tundev vpn0
Oct 27 22:26:57 alucard NetworkManager[814]: ** Message: openconnect started with pid 2695
Oct 27 22:26:57 alucard NetworkManager[814]: <info> VPN connection 'VPN connection 2' (Connect) reply received.
Oct 27 22:26:57 alucard openconnect[2695]: Attempting to connect to server <ip>:443
Oct 27 22:26:57 alucard NetworkManager[814]: <info> devices added (path: /sys/devices/virtual/net/vpn0, iface: vpn0)
Oct 27 22:26:57 alucard NetworkManager[814]: <info> device added (path: /sys/devices/virtual/net/vpn0, iface: vpn0): no ifupdown configuration found.
Oct 27 22:26:57 alucard openconnect[2695]: SSL negotiation with <ip>
Oct 27 22:26:57 alucard openconnect[2695]: Server certificate verify failed: signer not found
Oct 27 22:26:57 alucard openconnect[2695]: Connected to HTTPS on <ip>
Oct 27 22:26:57 alucard openconnect[2695]: Got CONNECT response: HTTP/1.1 200 OK
Oct 27 22:26:57 alucard openconnect[2695]: CSTP connected. DPD 30, Keepalive 20
Oct 27 22:26:57 alucard openconnect[2695]: SIOCSIFMTU: Operation not permitted
Oct 27 22:26:57 alucard NetworkManager[814]: <info> VPN connection 'VPN connection 2' (IP Config Get) reply received.
Oct 27 22:26:57 alucard NetworkManager[814]: <info> VPN connection 'VPN connection 2' (IP4 Config Get) reply received.
Oct 27 22:26:57 alucard NetworkManager[814]: <info> VPN Gateway: <ip>
Oct 27 22:26:57 alucard openconnect[2695]: Connected vpn0 as <ip>, using SSL
Oct 27 22:26:57 alucard NetworkManager[814]: <info> Tunnel Device: vpn0
Oct 27 22:26:57 alucard NetworkManager[814]: <info> IPv4 configuration:
Oct 27 22:26:57 alucard NetworkManager[814]: <info>   Internal Address: <ip>
Oct 27 22:26:57 alucard NetworkManager[814]: <info>   Internal Prefix: 32
Oct 27 22:26:57 alucard NetworkManager[814]: <info>   Internal Point-to-Point Address: <ip>
Oct 27 22:26:57 alucard NetworkManager[814]: <info>   Maximum Segment Size (MSS): 0
Oct 27 22:26:57 alucard NetworkManager[814]: <info>   Forbid Default Route: no
Oct 27 22:26:57 alucard NetworkManager[814]: <info>   Internal DNS: <ip>
Oct 27 22:26:57 alucard NetworkManager[814]: <info>   Internal DNS: <ip>
Oct 27 22:26:57 alucard NetworkManager[814]: <info>   DNS Domain: 'domain'
Oct 27 22:26:57 alucard NetworkManager[814]: <info> No IPv6 configuration
Oct 27 22:26:57 alucard NetworkManager[814]: <info> (vpn0): link connected
Oct 27 22:26:57 alucard NetworkManager[814]: <info> VPN connection 'VPN connection 2' (IP Config Get) complete.
Oct 27 22:26:57 alucard NetworkManager[814]: <info> VPN plugin state changed: started (4)
Oct 27 22:26:57 alucard openconnect[2695]: Established DTLS connection (using GnuTLS). Ciphersuite (DTLS0.9)-(RSA)-(AES-256-CBC)-(SHA1).
Oct 27 22:26:57 alucard NetworkManager[814]: <info> Writing DNS information to /sbin/resolvconf
Oct 27 22:26:57 alucard dnsmasq[1787]: setting upstream servers from DBus
Oct 27 22:26:57 alucard dnsmasq[1787]: using nameserver <ip>#53
Oct 27 22:26:57 alucard dnsmasq[1787]: using nameserver <ip>#53
Oct 27 22:26:58 alucard dnsmasq[1166]: reading /etc/resolv.conf
Oct 27 22:26:58 alucard dnsmasq[1428]: reading /etc/resolv.conf
Oct 27 22:26:58 alucard dnsmasq[1166]: using nameserver 127.0.1.1#53
Oct 27 22:26:58 alucard dnsmasq[1428]: using nameserver 127.0.1.1#53
Oct 27 22:26:58 alucard systemd[1]: Reloading LSB: Postfix Mail Transport Agent.
Oct 27 22:26:58 alucard postfix[2778]: * Reloading Postfix configuration...
Oct 27 22:26:58 alucard postfix[2780]: fatal: chdir(/usr/libexec/postfix): No such file or directory
Oct 27 22:26:59 alucard postfix[2778]: ...fail!
Oct 27 22:26:59 alucard systemd[1]: Reloaded LSB: Postfix Mail Transport Agent.
Oct 27 22:26:59 alucard dbus[823]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Oct 27 22:26:59 alucard NetworkManager[814]: <info> (vpn0): device state change: unmanaged -> unavailable (reason 'connection-assumed') [10 20 41]
Oct 27 22:26:59 alucard systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct 27 22:26:59 alucard NetworkManager[814]: <info> (vpn0): device state change: unavailable -> disconnected (reason 'connection-assumed') [20 30 41]
Oct 27 22:26:59 alucard NetworkManager[814]: <info> Device 'vpn0' has no connection; scheduling activate_check in 0 seconds.
Oct 27 22:26:59 alucard systemd[1]: NetworkManager.service: Main process exited, code=killed, status=6/ABRT
Oct 27 22:26:59 alucard NetworkManager[814]: <info> Activation (vpn0) starting connection 'vpn0'
Oct 27 22:26:59 alucard systemd[1]: NetworkManager.service: Unit entered failed state.
Oct 27 22:26:59 alucard NetworkManager[814]: <info> Activation (vpn0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 27 22:26:59 alucard systemd[1]: NetworkManager.service: Failed with result 'signal'.
Oct 27 22:26:59 alucard dbus[823]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 27 22:26:59 alucard systemd[1]: Started Network Manager Script Dispatcher Service.
Oct 27 22:26:59 alucard NetworkManager[814]: **
Oct 27 22:26:59 alucard NetworkManager[814]: libnm-util:ERROR:nm-utils.c:2611:nm_utils_get_private: code should not be reached
```

I have tried running openconnect from a terminal, that produces the same result.
The connection is established, but networkmanager dies and cannot be started again as long as the vpn0 interface is present.

---

