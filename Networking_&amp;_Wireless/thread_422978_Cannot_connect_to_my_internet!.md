---
title: "Cannot connect to my internet?!"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by cixelsid on 2007-04-25
I have an e-machines W3609 -- its pretty quick.. came with vista basic. I downloaded the cd and did the real install for Ubuntu but when i load the computer in Ubuntu i cant get it to connect to the internet, i dont think its reading my network card. Intel(R) PRO/100 VE Network Connection is all i can find as far as what card i have, but im new to the Linux thing, i have been on windows for about 10 years. =( plz help.

---

### Post by oedenfield on 2007-04-25
Open a terminal window and type this:

ifconfig

This is similar to the ipconfig command in Windows.  First make sure all of your TCP/IP settings are correct (IP address, gateway, DNS, etc).

---

### Post by stchman on 2007-04-25
> **cixelsid said:**
> I have an e-machines W3609 -- its pretty quick.. came with vista basic. I downloaded the cd and did the real install for Ubuntu but when i load the computer in Ubuntu i cant get it to connect to the internet, i dont think its reading my network card. Intel(R) PRO/100 VE Network Connection is all i can find as far as what card i have, but im new to the Linux thing, i have been on windows for about 10 years. =( plz help.

A few questions.

Are you connecting this machine to a router?
If yes is the router setup with DHCP?

That ethernet card should be supported by Ubuntu.

Open terminal and type:

---

### Post by cixelsid on 2007-04-25
Yes i am connecting thru a router. its a Belkin 2.4ghz 802.11g.  im not sure what DHCP is, its set up where my computer is plugged into the router, and my ps3 is connected to it wirelessly. This is the only actual computer that is connected, i have to reboot my computer to try the ipconfig suggestion on ubuntu, so i will brb, and the other guy didnt say what to type?

---

### Post by cixelsid on 2007-04-25
i also tried it with the computer pluged directly into the modem. if that matters, brb im loging into ubuntu

---

### Post by stchman on 2007-04-25
> **cixelsid said:**
> i also tried it with the computer pluged directly into the modem. if that matters, brb im loging into ubuntu

Go to Administrator--->Network and select your ethernet card and select either properties or configure.  You will need to place a check mark to enable it.  Select DHCP and that should do it.

---

### Post by oedenfield on 2007-04-25
> **cixelsid said:**
> Yes i am connecting thru a router. its a Belkin 2.4ghz 802.11g.  im not sure what DHCP is, its set up where my computer is plugged into the router, and my ps3 is connected to it wirelessly. This is the only actual computer that is connected, i have to reboot my computer to try the ipconfig suggestion on ubuntu, so i will brb, and the other guy didnt say what to type?

In ubuntu you will want to type ifconfig NOT ipconfig.

---

### Post by cixelsid on 2007-04-25
ok, i missed the if and ip part.. il go back to ubuntu- i also noticed at the top on ubunto theres no connection, and im pretty sure under admin>network> my ethernet isnt there.. il check right now to be sure..

---

### Post by cixelsid on 2007-04-25
yea, i just checked.. under admin.network my card doesnt show up. But i checked under hardware, and my card is listed there.. i took some SS's il try to have them on here.. any more suggestions?

---

### Post by oedenfield on 2007-04-25
Ok, ifconfig won't help if the system doesn't have eth0 (or ethX) running for your NIC.

---

### Post by cixelsid on 2007-04-25
ok, so now that we have reestablished that, what now?

---

