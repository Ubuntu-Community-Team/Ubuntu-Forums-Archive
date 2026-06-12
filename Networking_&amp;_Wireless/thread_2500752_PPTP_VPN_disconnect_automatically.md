---
title: "PPTP VPN disconnect automatically"
date: 2024-09-11
forum: Networking &amp; Wireless
---

### Post by sp3cter-is-noob on 2024-09-11
I have a provider to provide me with a PPTP VPN profile. In my Windows, I am having no problem connecting this pptp vpn.

As I am new to Ubuntu I tried almost all solutions but nothing worked. Please help me on this. Here is the log I find when use

Log Link - [https://paste.ubuntu.com/p/kSt9QCrrRd/](https://paste.ubuntu.com/p/kSt9QCrrRd/)

I have tried to change the /etc/ufw/before.rules
I have added those following lines in that file

# gre
-A ufw-before-input -p 47 -j ACCEPT
-A ufw-before-output -p 47 -j ACCEPT

I have also tried by disabling firewall still no effect. This issue was raised when I tried to reinstall ubuntu on the pc.

---

