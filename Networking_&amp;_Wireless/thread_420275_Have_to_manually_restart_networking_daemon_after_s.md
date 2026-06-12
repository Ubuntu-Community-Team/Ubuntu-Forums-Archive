---
title: "Have to manually restart networking daemon after startup"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-04-23
I previously was managing my wireless connection through Kubuntu with the Knetworkmanager.  Over the weekend I changed the /etc/network/interfaces file manually to accomodate a wpa2 encrypted connection with a static IP address.  

Everything works however I notice after starting up computer, the knetworkmanager applet appears stating manual configuration, however I need at the command line to restart the networking daemon 
sudo /etc/init.d/networking restart 
in order to access the internet.  Before making the manual configuration the connection would just work at startup.  

What do I have to do to prevent restarting the daemon at startup to gain an internet connection?

---

