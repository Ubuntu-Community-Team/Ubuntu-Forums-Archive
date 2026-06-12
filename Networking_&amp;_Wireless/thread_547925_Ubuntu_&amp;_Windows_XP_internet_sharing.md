---
title: "Ubuntu &amp; Windows XP internet sharing"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by TheAixtase on 2007-09-10
Hello All!

I am the happy owner of a laptop on which I have installed Ubuntu. However I have a problem upon trying to connect to the internet.

I have a tower which runs on XP and is connected to the internet. On my motherboard I have two ethernet sockets. One is conected to the internet (DSL Modem) and the other I have used to conect to my laptop.

Ubuntu recognises a network but it stops there. I would like to know how I could get internet out of my tower and on to my Ubuntu laptop. Also, what can I do when "connected" to the linux-windows network?

Thanks in advance for any help :popcorn:

Ed

---

### Post by KCPokes on 2007-09-10
You'd be better served to buy a standard router/firewall from Linksys, D-Link, Netgear, etc...  You can do it the way you are asking, but in order to connect the two machines directly you will need to buy/build a crossover cable, for starters.

---

### Post by TheAixtase on 2007-09-10
I've linked them up with a crossover cable already

---

### Post by KCPokes on 2007-09-10
You may want to look at ICS...

[http://www.microsoft.com/windowsxp/using/networking/expert/crawford_02july01.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/crawford_02july01.mspx)
[http://www.practicallynetworked.com/sharing/xp_ics/](http://www.practicallynetworked.com/sharing/xp_ics/)

Think that is going to be your easiest option.

---

### Post by Anteaus on 2007-09-10
Yep, ICS should work provided the Ubuntu box is set to use  DHCP (auto network config) - the implementation of ICS is basically a simple NAT router, BUT unlike a fullspec router, it can only work within one fixed subnet on the host computer. 

HST, at the price they are today, buy a router and gain some peace of mind from the fact that you have a hardware firewall between the evil hobgoblins out there and that vulnerable Windows box!

With a route,  best to turn off ICS and use the router's DHCP. Or, assign fixed IPs, whichever suits your purposes better.

---

### Post by TheAixtase on 2007-09-10
thanks a lot, KCPokes! You made my day!
Your help couldn't be any simpler and effective!
Thanks again

Ed

---

