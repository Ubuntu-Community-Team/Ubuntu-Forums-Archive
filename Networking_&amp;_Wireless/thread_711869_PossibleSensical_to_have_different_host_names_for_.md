---
title: "Possible/Sensical to have different host names for different eth devices?"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by Meson on 2008-03-01
I've got a device eth0 and eth1 (lan and wlan).  Does it make sense to try and have different host names for each device?  How do I it?

---

### Post by Mr. C. on 2008-03-01
> **Meson said:**
> I've got a device eth0 and eth1 (lan and wlan).  Does it make sense to try and have different host names for each device?  How do I it?

This question is a little complex to answer without some background.  In a nut shell, interfaces do not have host names.  Rather, there are services that map hostnames to IP addresses (and vice versa).  Using these services allows one to connect to a particular address via usage of a host name.  So host names are really only useful in this context for other systems on either of your networks to be able to address your machine via host name.

Assume:
Your eth0 network, say has network 10.0.0.0/24, and the dual-interface system's eth0 IP address is 10.0.0.1.

Your wlan0 network, say has network 192.168.0.0/24, and the dual-interface system's wlan0 IP address is 192.168.0.1.

Let's give them names:
host1_net10    10.0.0.1
host1_net192  192.168.0.1

Now, other systems on the 10.0.0.0/24 network could communicate with your system by using the host name assigned to the 10.0.0.1 IP address (host1_net10).  And likewise, wlan0 systems on the 192.168.0.0/24 network could talk to your system by using the host name assigned to the192.168.0.1 IP address (host1_net192). 

It doesn't make sense to have a system on the 10.0.0.1 network try to communicate with your dual-nic system by using the host name assigned to 192.168.0.1 (host1_net192), because it can't directly talk to it, and serves no real purpose.  That host is really interested in talking to your *system*.  So as such, it is sufficient for each host on those networks to use the host name designated for the interface they are directly connected to.

The final issue is getting those host names assigned, available, and in use by all the other systems.  And this is a job for mass updates of /etc/hosts, and/or DNS, and/or other naming service.

Helps?

---

### Post by Meson on 2008-03-01
Helps a little, but you're assuming that each device is part of a different network, which is not the case. 

They are both on a 192.168.0.0/16.  The advantage to me would be that I could force other computers to look for say, file sharing, only ove the wired connection.  

Also, my router has static DHCP reservations which require a host/mac/ip combo, and none of them can be repeated.  So with my laptop, I can't have a static entry for each nic without assigning a different hostnam to each nic.

---

