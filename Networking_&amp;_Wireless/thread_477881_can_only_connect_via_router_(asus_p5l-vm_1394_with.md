---
title: "can only connect via router (asus p5l-vm 1394 with attansic L1 adapter)"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by whoop on 2007-06-18
I just installed Ubuntu 7.04 on my new machine (mobo:asus p5l-vm 1394). I could not get an internet connection although networkmanager applet indicated it was connected to a wired network. 
The mobo has an onboard Attansic L1 adapter which seems to be recognized out of the box. When i checked connection information on the networkmanager applet every entry (IP Address, Broadcast Addres etc.) accept mac address consisted of zeros (i.e. 0.0.0.0).

I used an old computer and a hub as a router and connected the new machine to it and it worked. Normal connection information and a working connection. 

As soon as I plug the UTP cable directly into my new machine a get to the non working state. Can anybody help me to get it working directly? I tried changing the configuration from Automatic configuration (DHCP) to Local Zeroconf network but this did not work. Why does this problem not occur on my old machine and in windowz ? I also tried Mandriva 2007.1, same problem

cheers.

---

### Post by whoop on 2007-06-19
Update: Once I got an internet connection via a router I put the cable directly into the new machine. once I rebooted the connection was lost again. I could be jumping to conclusions but it looks like I am not obtaining an ip address when i connect directly but once I get an ip address it seems to work. Still no idea how to connect directly. Please help.

---

### Post by whoop on 2007-06-21
Update: I figured out so far that the onboard network adapter is conflicting with my cable modem. I have solved the solution in windows by changing the Media Type from "auto" to "10Mbps Half Duplex". In ubuntu the problem still persists. So this should be an easy question now. How do I configure my nic to go at 10Mbps Half Duplex in ubuntu ?

---

### Post by jcliburn on 2007-06-22
I'm new to ubuntu, but this should work:

sudo ethtool -s eth0 speed 10 duplex half

---

### Post by whoop on 2007-09-03
I resolved the issue by returning my motherboard and changing it for an asus P5B... No more issues since then..

cheers...

---

