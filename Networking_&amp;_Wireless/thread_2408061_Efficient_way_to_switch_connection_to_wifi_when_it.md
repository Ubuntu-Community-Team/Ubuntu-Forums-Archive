---
title: "Efficient way to switch connection to wifi when it is available"
date: 2018-12-13
forum: Networking &amp; Wireless
---

### Post by jimhce on 2018-12-13
I am implementing a network application running Ubuntu in a computer which has three network connections, Ethernet, Wifi and 3G, Ethernet takes the highest connection priority if it is available, the next is the WiFi and the next is the 3G, it is similar in mobile phone when WiFi is available, switch from 3G to Wifi immediately, does anyone know how it is implemented in mobile phone? What is the efficient and reliable way to have a smooth transition from different network connection without affecting TCP applications?

---

### Post by TheFu on 2018-12-13
It is not possible without using addon programs, because TCP connections are state-full. Any change to the IP would require a new TCP connection.

There was a standard called Mobile-IP a few years ago. I don't think it took off. [https://en.wikipedia.org/wiki/Mobile_IP](https://en.wikipedia.org/wiki/Mobile_IP)

When I needed this, using a VPN was suggested, but changing IPs was considered too much of a security risk for our needs and it was part of the VPN connection security.  We decided at the time it wasn't worth the risk.

However, there's a new alpha-level VPN being added to Linux, wireguard.  The connection setup is much, much, quicker than with other VPN options.  Wireguard is sub-second whereas openvpn is 8+ seconds to setup a new connection.  [https://arstechnica.com/gadgets/2018/08/wireguard-vpn-review-fast-connections-amaze-but-windows-support-needs-to-happen/](https://arstechnica.com/gadgets/2018/08/wireguard-vpn-review-fast-connections-amaze-but-windows-support-needs-to-happen/) is a hands-on article.

No idea about wireguard availability on mobile devices.

---

