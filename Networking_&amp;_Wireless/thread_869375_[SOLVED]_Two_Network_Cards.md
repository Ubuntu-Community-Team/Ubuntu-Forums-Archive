---
title: "[SOLVED] Two Network Cards"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by MunkyJunky on 2008-07-24
I own an Acer Aspire NAS, and I'd like to be able to sue its full gigabit Ethernet capabilities, but my router wont support this, so I stuck one of my spare network cards into my machine and have tried fruitlessly for 3 hours to get it to work.

My NAS can be set up as a DHCP server, which is what I've been trying to get it to do, along with having a static IP. I can manage that, but when I plug it into my new NIC it stops working. I know the card is ok, I'm just getting SOMETHING wrong!

Here's basically what my network looks like:

Odin (My ubuntu PC)
 | etho ============== [ VANIR ] ===== | GATEWAY  (192.168.1.1)
 | 
 | eth1 ============== [ AESIR ] ===== | VALHALLA (192.168.0.1)


My machine is Odin, Valhalla is my NAS, Gateway is my router. Vanir is my home network domain name, and Aesir is what the NAS should be giving off. 

Valhalla is set to static IP 192.168.0.1, and set as a DHCP server. To set it as this, I have to have it as a DHCP client of GATEWAY, make the changes, and restart it, then plug it into my machine (which should produce AESIR). 

Basically, my problem is that this ISN'T working, and I cant see why not. In network settings, I've tried both connections on roaming mode, and DHCP client. Neither helped. 

If anyone has any insights into what I'm missing, I would be very grateful, because here is the only place I can think of getting any help!


EDIT:: I solved it, finally!

---

