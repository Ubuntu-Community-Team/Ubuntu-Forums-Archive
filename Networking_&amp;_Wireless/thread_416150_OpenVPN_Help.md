---
title: "OpenVPN Help"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by xmrcivicboix on 2007-04-20
I'm a total noobie and was wondering if someone can help me with this. I have XP running on this work laptop and OpenVPN is already configured; however, I just installed Ubuntu on my external harddrive and want to be able to use OpenVPN in Ubuntu as well. I have installed openvpn, openssl, and ssh but I have no clue what else to do after that. I have 3 files from my Windows install that I think might need: TCP.ovpn, UDP.ovpn, and laptop.key. I placed those files in /etc/openvpn and changed the two .ovpn to .conf but then I don't know what to do after that. Is there a way to get a GUI to login or something?

Thanks

---

### Post by bnuytten on 2007-04-21
/etc/openvpn/openvpn.conf
/etc/openvpn/static.key <- you already have this one
/etc/openvpn/tun0.conf
/etc/openvpn/tun0.up
/etc/ppp/peers
/etc/ppp/options
[https://help.ubuntu.com/community/VPNClient]("https://help.ubuntu.com/community/VPNClient")

---

