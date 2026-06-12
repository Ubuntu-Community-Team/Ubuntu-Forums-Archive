---
title: "Two network cards (Internet)"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by sol4u1 on 2006-11-18
Hi All,

This is my first post in Ubuntu forums. I have installed Ubuntu 6.0.LTS in my PC. The PC initially had only one Network card (Eth0). I used to connect to internet on that card with DHCP. I had another Toshiba Laptop to which I would like to share my internet connection. I do not have a Router or Switch for the time being. So I installed another (Second) Network card in the PC and I would like to share internet on that card. However, I am unable to use the internet after installing 2nd Network card. But when I Deactivate the Second Network card in Network Tools, I can use the internet. Even the Default Gateway is Eth0. I  dont know why I am unable to get the default internet on the PC. I can see the data LED blinking on the 2nd card which makes me think that the PC is trying to findf internet on 2nd card. However, the internet connection is configured on 1st Card.

This is my first Experience with the Ubuntu Linux. I am a new bee.

I hope you will help me regarding the issue.

Thanks & Regards,

Solomon

---

### Post by scrooge_74 on 2006-11-18
I have a pc which has two cards.  The one connecting to internet is eth0 which gets IP from DSL provider using DHCP, the one for internal land is eth1 and I give it a stactic IP which has to be different from the one my ISP uses, I give it a 192.168.1.1, mask is 255.255.255.0, then I tell firestarted which one is connecting to the internet and which one is internal

then I instruct other pc to use as gateway my second card IP address, and i give that other pc an address like 192.168.1.2

I hope this can help you

---

### Post by sol4u1 on 2006-11-18
Hi,

Thanks for your reply. I got it, what I have done previously was I kept the Gateway for the Second card as its own IP address. That is I configured as IP: 10.0.0.1 and the Gateway 10.0.0.1. After removing the gateway. I can use my interne fine.

Thanks,
Solomon

---

### Post by scrooge_74 on 2006-11-18
Glad to hear you manage to resolve that issue, also learn how to use the ifup  and ifdown commands, that should be helpfull if you get into any troubles with your cards again

---

