---
title: "PPPoE Help"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by Jedakiah on 2007-04-06
I just built a new computer and installed kubuntu.  I'm trying to use it as a firewall/virus protection for my network.  

Previously I had a router that connected to the internet through PPPoE.  As a first step I'm  trying to setup kubuntu's internet access.  It is plugged directly into the modem.  I am incredibly new to linux & the command line but I still understand it pretty well.  

I have followed [these]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Dialup_PPP_Client_.28GNOME_PPP.29") steps.  I figured that gedit referred to the text editor so I replaced it with kate, and that gksudo should be replaced with kdesu.  Since I could not directly connect to the internet I skipped the first step.  

When I run 'pppoe-start' it will successfully connect with the following settings:

dns = server
firewall = masquerade 
demand activated = no

However konqueror will not connect to any web page.  I have also tried unpacking the rp-pppoe-3.8.tar.gz archive and install it the way the READ-ME.linux tells me to.  This doesn't work either.  My ethernet card is set on dhcp and my gateway is blank.

Please help, is there anything I can try?

---

### Post by Jedakiah on 2007-04-06
UPDATE: I verified that my ISP allows pings from windows.  I than pinged google 1000 times with no response in konsole.  I know that my computer is communicating with my ISP because a wrong password will not connect.  It seems to me that my inbound is blocked.  I don't know what that tells me though.  Please help.  It is urgent that I get this working.

---

### Post by Jedakiah on 2007-04-06
**Bump**

I'm sorry, I know you guys are very busy.  But if you could spare a few moments of your time it would be greatly appreciated.  I'm not doing this as a hobby, it is urgent that I get this business' network running the way it should.

---

