---
title: "Iptables configuration for openvpn"
date: 2015-04-04
forum: Networking &amp; Wireless
---

### Post by shubh9835 on 2015-04-04
[COLOR=#000000][FONT=verdana]hi all! i just configured openvpn server to run on my fedora 21 with the help of [/FONT][/COLOR][http://fedoraproject.org/wiki/Openvpn](http://fedoraproject.org/wiki/Openvpn)[COLOR=#000000][FONT=verdana] this guide. but i am confused a little. in the firewall configuration it states[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]The following should work (assuming an outside interface is eth1 and an inside interface is eth0):
[/FONT][/COLOR]```
[COLOR=#000000]iptables -A INPUT -i eth1 -p udp --dport 1194 -j ACCEPT[/COLOR]
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -A FORWARD -i eth0 -o tun+ -j ACCEPT [COLOR=#000000]iptables -A FORWARD -i eth1 -o tun+ -m state --state ESTABLISHED,RELATED -j ACCEPT[/COLOR]
```[COLOR=#000000][FONT=verdana]
the thing is i have only one physical ethernet adaptor connected to the router . i.e p2p1  . i am confused for the part where it says "[/FONT][/COLOR][COLOR=#000000][FONT=verdana](assuming an outside interface is eth1 and an inside interface is eth0)"
in my case the outside interface is p2p1 right ?  also the inside interface should be tun0 right? 
but the above iptables rule already mention tun+ which correspond to all tun(tun0  , tun1  ,tun2)
btw i have fedora as the vpn server and ubuntu as the client
will someone please shed some light on me
thanx!![/FONT][/COLOR]

---

### Post by changingstate on 2015-04-04
I've got something similar hooked up using Tor in transparent proxy mode on Debian. I decided the easiest thing to do was to run a second virtual network interface. That way I have two ip addresses for a single port and could logically segment my network. Much as I don't know fedora internals, there's instructions here that might work for you.   [http://linuxconfig.org/configuring-virtual-network-interfaces-in-linux](http://linuxconfig.org/configuring-virtual-network-interfaces-in-linux)  Once you do that, you'll then have the two network interfaces and the tunnelling adapter the openvpn guide recommends and the iptables rules should work with minimal tweaking.

---

