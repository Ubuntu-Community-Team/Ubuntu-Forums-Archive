---
title: "Openvpn asking for socks password"
date: 2014-12-30
forum: Networking &amp; Wireless
---

### Post by amnesia2 on 2014-12-30
I'm having a nightmare setting up openvpn I've got as far as tcp connection made but it's now saying socks handshake failed no login details given for the proxy I'm behind there is no login details and I think this is a bug in openvpn there is a patch for this problem [https://github.com/OpenVPN/openvpn/blob/master/src/openvpn/socks.c#L194](https://github.com/OpenVPN/openvpn/blob/master/src/openvpn/socks.c#L194) but I don't know which file I'm supposed to apply this patch to?
[https://community.openvpn.net/openvpn/attachment/ticket/62/openvpn-socks-auth.patch](https://community.openvpn.net/openvpn/attachment/ticket/62/openvpn-socks-auth.patch)

---

### Post by slickymaster on 2015-01-05
*Moved to the ***Networking & Wireless*** sub-forum*

---

