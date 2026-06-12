---
title: "Internet Connection Sharing - thru Dial-Up"
date: 2005-09-23
forum: Networking &amp; Wireless
---

### Post by oragon on 2005-09-23
im new to linux, esp. netowrking. please allow me to post a question with regards of internet connection sharing on ubuntu linux, specifically to sharing a dial-up (as opposed to a broadband) connection appears to be rather old... but this is my real situations. im planning to assign one of my ubuntu linux for dial-up. and the rest of 5 for worskations. Can you please give me a guide what to configure, install such services? I really appreciate your help!

i will fully appreciate any support!

Thanks!

---

### Post by cwaldbieser on 2005-09-24
[QUOTE=oragon]im new to linux, esp. netowrking. please allow me to post a question with regards of internet connection sharing on ubuntu linux, specifically to sharing a dial-up (as opposed to a broadband) connection appears to be rather old... but this is my real situations. im planning to assign one of my ubuntu linux for dial-up. and the rest of 5 for worskations. Can you please give me a guide what to configure, install such services? I really appreciate your help!

i will fully appreciate any support!

Thanks![/QUOTE]
I would think that it would essentially be the same as connection sharing with broadband.  The instead of routing Internet traffic to eth0, it would go to ppp0, or whatever your devices happen to be named.

---

### Post by oragon on 2005-09-24
thanks for the info! do i have to set proxy for that?

---

### Post by cwaldbieser on 2005-09-25
[QUOTE=oragon]thanks for the info! do i have to set proxy for that?[/QUOTE]
I don't think you need to use a proxy.  Just set your other computers to use the Ubuntu computer as the default gateway.  You will probably have to do some sort of network address translation.  You can configure this manually with iptables or use a nice firewall front-end.  And IP forwarding will have to be enabled.  If you have questions about any of those areas, feel free to ask.  There are probably lots of old entries in this forum about NAT and Internet connection sharing, too.

---

### Post by Matchless on 2005-09-25
Hi,
    Use Firestarter firewall on the server, make sure you setup and go on the internet with your modem. run the Firestarter setup wizard which as internet connection sharing in it, make sure you add your ISP DNS IP's as well and it should work.
Regards
Matchless

---

### Post by robert_pectol on 2005-09-26
This Internet Connection Sharing How-To for Ubuntu might help:
[http://rob.pectol.com/content/view/5/28/](http://rob.pectol.com/content/view/5/28/)

Good luck!

---

