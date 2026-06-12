---
title: "Help with wired network"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by Artorius on 2008-09-20
I cant get my Ethernet card to work with Ubuntu 6.01. What I'm looking for are the terminal commands to get my Ethernet card working. I have the card configured as eth0 and I'm using a dynamic ip address, but I cant connect to the Internet.  Any Help would be greatly appreciated.

---

### Post by blastus on 2008-09-20
Show detailed information about your network interfaces
```
ifconfig -a
```

If you see an IP address (inet addr) by the eth0 interface it means it has an IP address and should connect. However, if something has been reconfigured or changed on the other end of the connection such that the IP is no longer valid, you may have to release and renew (see below.)

Under Network Settings, if you uncheck Roaming Mode and set the configuration to DHCP you can use the following commands the bring down (release) and up (renew) the interface eth0

```
sudo ifdown eth0
sudo ifup eth0
```

When you bring up the interface it will tell you what you the IP address is and what the DNS (nameserver) is. If you are directly connected to a modem (and not to a router) this should be your Internet IP address and DNS of your ISP.

Do you have a router to test your network card with?

---

### Post by Artorius on 2008-09-21
Im trying to get my laptop to work with my parents home network,I need the wired conection so I can download the ndiswrapper and the driver files to get my wireless card to work. Yes they have a router on the network.

---

