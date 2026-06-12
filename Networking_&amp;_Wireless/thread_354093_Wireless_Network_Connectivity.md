---
title: "Wireless Network Connectivity"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by brandoncolorado on 2007-02-05
Hey everyone,

I am not sure if this is a hardware issue or something within Ubuntu or bios that needs adjusted.  I have called technical support many times, and every time they tell me to reinstall drivers.

Problem - Wireless disconnects, connects, disconnects, connects.  This happens at my school where the whole building is wireless.  There are many people around me, many with same brand and even model laptops without the problem.  In Ubuntu, I can usually fix the problem temporarily by right click on network-manager and turning off wireless, then turning it back on.    My network signal strength is pinned at 30% in ubuntu because of a bug.

Is there anything I could try, I really need my wireless for class.

---

### Post by jml on 2007-02-05
A bit more information would be helpful.  

What version of Ubuntu are you using?
What laptop brand and model are you using?
What is the chipset for your computers wireless card?
Is the network you are trying to connect to use encryption?  If yes, what type, WEP,WPA, WPA2?

These answers make help someone point you in the right direction.

Joe

---

### Post by brandoncolorado on 2007-02-05
> **jml said:**
> A bit more information would be helpful.  

What version of Ubuntu are you using?
What laptop brand and model are you using?
What is the chipset for your computers wireless card?
Is the network you are trying to connect to use encryption?  If yes, what type, WEP,WPA, WPA2?

These answers make help someone point you in the right direction.

Joe

Version Edgy Eft 6.10
Gateway MX 3414
Realtek RTL8185 54m Wireless
The network allows anyone to connect, but then when you open a browser, we have to log in.

---

### Post by timlewis242 on 2007-02-06
I have the same problem, in fact I posted a message for assistance in getting my Reaktek card to renew it's IP address. I assumed the problem was that when I shut down the pc, the card was trying to use the same IP address as another computer and could not connect. The only way to make it connect was as you say, disconnect and reconnect or change the IP address (I switched all of my pc's to static addresses) manually and reconnect. However, now I believe the problem to be the driver that Ubuntu uses when it detects the card. I think it has to forced to reconfigure itself after each session in order to connect. It's probably the same driver that is keeping the connection at 30%.

I have tried NDIS Wrapper for this card and it simply will not work with the windows driver. It reports back that it's an invalid driver. I tried to download and install the Linux version of the Realtek driver but can't get it to load after I build it and can't seem to uninstall the current driver, which I suspect is keeping me from installing the built one. If you figure it out let me know. It sucks having to restart the card every time you power down and want to connect but so far nothing else has worked.

---

### Post by brandoncolorado on 2007-02-14
bump

---

