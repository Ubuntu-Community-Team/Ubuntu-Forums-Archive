---
title: "Wireguard at home question"
date: 2020-07-18
forum: Networking &amp; Wireless
---

### Post by hecresper2171 on 2020-07-18
Hi,

I want to install and configure Wireguard at home, but I have one question that can't seem to find an answer to online:

If I setup a dedicated Wireguard box at home, can I use it for with my in-home clients?

Basically it would be like running my own VPN service at home.

That's it.  Thank you.

---

### Post by aboka on 2020-07-19
i hv the same question before, and i think it should work for both lan/wan. it should be easy if it is setup just to be use on either lan or wan, but if you want it to work for both, you need to have some 'special setup' like your firewall routing etc.

i hv try once to connect my lan pc to Raspberry Pi that runs OpenVPN, it can connect but no internet after that. probably the issue mention above. but i did not pursue as only intend to use the vpn to connect from outside.

good luck.

---

### Post by The Cog on 2020-07-19
Yes you can, although I would wonder why, if its all used within the home.

That said, I have a Wireguard server running on a pi at home. I use it primarily as a server for PCs in the house, so they can communicate encrypted even within the home network. I have no reason to do this other than to play and experiment with Wireguard. I do have my laptop configured so that it connects to that pi either in the house or from outside over the interent if I'm somewhere else with it. Mainly again just for experimenting, although the fact that the laptop "phones home" with a VPN might come in handy if the laptop is ever stolen.

I also have another wireguard VPN from my desktop and laptop to a rented cloud server which I use so I can get IPv6 connectivity to the internet, because my useless ISP (Virgin Media) has no idea how to provide IPv6 and probably won't before I retire.

Not sure if this answers your question because I'm not sure what in-home clients means. But I home it helps.

---

### Post by hecresper2171 on 2020-07-19
Thanks for replies.

After reading them, I came up with another way of asking this question by giving an example:

When someone signs up for a VPN service, it is usally not hosted at home and they can connect to it from anywhere: home, office, coffee shop, etc.

Is having Wireguard hosted in-home, the same as signing up for a VPN service?

Thanks guys.

---

### Post by uninvolved on 2020-07-19
In many ways, it will be similar. It won't have various end-points and your public IP address will be that of the server at your home. This negates a lot of the reasons people use an VPN for, but it still does allow you to encrypt all your traffic while doing things like using a public WiFi spot.

I have a VPN set up here at the house - but I just use it when I want it to look like I'm home. It's a long story. I also have a server that only accepts 'local' addresses and the VPN allows me to appear local even when I'm not home. This means I can stream my security cameras remotely without actually having put them on the public internet.

---

