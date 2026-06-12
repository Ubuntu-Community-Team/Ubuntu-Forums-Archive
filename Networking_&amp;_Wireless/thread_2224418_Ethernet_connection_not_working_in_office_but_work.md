---
title: "Ethernet connection not working in office but working fine at office on ubuntu 12.04"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by ravindra-luv on 2014-05-16
Ethernet and wifi connection  is working properly at home but in office it shows "wired network disconnected you are now offline". In ethernet port is workign fine. If you want me to run anything please ask.
I am completely new to ubuntu12.04.

Any help in this regard will be highly appreciated.

---

### Post by Vladlenin5000 on 2014-05-16
Hi, welcome.

First things first: Are you allowed to use your own devices at your office? If not there's a good chance for the network to be looked down to MAC addresses and/or requiring certificates. As such, and knowing there's nothing wrong with your hardware or  OS - it works at home - you should ask your office's network administrator.

---

### Post by ravindra-luv on 2014-05-16
Actually two days back i was able to use it both on ethernet and wireless, but now it is not working. Ours is a small office and don't have efficient networking people, so any help will be reallly appreciated.

---

### Post by grahammechanical on 2014-05-16
This may help or it may not help.

At home you make a connection with the router by ethernet and Ubuntu's network manager recognises that connection. But in the office that connection is broken because you are using a different router with a different network address. So, the connect registered in network manager will not work.
 
There are two things you could try. 1) disable the home wired connection to the router from connecting automatically. 2) at the office set up a new connection to the office router but do not set it up to connect automatically.

You can try something similar with wireless (WiFi) connections. If we have network connections set to connect automatically we will get the "off-line" message if we load Ubuntu and are not connected to the router that Ubuntu is expecting to be connected to. With wireless we usually get a "networks available"  message if we are in range of any wireless access points and if Ubuntu cannot connect automatically to our wireless router as it expects to.

Regards.

---

