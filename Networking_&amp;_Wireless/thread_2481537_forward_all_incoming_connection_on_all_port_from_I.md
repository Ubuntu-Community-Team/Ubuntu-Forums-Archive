---
title: "forward all incoming connection on all port from IPV4 to IPV6"
date: 2022-12-02
forum: Networking &amp; Wireless
---

### Post by aliborhani on 2022-12-02
Hi
I Have VPS which only accept IPV6, and my internet provider support only IPV4, I think to rent another VPS with both IPV4 and IPV6 support, then I connect to this middle VPS and this forward my traffic to main VPS, is it possible? and how could I do this?
I want to transfer all traffic on all port except 22 (ssh port) both UDP and TCP protocol,
regards

---

### Post by The Cog on 2022-12-02
I think you should tell your internet provider that if they cannot provide access to the majority of the internet that you deserve a significant reduction in price they are charging for internet access. It probably won't help, but make your unhappiness known anyway. 
My ISP doesn't care at all, sadly. I don't think they can even spell IPv6, let alone deliver it.

There are a number of public tunnel brokers who provide full IPv6 internet access over an IPv4 tunnel to your PC - essentially a VPN that provides full IPV6 connectivity. The best known of these is Hurricane Electric [http://he.net/](http://he.net/) but I have recently started using route48 [https://www.route48.org/](https://www.route48.org/) and I'm very happy with them. You can google for "list of ipv6 tunnel brokers", but I couldn't find any really comprehensive-looking lists.

---

### Post by aliborhani on 2022-12-03
tnx but that is not my solution

---

