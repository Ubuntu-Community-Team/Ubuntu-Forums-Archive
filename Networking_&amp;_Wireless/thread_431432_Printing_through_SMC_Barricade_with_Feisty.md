---
title: "Printing through SMC Barricade with Feisty"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by eringvo on 2007-05-03
I have now Feisty and its connected to my router SMC Barricade who has an printer connected.
When i run printer setup it can not find the printer automaticly. Then I try to connect as an network printer with Unix. I cant get it to print. The Icon for the printer is OK and "green" but nothing is happening. I set up the IP which is 192.168.2.1  When I ping i cant figure out that the printer has an  IP adress.
Is there anyone who has any idea ??

---

### Post by eringvo on 2007-05-03
Now i found out :
Printer has to be setup as UNIX printer and then URI: LPD/192.169.2.1/lpt1
All well and working good.

---

