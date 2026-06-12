---
title: "HELP with Wireless Issue"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by san2004 on 2007-11-18
I have installed Ubuntu 7.10 dual booting with Win XP in a laptop with Intel PRO 3945ABG Network Card. I connect to the internet through a wireless  ADSL modem.  But the computer fails to connect to the network in Ubuntu (pppoeconf could not find access cconcentrator). 

It connects in Windows environment.
The network status in the Windows environment shows
 Network Name : WA1003A
Band       : 801.11g/
Authentcation Level : Open
Data Encryption : None

The network card driver installed out of box and shows as restricted driver. Inspite of that I also intalled the Windows XP driver through ndiswrapper. Still the mahine could not see the network. After I installed wlassistant the machine could see the network but could not connect.

Th funny thing is the machine connects to the wireless modem through live ubuntu CD 7.10 seamlessly without any prodding.

It seems I am missing something silly. 

Please help me and thanks in advance.

---

### Post by Blutack on 2007-11-18
pppoeconf?  Where did that error come from exactly please?  And how are you attempting to connect?

---

### Post by san2004 on 2007-11-18
I am sorry. I think I rushed through my last post. I connect to the internet through a ASDL modem with a username and password. After the  wireless link is established, I use pppoeconf to set up the internet connection.

pppoeconf after initialization searches for valid connection and reports the error if it cannot find any connections.

I hope I have been able to explain the problem.

Thanks.

---

