---
title: "Creating openvpn connection network manager"
date: 2015-11-09
forum: Networking &amp; Wireless
---

### Post by blixem2 on 2015-11-09
Hello,

It's driving me crazy, but I can't connect via the Lubuntu 15.10 network manager when I creating an openvpn connection.

I have insert all the things it needs to do his work. Log:

Nov  9 20:09:20 hjalmar-linux dbus[657]: [system] Successfully activated service 'org.freedesktop.hostname1'
Nov  9 20:09:20 hjalmar-linux systemd[1]: Started Hostname Service.
Nov  9 20:09:37 hjalmar-linux NetworkManager[668]: <info>  VPN service 'openvpn' disappeared
Nov  9 20:09:49 hjalmar-linux NetworkManager[668]: <info>  Starting VPN service 'openvpn'...
Nov  9 20:09:49 hjalmar-linux NetworkManager[668]: <info>  VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 7315
Nov  9 20:09:49 hjalmar-linux com.canonical.indicator.application[906]: (process:1057): indicator-application-service-WARNING **: Application already exists, re-requesting properties.
Nov  9 20:09:49 hjalmar-linux NetworkManager[668]: <info>  VPN service 'openvpn' appeared; activating connections
Nov  9 20:09:49 hjalmar-linux com.canonical.indicator.application[906]: (process:1057): indicator-application-service-WARNING **: Application already exists, re-requesting properties.
Nov  9 20:09:49 hjalmar-linux NetworkManager[668]: <info>  VPN plugin state changed: starting (3)
Nov  9 20:09:49 hjalmar-linux NetworkManager[668]: nm-openvpn-Message: openvpn started with pid 7321
Nov  9 20:09:49 hjalmar-linux NetworkManager[668]: <info>  VPN connection 'client' (ConnectInteractive) reply received.
Nov  9 20:09:49 hjalmar-linux nm-openvpn[7321]: OpenVPN 2.3.7 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jul  8 2015
Nov  9 20:09:49 hjalmar-linux nm-openvpn[7321]: library versions: OpenSSL 1.0.2d 9 Jul 2015, LZO 2.08
Nov  9 20:09:49 hjalmar-linux com.canonical.indicator.application[906]: (process:1057): indicator-application-service-WARNING **: Application already exists, re-requesting properties.
Nov  9 20:09:49 hjalmar-linux nm-openvpn[7321]: WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Nov  9 20:09:49 hjalmar-linux nm-openvpn[7321]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Nov  9 20:09:49 hjalmar-linux nm-openvpn[7321]: Attempting to establish TCP connection with [AF_INET]ip:1194 [nonblock]
Nov  9 20:09:50 hjalmar-linux nm-openvpn[7321]: TCP: connect to [AF_INET]ip:1194 failed, will try again in 5 seconds: Connection refused
Nov  9 20:09:55 hjalmar-linux dbus[657]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Nov  9 20:09:55 hjalmar-linux NetworkManager[668]: nm-openvpn-Message: Terminated openvpn daemon with PID 7321.
Nov  9 20:09:55 hjalmar-linux nm-openvpn[7321]: SIGTERM[hard,init_instance] received, process exiting
Nov  9 20:09:55 hjalmar-linux systemd[1]: Starting Network Manager Script Dispatcher Service...
Nov  9 20:09:55 hjalmar-linux com.canonical.indicator.application[906]: (process:1057): indicator-application-service-WARNING **: Application already exists, re-requesting properties.
Nov  9 20:09:55 hjalmar-linux com.canonical.indicator.application[906]: (process:1057): indicator-application-service-WARNING **: Application already exists, re-requesting properties.
Nov  9 20:09:55 hjalmar-linux dbus[657]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov  9 20:09:55 hjalmar-linux systemd[1]: Started Network Manager Script Dispatcher Service.
Nov  9 20:09:55 hjalmar-linux nm-dispatcher: Dispatching action 'vpn-down' for enp5s0
Nov  9 20:10:15 hjalmar-linux NetworkManager[668]: <info>  VPN service 'openvpn' disappeared
Nov  9 20:10:18 hjalmar-linux NetworkManager[668]: <info>  Starting VPN service 'openvpn'...
Nov  9 20:10:18 hjalmar-linux NetworkManager[668]: <info>  VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 7366
Nov  9 20:10:18 hjalmar-linux com.canonical.indicator.application[906]: (process:1057): indicator-application-service-WARNING **: Application already exists, re-requesting properties.
Nov  9 20:10:18 hjalmar-linux NetworkManager[668]: <info>  VPN service 'openvpn' appeared; activating connections
Nov  9 20:10:18 hjalmar-linux com.canonical.indicator.application[906]: (process:1057): indicator-application-service-WARNING **: Application already exists, re-requesting properties.
Nov  9 20:10:18 hjalmar-linux NetworkManager[668]: <info>  VPN plugin state changed: starting (3)
Nov  9 20:10:18 hjalmar-linux NetworkManager[668]: nm-openvpn-Message: openvpn started with pid 7372
Nov  9 20:10:18 hjalmar-linux NetworkManager[668]: <info>  VPN connection 'client' (ConnectInteractive) reply received.
Nov  9 20:10:18 hjalmar-linux nm-openvpn[7372]: OpenVPN 2.3.7 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jul  8 2015
Nov  9 20:10:18 hjalmar-linux nm-openvpn[7372]: library versions: OpenSSL 1.0.2d 9 Jul 2015, LZO 2.08
Nov  9 20:10:18 hjalmar-linux com.canonical.indicator.application[906]: (process:1057): indicator-application-service-WARNING **: Application already exists, re-requesting properties.
Nov  9 20:10:18 hjalmar-linux nm-openvpn[7372]: WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Nov  9 20:10:18 hjalmar-linux nm-openvpn[7372]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Nov  9 20:10:18 hjalmar-linux nm-openvpn[7372]: UDPv4 link local: [undef]
Nov  9 20:10:18 hjalmar-linux nm-openvpn[7372]: UDPv4 link remote: [AF_INET]ip:1194
Nov  9 20:10:59 hjalmar-linux NetworkManager[668]: <warn>  VPN connection 'client' connect timeout exceeded.
Nov  9 20:10:59 hjalmar-linux NetworkManager[668]: nm-openvpn-Message: Terminated openvpn daemon with PID 7372.
Nov  9 20:10:59 hjalmar-linux nm-openvpn[7372]: SIGTERM[hard,] received, process exiting
Nov  9 20:10:59 hjalmar-linux com.canonical.indicator.application[906]: (process:1057): indicator-application-service-WARNING **: Application already exists, re-requesting properties.

When I do this:

sudo openvpn --config client.ovpn

it's connecting succesfully. But with the network manager not.

Any idea's?

---

### Post by blixem2 on 2015-11-10
Nobody? :(

---

