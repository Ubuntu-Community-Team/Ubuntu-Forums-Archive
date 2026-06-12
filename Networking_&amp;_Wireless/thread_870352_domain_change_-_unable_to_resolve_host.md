---
title: "domain change - unable to resolve host"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by sjbaugh on 2008-07-25
When I recently installed Ubuntu (Hardy Heron 64 bit) I took the default setting for host name and domain these were:
host: steve-desktop
domain: <blank>

I have since found that in order to get printing working correctly with my ethernet to USB print server (also used by Windows :( Machines) I have had to change the domain in:
System>Administration>Network>General
to MSHOME. I now have two problems:
1) I now get sudo: unable to resolve host steve-desktop. There is a setting for 127.0.1.1 for steve-desktop.MSHOME in Hosts (although no entry for steve-desktop without a domain name).
2) When I reboot the domain returns to blank, even though I created a Location and saved it and clicked the green tick.

How do I sort out my host resolution and how do I make the domain name change stick?

Thanks, Steve, England.

---

### Post by Iowan on 2008-07-25
You're most of the way there already.  Edit the line in **/etc/hosts** file to read ```
127.0.1.1 steve-desktop.MSHOME steve-desktop
```

---

### Post by sjbaugh on 2008-07-25
Iowan,

The Ubuntu is not fully with me yet! I have done what you suggested and I no longer get the unable to resolve host problem, but when I re-boot/restart my computer and look in Network Settings> General the domain keeps going back to blank and the print server has problems again. If I set it manually each time it's OK. I have created a Location called MSHOME that has the domain set and the extra host entry but I dont seem to be able to make it the default.

---

### Post by Iowan on 2008-07-25
If you're getting your IP address via DHCP, **/etc/dhcp3/dhclient.conf** has a **request** line that includes **domain-name**.  Your DHCP server might be resetting the domain.  You might try editing **domain-name,** out of the file (I'd make a backup first) and restarting networking.

---

### Post by sjbaugh on 2008-07-25
Thanks for your help, I don't know much about networking! I am using DHCP from my wireless router (Although this Linux machine is connected directly to it, not by WiFi). I have edited dhclient.conf as you suggested. I then went into:
System>Administration>Network and change the domain again and clicked on the hosts tab and changed this so that there was an entry:
127.0.1.1 steve-desktop.MSHOME steve-desktop
I then re-booted and the domain name was again blank and this time the Hosts entry was:
127.0.1.1 steve-desktop.MSHOME steve-desktop.MSHOME
I am getting confused about the differences between editing /etc/hosts and changing it in the Network Settings dialog box. I have found the file /etc/hostname and this contains:
steve-desktop
I don't know where the domain name I set in the Network Settings dialog box is stored to see if that is being set correctly. I supose that I could try to change the DHCP settings in the wireless router but I don't know what effect this will have on my XP Home machines. Thanks, Steve.

---

