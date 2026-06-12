---
title: "[SOLVED] Internet /vision net 709 adsl modem"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by Lemmyaraya on 2008-01-08
I am unable to connect to the internet through my vision net adsl 709 modem. It works fine with windows, I have tried Ubuntu 7.10, PCLinusOS, Madrivia, Fedora, and OpenSuSE. Using the live cds, except for Ubuntu, in which I did a real install. Replacing SuSE 9.0, which did not connect to the internet either. I have tried with three different computers, and it also went through two seperate routers, a trendnet and linksys routers, using both wired and wireless. I can share files, and see all other computers on the net work, access both routers, and access the modem, but still no connection to the internet with error messages of timing out or saying that there is no connection. 

It is a dsl connection with a static ip, no ppoe (?), no user name no password. It is always on. All networking works, I am able to ping all routers and the modem, and make changes to the modem and router settings.

Any assistance would be greatly appreciated.

---

### Post by Theo Venter on 2008-01-08
Join the club!!!!
I have the same dilema!
I've had some help this morning but then had go slave again. I'm now waiting for them to reply again. If I find something I will pass it on

---

### Post by Lemmyaraya on 2008-01-10
I was able to connect to internet With DSlinux live cd but am still unable to connect with Ubuntu.
This is on the same machine.  Dose anyone know what is different in how they connect?
All other networking still functions .

---

### Post by Lemmyaraya on 2008-02-29
Found problem in DNS listing 
default setting was setting dns to router ip address (gateway)  
DNS servers were listed in ADSL routers WAN table
Switched the DNS to the 2 listed in modem and boom we have internet

---

