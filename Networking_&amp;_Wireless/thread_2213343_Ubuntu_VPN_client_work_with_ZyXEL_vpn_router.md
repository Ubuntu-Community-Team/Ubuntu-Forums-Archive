---
title: "Ubuntu VPN client work with ZyXEL vpn router?"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by DetroitDoc on 2014-03-26
I'm building a small business network and am looking at using a ZyXEL USG50 firewall/VPN router.   It supports Ipsec and L2TP protocols for VPN.

Looking throug the ubuntu docs it looks like the available clients are OpenVPN, PPTP and VPNC (Cisco).   Does anyone know if any of those clients will work?   I'd rather run my VPN off the router than have to set up an OpenVPN server.

Thanks!
Doc

---

### Post by tomearp on 2014-03-26
From reading the relevant section of the [user guide for the usg 50]("ftp://ftp2.zyxel.com/ZyWALL_USG_50/user_guide/ZyWALL%20USG%2050_v3-00_Ed2.pdf#page69") I think it should be possible to connect from Ubuntu. Page 79 onwards describes how to configure it for L2TP/IPsec operation.

There are no client configuration instructions for Ubuntu/Linux explicitly but I don't imagine it will be difficult to set up, you'll need the IPsec pre-shared key and a valid username/password.
[This page]("https://my.hostvpn.com/knowledgebase/11/L2TPorIPSec-Connection-from-Ubuntu-Desktop-1204.html") describes some software you can use to handle L2TP connections. The instructions are for 12.04. I have not tested them. (personally, I use [SoftEther]("https://www.softether.org/") VPN server as it supports L2TP, MS-SSTP, OpenVPN and SSL-VPN clients which covers most things)

---

