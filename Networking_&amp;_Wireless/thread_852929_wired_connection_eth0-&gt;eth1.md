---
title: "wired connection eth0-&gt;eth1"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by markusr99208 on 2008-07-08
Good day,

I am using VMWare. The host machine has 2 NIC cards. NIC 1 is a USB device that basically creates a cell connection, this is where I get my IP address and internet connection and such. NIC 2 is connected to a router. (I don't even know if any of this is relevant).

In Ubuntu (first of all I configured the ubuntu LAPP on another computer and copied it to this computer) when it tries to get an IP address through DHCP I get an <UNKNOWN DEVICE>. So I went and did ifconfig -a and it looks like I want to use eth1.

So I edit /etc/network/interfaces and switch from eth0 to eth1 and restart the network and all appears to be happy. I can ping the other xp vm machine.

However, when I reboot ubuntu /etc/network/interfaces goes back to eth0. 

How do I make this change permanent?

---

### Post by markusr99208 on 2008-07-08
It actually says:

eth0: error fetching interface information: Device not found
eth0:3: error fetching interface information: Device not found
IP address for this Virtual Appliance is <UNDEFINED>
VA Management Condole can be accessed at https://<UNDFINED>:8000

...

-Markus

---

