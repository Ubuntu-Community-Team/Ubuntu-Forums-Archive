---
title: "network problems"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by drravshan on 2007-07-05
hi all,
i have a strange problem. i had put it up earlier in this forum but without much luck. am trying my luck again!
have a Win XP & ubuntu 7.04 dual booter. i used to use win xp earlier to connect to the internet using ADSL (HUAWEI). however after installing ubuntu, i couldnt connect to the net. then i queried this forum & got an useful link with the following advise
 
sudo if config eth0 up 192.168.1.2
sudo route add default gw 192.168.1.1
sudo vi /etc/resolv.conf

after that, i could connect to the internet using ubuntu, but since theniam now unable to connect to the net using Win XP!!
another problem - eveytime i boot with ubuntu, i need to enter the above mentioned commands to be able to connect to the net. 
pl help
ravi

---

### Post by sfarber53 on 2007-07-05
It sounds as though you have the system dual-booted (correct?).

You might try setting things up to use either a static IP address (the same for both) or, alternatively, use DHCP if it is available.

Actually, the best solution would be to put a router on your system (one that has dhcp).  That way, any machine that accesses the system using DHCP will automatically get an address for the new session.  My system at home is set-up that way for about 6 machines and no worries.

I recommend the Netgear routers that support 4 wired and wireless computers.  Excellent quality and reliability.

Cheers!

Steve

---

### Post by w4ett on 2007-07-27
In Xp Start>Run ipconfig to reset your DHCP address  Set the DHCP there. Try shutting down your computer and router/Modem, then restart your modem til it Synchronizes then restart your compter....try to resolve web addresses again

---

### Post by coffeecat on 2007-07-27
How are you connecting to the internet? Yes, I know you are using adsl, but are you using a modem/router? If so what make/model and are you connecting to it by ethernet cable or wireless.

Also - have you tried configuring your connection to use DHCP in both Ubuntu and Windows?

---

### Post by frodon on 2007-07-27
All duplicate threads merged, please do not open more than one thread for a support request.

---

