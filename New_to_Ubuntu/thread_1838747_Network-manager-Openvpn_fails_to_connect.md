---
title: "Network-manager-Openvpn fails to connect"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by UniXSouL on 2011-09-04
Hello Folks,
this is my first post here.. At home I'm trying to connect to my office  OpenVPN server.  It works perfectly well with Kvpn  or via CLI but for  some reason I couldn't manage to make it work with  Network-Manager-Openvpn. I've used both the import feature and the  manual configuration, i've tried to un-check “available to all users”  and “ignore automatically obtained routes” but I still have the same  problem. Here is what happens in the log files:

> NetworkManager[10331]: <info> Starting VPN service 'openvpn'... 
NetworkManager[10331]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 10569 
NetworkManager[10331]: <info> VPN service 'openvpn' appeared; activating connections 
NetworkManager[10331]: <info> VPN plugin state changed: 1 
NetworkManager[10331]: <info> VPN plugin state changed: 3 
** Message: openvpn started with pid 10572 
NetworkManager[10331]: <info> VPN connection 'sofia.lab.internet' (Connect) reply received. 
NetworkManager[10331]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tap0, iface: tap0) 
NetworkManager[10331]:    SCPlugin-Ifupdown: device added (path:  /sys/devices/virtual/net/tap0, iface: tap0): no ifupdown configuration  found. 
NetworkManager[10331]: <warn> /sys/devices/virtual/net/tap0: couldn't determine device driver; ignoring... 
 
** (process:10601): WARNING **: nm-openvpn-service-openvpn-helper did not receive a valid IP4 Address from openvpn 
NetworkManager[10331]: <warn> VPN plugin failed: 2 
NetworkManager[10331]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tap0, iface: tap0) 
 
** (nm-openvpn-service:10569): WARNING **: openvpn exited with error code 1 
NetworkManager[10331]: <warn> VPN plugin failed: 1 
NetworkManager[10331]: <info> VPN plugin state changed: 6 
NetworkManager[10331]: <info> VPN plugin state change reason: 0 
NetworkManager[10331]: <warn> error disconnecting VPN: Could not  process the request because no VPN connection was active.
In my setup I'm using certificates for authentication, no LZO  compression and TAP  interface. My Ubuntu is Amd64-Desktop 11.10 Beta 1.   For the Ip addresses of the client i'm using dhcpd rather than the  build-in functionality in openvpn-server...
    This wasn't working for me also in Ubuntu 11.04.

Any ideas ?

---

