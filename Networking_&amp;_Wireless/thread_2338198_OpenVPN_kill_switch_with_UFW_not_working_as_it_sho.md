---
title: "OpenVPN kill switch with UFW not working as it should"
date: 2016-09-25
forum: Networking &amp; Wireless
---

### Post by aivanofffru on 2016-09-25
Hello everyone. I hope I'm posting this in the right place.
My idea is to make Bluetooth VPN router, so all devices that connect to this router via Bluetooth are transparently connected to internet via vpn connection. Everything is working fine except the kill switch thing.
I'm running Ubuntu 14.04, bluetooth NAP is configured with blueman, vpn connection is managed by openvpn.

I have set net.ipv4.ip_forward=1 and added following iptables rules:

iptables -t nat -A POSTROUTING -o tun0 -j MASQUERADE
iptables -A FORWARD -I pan1 -o tun0 -j ACCEPT
iptables -A FORWARD -I tun0 -o pan1 -m state RELATED,ESTABLISHED -j ACCEPT

The kill switch is done with ufw:

ufw default deny outgoing
ufw default deny incoming
ufw allow out to 10.1.143.0/24
ufw allow in to 10.1.143.0/24
ufw allow out to <vpn_ip>
ufw allow out on tun0
ufw allow in on pan1 from any port 68 to any port 67 proto udp


Everything is working just fine and there's no internet on my devices when openvpn on Ubuntu is down, however when I try to connect from my laptop (running Linux Mint) to openvpn then it connects without any problems and internet is working which is obviously not what I want.


I'm stuck on this for days now and would really appreciate any help.

UPD: forgot to mention that I'm able to connect to another vpn provider from my laptop, not to the one on the ubuntu router

---

