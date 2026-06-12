---
title: "How to block non VPN connections."
date: 2015-07-22
forum: Networking &amp; Wireless
---

### Post by ksantr on 2015-07-22
Hello.

I use this rules for every vpn session:

sudo openvpn --config client.ovpn && \
    sudo iptables -A OUTPUT -o eth0 -j DROP; \
    sudo iptables -A OUTPUT -o wlan0 -j DROP'

But when I lost my vpn connection, wlan0 OUTPUT continues to work with some strange behaviour: ping (icmp) not works, but http connections continues to work.

What is the best way to avoid situations like this? 

I use UFW and may be this is a reason of this trouble, but I'm not sure.

p/s Sorry for my bad English.

---

