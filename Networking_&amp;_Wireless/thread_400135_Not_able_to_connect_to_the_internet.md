---
title: "Not able to connect to the internet"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by Abhi Kalyan on 2007-04-03
Hullo - SOS!!!
The problem:
Not able to connect to any sites from the browser, not able to send or receive mails.

Am able to ping to sites, using the Ip that i recive on ping if i paste it in the address bar, Am able to browse the Site, other Wise Am gone.

Ex: First I have to Ping Yahoo.com, Then i get an Ip 71.94.89.36,
I paste this number on my Firefox Adddress Bar and i can browse the site.
---------------------------------------------------------
My topography:
My system connects to this router through a LAN chord.
On my system i have two NIC's
eth0, eth1.
etho:
address 192.168.1.3, 255.255.255.0
gateway 192.168.1.1 ( the ip of the router)
dns-servers 192.168.1.1

eth1:
address 192.168.1.2, 255.255.255.0
----------------------------------------------------------
I have been comfortably sharing internet from this comp till a few days back.
I dont know all of a sudden out of the blue This has happened.
I have tried all installs, all distros.
But the problem doesnt go.

---------------------------------------------------
This happens only with linux on the windows system the internet is working like a dream.

Currently am forced to share internet usinf RAS on a windows 2003 server.
--------------------------------------------------------------

Please help or the whole project of shifting to Ubuntu might fall through the roof.


Please HELP!!!

---

### Post by Abhi Kalyan on 2007-04-04
The best Part is When i make the eth cards accept IP from a dhcp Address, The inetrnet works seamlesely.
This problem is stopping us form configuring ubuntu as the Internet server.
PLEASE HELP!!!

---

### Post by menacespb on 2007-04-04
This is quite obviously a dns issue, as you are able to reach the internet with ip adresses but can not make dns resolve properly. Basically, DNS should not be an adress on your local network.

Go to one of your windows systems, press the start menu -> run. In the box that appears, type cmd and press enter. This will give you a dos-like window. Type "ipconfig /all" and see what address appears in the DNS entry on the output you get there.

Good luck.

---

### Post by Abhi Kalyan on 2007-04-05
Thank you menacespb,
Did try what you asked on my internet sharing server.
The eth0 that is connected to the ADSL router given by my ISP gives the DNS as 192.168.1.1,
But thats it, it still does not work on my linux system, 
Am working on it will update as soon as i get some thing Going.
-------------------
Thank you a Lot for helping me out. Lookng forward for more interactions
Sincerely 
Abhi Kalyan

---

