---
title: "Sharing a connection from Ubuntu w/ wireless (newbie)"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by wordsmythe on 2006-09-11
Ok, so on recommendation I picked up a Netgear WG311T because it's supposed to work well with MadWiFi--though I'm not sure what MadWiFi is.  I opened the box and put the card in.  That's as far as I got.  

I only have one IP number from my ISP, and I was hoping to get a network going where 2 XP machines can get on the internet through this Ubuntu box.  Can someone lay this out for me--in idiot terms?

---

### Post by spd106 on 2006-09-12
Dapper (and Edgy) have the madwifi drivers that allow you to use the card in normal infrastructure or station mode. But you want to use either AP oe Adhoc mode. To do this you will need to compile madwifi-ng from source. This page will tell you how to do it [https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi).

To allow you to provide Internet access you will need to enable packet forwarding, through iptables or maybe a gui such as firestarter or smoothwall.

If you want to provide addresses to the other PCs then you will need to set up a dhcp server.

You might also be able to configure hostap or some other means of providing stronger authentication/encryption.

---

