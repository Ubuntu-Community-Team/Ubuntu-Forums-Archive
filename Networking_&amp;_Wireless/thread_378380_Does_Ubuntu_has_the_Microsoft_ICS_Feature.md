---
title: "Does Ubuntu has the Microsoft ICS Feature?"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by stroker on 2007-03-07
I've not yet installed Ubuntu because i dont know if this OS can share two DSL connections without purchasing a router. Microsoft ICS f(internet connection sharing) feature enables me to share my connection to another computer without using a router. sharing another connection just needs an additional NIC connected to the pci slot.

Is it possible? if it is, can you give me a step-by-step instructions.

Thanks for the help in advance!

---

### Post by louis_nichols on 2007-03-07
First of all, ICS is by no means a Microsoft feature. Microsoft makes in fact some of the worst products when it comes to anything related to networking. Then, of course it is possible! And pretty easy, too.

First, you need to install 2 packages: **dhcp3-server **and **firestarter**. Then, go to System>Administration>Networking and configure the card connected to LAN to use IP number 192.168.0.1 and default netmask.

Next, you go to System>Administration>Firestarter and follow the first run wizard, making sure to check the option "Share internet connection" and correctly choose which network card is connected to the internet and which to your home LAN. Also check the option "enable dhcp for local network" and leave the default settings there.

Next step is to open a terminal window and execute this command:

```
sudo /etc/init.d/dhcp3-server start
```

And... this should be all. The only thing is that you might need to configure dhcp3-server to run automatically at startup, but I think that is the default setting, so you might not need to do anything in fact.

---

