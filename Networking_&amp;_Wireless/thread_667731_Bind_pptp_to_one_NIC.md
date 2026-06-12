---
title: "Bind pptp to one NIC"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by Gymnae on 2008-01-14
Hi,

I have small server at my flat with 2 NICs in it. I want one NIC to deal with all the Apache and SSH traffic via normal Internet accessed through a Router hooked up to a DSL Line. The 2nd NIC is only for  an VPN tunnel.
I tried it with Network Manager from Gnome via XFCE4 but Network Manager didn't work out so well and I mostly manage my Server via ssh shell, so I'd prefer a console approach. That's why I tried pptpconfig.

Now I want my successfully configured PPTP Tunnel to run only through eth1 - and no, I don't have iptables or so installed. 

Has anybody an idea?
All eth0 traffic should remain unaffected by the VPN tunnel. 

greetings,
gymnae

---

