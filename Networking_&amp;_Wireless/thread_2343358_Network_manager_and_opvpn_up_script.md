---
title: "Network manager and opvpn up script"
date: 2016-11-15
forum: Networking &amp; Wireless
---

### Post by dramaekrs on 2016-11-15
Hi,

I use openvpn to connect to my cloudserver. Because some of the services are private on the vpn, I use a dns-server on the vpn network to resolve private url's. So if the vpn connection is active, the client should use the dns-server on the vpn network. If the vpn connection is not active, the client should use the dhcp provided dns-server.

I can do this manually like this:
nmcli con mod "THUIS 1" ipv4.ignore-auto-dns yes      #deactivate the dhcp provided dns-server
nmcli con mod "THUIS 1" ipv4.dns "10.111.0.1"           #Set the vpn dns-server
nmcli con up "THUIS 1"                                             #Enable the new settings

But scripting this in a up-script of openvpn is not easy. The script should do a few not straightforward analyses, will have to save the normal state of the network connections, etc...

On the www, a lot is written to solve this problem but all sollutions are based on on of two assumptions:
1) disable the dns-settings of network-manager to fall back to resolv.conf
2) having to manually change the dns-settings

I want to have the dns-setting change done by the up-script of openvpn without breaking the normal behaviour of network manager.

The goal is to implement this feature on pc's, laptops and ubuntu-touch devices of normal users... So users with no special skills...

Does anybody have a idea how to do this?

---

