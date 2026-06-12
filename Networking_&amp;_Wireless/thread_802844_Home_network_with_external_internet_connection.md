---
title: "Home network with external internet connection"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by botfish on 2008-05-21
I have a small home network setup using a D-Link ADSL modem/router. I have one computer running Ubuntu 8.04 desktop, and another running Ubuntu 8.04 server. Both computers connect to the internet and each other (ftp and http) through the D-Link router via Ethernet cable.

I want to cancel my ISP account. How do I connect to my friend’s router so I may use their internet connection? I don’t want to access my friend’s computer, just his internet. I prefer an Ethernet connection but may have to use wireless.

What hardware will I need? and will I need to install any software?

Thank for any suggestions.

---

### Post by superprash2003 on 2008-05-21
how far is your friend located from you?

---

### Post by botfish on 2008-05-21
My friend is in the next room (< 5m away).

---

### Post by Peter09 on 2008-05-22
Run a cable from a socket on your router / switch to a socket on his router switch. Thats most probably the simplest way. (after disconnecting your Internet Link)

PC

---

### Post by superprash2003 on 2008-05-22
yea peter09 is right.. i think laying a cable from his router to your router is easy and simple

---

### Post by botfish on 2008-05-22
Do I need a switch? or can I just connect my router to his router modem?

---

### Post by Peter09 on 2008-05-22
Most routers have an integral switch, that is, it should have more than one port to connect devices to.

PC

---

### Post by rickyjones on 2008-05-22
> **botfish said:**
> Do I need a switch? or can I just connect my router to his router modem?

Take a network cable and connect your router's WAN port to one of his LAN ports (on his router). Connect your router to his in the same manner that you would connect your router to your modem.

-Richard

---

### Post by Peter09 on 2008-05-22
Hang on.... this may depend on your router..... some routers have an integral modem and if so you cannot connect from what is a telephone line to his router.

For simplicity take a wire from one of the switch ports on your router (that is one of the ports where you connect you computer to) and put in in a similar port on his router/switch.

These ports are often number 1-4 or similar and will be in a line on hte front of your router, there is normally a light which will come on when active. 

If you have a problem the tel us the model number of you and your friends routers.

PC

---

### Post by Zafrusteria on 2008-05-22
Hi

As all the others have said run a cable. BUT one problem you may see if you were using DHCP from YOUR router and your friends router also has DHCP turned on ... see where this is going :-) You will need to turn off DHCP on your router and also make your friends router the default gateway. 

Also remember to change the DNS servers you had to the ones your friends ISP is providing. You will most likely not be able to use your old ISP DNS machines any more.

Have a look at the DNS from these guys it looks rather good :-)
[http://www.opendns.com/]("http://www.opendns.com/")

---

### Post by rickyjones on 2008-05-22
> **Peter09 said:**
> Hang on.... this may depend on your router..... some routers have an integral modem and if so you cannot connect from what is a telephone line to his router.

For simplicity take a wire from one of the switch ports on your router (that is one of the ports where you connect you computer to) and put in in a similar port on his router/switch.

These ports are often number 1-4 or similar and will be in a line on hte front of your router, there is normally a light which will come on when active. 

If you have a problem the tel us the model number of you and your friends routers.

PC

The OP did not mention an integrated modem. What you are suggesting is an alternative however he will need to disable HIS router's DHCP service. Connecting a LAN port to a LAN port, between routers, will mean that they will fight (DHCP services) unless one is disabled.

If his router is a standard router then connecting his WAN port to his friends LAN port would be the simplest and safest route to take.

Sincerely,
Richard

---

### Post by rickyjones on 2008-05-22
> **Zafrusteria said:**
> Hi

As all the others have said run a cable. BUT one problem you may see if you were using DHCP from YOUR router and your friends router also has DHCP turned on ... see where this is going :-) You will need to turn off DHCP on your router and also make your friends router the default gateway. 

Also remember to change the DNS servers you had to the ones your friends ISP is providing. You will most likely not be able to use your old ISP DNS machines any more.

Have a look at the DNS from these guys it looks rather good :-)
[http://www.opendns.com/]("http://www.opendns.com/")

He only needs to disable his DHCP service if he connects his LAN port to his friend's LAN port. If he connects his WAN port to his friends LAN port then the router will act exactly as if he was connected to a cable/dsl modem.

Thanks,
Richard

---

### Post by Peter09 on 2008-05-22
In his first post hey says

> I have a small home network setup using a D-Link ADSL modem/router. I have one computer running Ubuntu 8.04 desktop, and another running Ubuntu 8.04 server. Both computers connect to the internet and each other (ftp and http) through the D-Link router via Ethernet cable.

An ADSL modem/router will have a telephone socket to connect to the ISP. He will have no WAN connection.

PC

---

### Post by rickyjones on 2008-05-22
> **Peter09 said:**
> In his first post hey says



An ADSL modem/router will have a telephone socket to connect to the ISP. He will have no WAN connection.

PC

That depends on the model. I've seen some that also had a WAN port, you did not /have/ to use the integrated modem. Push comes to shove he could also purchase a new router, especially if his ISP is providing this current one.

Thanks,
Richard

---

### Post by Peter09 on 2008-05-22
Yep,
hey, lets see how he gets on, we could discuss this for hours and both be right / wrong. :)

PC

---

### Post by rickyjones on 2008-05-22
> **Peter09 said:**
> Yep,
hey, lets see how he gets on, we could discuss this for hours and both be right / wrong. :)

PC

Very true, I'm definitely not about to claim absolute certainty about assumptions :D

-Richard

---

### Post by botfish on 2008-05-22
Thanks everyone.

I do not have a WAN port. Only 4 LAN ports.

I will try a LAN to LAN connection. If that fails I will buy a router with a WAN port.

---

