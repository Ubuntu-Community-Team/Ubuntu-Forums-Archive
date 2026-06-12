---
title: "Setup L2TP VPN server on dedicated VM"
date: 2015-11-11
forum: Networking &amp; Wireless
---

### Post by smeerbartje on 2015-11-11
My situation: I have an Ubuntu server acting as my home router. It has two NICs and all the internal devices are using the server as their gateway. So far so good. On the server I have installed KVM and now my next step is to have a dedicated virtual machine running Ubuntu server as a L2TP VPN server. So when I'm abroad, I can connect to my external IP and IPTABLES forwards the traffic to the L2TP server running on an internal static IP.

This can be done, right? Or am I missing someting? I could use some help setting this up.

---

