---
title: "VPNC configuration for &quot;ipsec over udp&quot;"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by mad_cow on 2007-11-16
Hi i want to connect to cisco vpn server.

I tried the Cisco VPN client (latest 4.8.01) but it doesnt work. I manage to connect, but no data is sent.
I also tried the vpnc which results in the same problem.

I believe the porblem lies in "ipsec over tcp" which should be enabled. In the cisco vpnclient: if I select it, it doesn't connect. If I do not select it, it connect, but no data is sent.

In vpnc I cannot select ipsec over tcp, but it does connect, but as i said no data is sent.

In windows I also use the cisco vpn client which works both for "ipsec over tcp" and "ipsec over udp".

Therefor I want to try vpnc with the option "ipsec over udp", which I believe should be possible since it is implementen since version 0.3.

The onlyquestion I have is: how do I enable it? I cant find instruction on how to enable it in the .conf file. (or rthrough the GUI)

---

### Post by mad_cow on 2007-11-21
anyone? please

---

### Post by dthomasdigital on 2007-11-21
I'm connecting to a pix with vpnc I might can help

---

