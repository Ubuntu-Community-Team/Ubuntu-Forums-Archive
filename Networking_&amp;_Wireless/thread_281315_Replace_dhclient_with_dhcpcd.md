---
title: "Replace dhclient with dhcpcd"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by abc1987 on 2006-10-20
Hi there,

I have my Ubuntu Dapper machine connected to a university network via Ethernet providing a direct internet connection which is managed using DHCP. Unfortunately dhclient won't work with the network due to it requesting an IPv6 alias which the router won't provide, the DHCP server only issues IPv4. I have installed dhcpcd which does work, but I have to start it manually since Ubuntu seemingly won't simply replace dhclient with it. Setting static IPs is not an option since the IP isn't fixed. Could someone please tell me how I can configure Ubuntu to use dhcpcd all the time instead of dhclient so I can get rid of this problem? I have a friend with Debian Etch who has been able to get dhcpcd working simply by installing it - but this doesn't seem to happen with Dapper :( 
I've already tried editing /etc/init.d/networking and got nowhere.

Please help. Thank you,

Alastair

---

### Post by abc1987 on 2006-10-21
Oops - I was very sleepy when I made this post. I'm not actually running Dapper, I'm running Edgy, but the problem was the same when I had Dapper so I don't think it makes any difference!!

---

### Post by Balabare on 2006-10-27
Hi everybody,

I have exactly the same problem as abc1987 on kubuntu Edgy.

Please help us ! Thank you

---

