---
title: "Bridging 2 wired network connections"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by harrisony on 2007-11-27
(I know this is possible since I did it last night but forgot how and it was hacked up badly)

Currently I have my main computer and my PS3.
my current setup is

Modem <=> Desktop
and 
PS3 <=> Nothing 
The setup i want is
Modem <=> desktop and for the ps3 to get Internet

The desktop has its onboard LAN and a PCI card I found in the street and the ps3 has one port.
Last night I was playing around with dnsmasq, firestarters Internet connection sharing and these 2 pages
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router) [https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

any help is :D

---

### Post by mellowd on 2007-11-27
I'm a bit confused. Essentially you want the modem connected to the desktop, and then the ps3 connected to the desktop with internet access. Is that right? 

What kind of modem do you have? What other network devices do you have?

---

### Post by elctb on 2007-11-27
Haven't done it in while.  Try this command and see if it works:

```
sudo echo 1 > /proc/sys/net/ipv4/conf/all/forwarding
```

---

### Post by harrisony on 2007-11-27
> **mellowd said:**
> I'm a bit confused. Essentially you want the modem connected to the desktop, and then the ps3 connected to the desktop with internet access. Is that right? 

What kind of modem do you have? What other network devices do you have?
Correct

the modem is a 
Navini Ripwave Modem ("Rabbit") (ethernet)

the onboard lan is a
Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

and the PCI network card is a 
(I just unplugged it so i cant get the exact details but it says on it) Netgear FA310TX

As I said, it was working all last night although I have no idea how I did it

---

