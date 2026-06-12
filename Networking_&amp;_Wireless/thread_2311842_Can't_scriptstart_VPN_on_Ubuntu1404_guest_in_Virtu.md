---
title: "Can't scriptstart VPN on Ubuntu14:04 guest in Virtualbox on Mac"
date: 2016-01-30
forum: Networking &amp; Wireless
---

### Post by James Wilde on 2016-01-30
[COLOR=#000000]I'm running 14.04 as a Virtualbox guest on a machine running OSX 10.9[/COLOR]

[COLOR=#000000]My problem concerns starting a VPN automatically. If I enter the following command in a terminal it stops part way through the process.[/COLOR]

[COLOR=#000000]sudo openvpn --config /etc/openvpn/Los\ Angeles.ovpn[/COLOR]

[COLOR=#000000]The lines immediately before its stopping are:[/COLOR]

[COLOR=#000000]Fri Jan 29 16:17:05 2016 TUN/TAP device tun0 opened[/COLOR]
[COLOR=#000000]Fri Jan 29 16:17:05 2016 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0[/COLOR]
[COLOR=#000000]Fri Jan 29 16:17:05 2016 /sbin/ip link set dev tun0 up mtu 1500[/COLOR]
[COLOR=#000000]Fri Jan 29 16:17:05 2016 /sbin/ip addr add dev tun0 10.10.20.66/26 broadcast 10.10.20.127[/COLOR]
[COLOR=#000000]Fri Jan 29 16:17:05 2016 Initialization Sequence Completed[/COLOR]

[COLOR=#000000]But no VPN open and I can't start it from the network icon. In fact the only way I can start it is from the network icon when no previous attempt has been made to start it. (Before anybody asks, I have my id and password in a file and refer to that file in the LA.ovpn file on the line for auth-user-pass.[/COLOR]

[COLOR=#000000]So how do I start this automagically on boot-up?[/COLOR]

[COLOR=#000000]TIA[/COLOR]

---

### Post by James Wilde on 2016-01-31
No-one?  Is no-one running a vpn in Ubuntu 14:04 and starting it with a script?

---

### Post by pauljw on 2016-01-31
Sorry, can't answer your specific question, but is there a reason that you can't connect your host to the vpn prior to booting your vm?  The vm would just use that vpn connection with no further setup required.  However, if you have some special reason to only open the vpn in the vm then I'm no help.

Paul

---

