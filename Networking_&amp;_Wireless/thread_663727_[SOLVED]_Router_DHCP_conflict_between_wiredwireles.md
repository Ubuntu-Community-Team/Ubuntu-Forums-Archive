---
title: "[SOLVED] Router DHCP conflict between wired/wireless laptop connections"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by colgt on 2008-01-10
Hello everyone - been an Ubuntu user for about a year now on my PC's, but used Linux at Uni for around 3 years on and off.  I have always found lots of answers to problems on these forums but this is the first time nobody else has had/solved the problem I had so I decided to register.  Just wanted to say that these forums are priceless in the help they've given me, and let's hope it's the same for this problem!

I have a Netgear wireless router and Gutsy 32bit laptop/desktop installs.  Each has samba/winbind installed and the /etc/nsswitch.conf set to resolve hosts using the order 'files wins...' and is set to use wins in /etc/samba/smb.conf.  The desktop uses a wired, static ip whereas the laptop uses nm-applet to get dynamic ip addresses.  I connect the laptop to the router via wired and wireless depending on what I have to do. 

Presuming the router has been powered down and all dhcp leases cleared, if I connect via wireless then I get an IP address assigned to the MAC address of the wireless nic and can go about my business ie. ping the desktop by name etc.  If I then connect via wired nic then that also gets an IP address assigned but I cannot resolve the desktop by hostname as the router has two dhcp leases for the laptop.  The first of these leases becomes a problem somewhere along the line (I know this because if I ping the desktop by ip I get details that the the first ip assigned to the laptop is unreachable for a reply - even though I pinged from the other ip).

This did not appear a problem with Feisty, but if I can't do anything about it, is there any kind of trick I can use to get the laptop to have an alias for both the wireless and wired nic's?  It seems that the problem is the desktop is responding to requests to the wrong ip for the laptop.

Thanks for any help you can give me!

---

### Post by colgt on 2008-01-27
Any help on this out there?

---

