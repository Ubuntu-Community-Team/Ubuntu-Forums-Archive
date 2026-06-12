---
title: "Changing a network interface from eth1 to eth0"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Tanvir on 2008-04-28
Hello, Due to some software licensing restriction, I need to have eth0. In my computer I only have one network card installed. If I run the command ifconfig it shows eth1. No eth0 in there at all. My question is how I would rename eth1 to eth0 so that the ifconfig will show eth0 instead of eth1. 

Thanks

---

### Post by jetsam on 2008-04-28
Interface names are set in the file /etc/udev/rules.d/70-persistent-net.rules

You should be able to edit this file with sudo and a text editor, then change your interface from eth1 to eth0.  

It's strange that you have only one interface, and yet it isn't called eth0 already.  There may be another entry in your file for an older  and now missing network card that's using eth0.  If so, comment it out by adding a '#' sign to the beginning of the line.

Once you restart, you'll lose networking.  You'll need to reconfigure networking for the new interface name.

---

### Post by Tanvir on 2008-04-29
> **jetsam said:**
> Interface names are set in the file /etc/udev/rules.d/70-persistent-net.rules

You should be able to edit this file with sudo and a text editor, then change your interface from eth1 to eth0.  

It's strange that you have only one interface, and yet it isn't called eth0 already.  There may be another entry in your file for an older  and now missing network card that's using eth0.  If so, comment it out by adding a '#' sign to the beginning of the line.

Once you restart, you'll lose networking.  You'll need to reconfigure networking for the new interface name.

Thanks a lot. It worked and my software is now working perfectly. Thanks again.

---

