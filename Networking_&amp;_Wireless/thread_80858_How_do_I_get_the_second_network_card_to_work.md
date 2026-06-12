---
title: "How do I get the second network card to work?"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by bit on 2005-10-23
Hi,
I am trying to make a firewall with ubuntu. Im very new to linux so I hope you can help me.

I install in server mode, because I dont want the windows system.

When I install ubuntu, he finds 2 NIC, and I select the one that I connect to the ADSL / Internet.

After install I can apt-get and surf Inet with lynx.

But ifconfig does not accept eth1. I only got eth0.

How can I tell ubuntu to use the second NIC also ?
The second NIC should be a static ip 192.168.0.1 for my home LAN.

I guess I shuld maybe edit /etc/network/interfaces, but I am not sure what to edit, and if that is the correct thing to do in the first place.

Thank you for any input you can give me.

---

### Post by spd106 on 2005-10-23
What does **lspci** show?
If both NIC's came up at installation, then both should be compatible with Ubuntu. 

Can you please post the interfaces file. It might be that it is missing an *auto eth1* line. Or maybe some other part is wrong.

---

### Post by bit on 2005-10-24
[QUOTE=spd106]What does **lspci** show?
If both NIC's came up at installation, then both should be compatible with Ubuntu. 

Can you please post the interfaces file. It might be that it is missing an *auto eth1* line. Or maybe some other part is wrong.[/QUOTE]

Yes the auto eth1 was missing.

Thank you.

---

