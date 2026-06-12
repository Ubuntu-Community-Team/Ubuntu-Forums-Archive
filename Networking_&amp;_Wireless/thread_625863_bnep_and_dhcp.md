---
title: "bnep and dhcp"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by Keps on 2007-11-28
hi!!
i have a little problem. 
for a project i have to connect two pc through bluetooth. So i have created the bnep0 on one pc (supposed the client) and a bnep0 connected to a pan0 on the other. it seems to work good.

but now i have to install dhcp on the server pc, so that , when the client connect to the server, the server assign automatically the ip to the client.
I installed dhcp3-server, i configured the /etc/default/dhcp3-server (INTERFACE="pan0") and /etc/dhcp3/dhcpd.conf.
The problem it's that the server assign the ip only one time, and other ten no...i don't know why.

I tried to use the dhcp server on eth0, and it works....

Some one knows why it work so few time?

i didn't write anything in /etc/network/interface on the client pc,...i have to write something?

thank to all...

gabriele

---

