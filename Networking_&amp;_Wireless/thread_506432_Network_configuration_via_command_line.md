---
title: "Network configuration via command line?"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by grenadier32 on 2007-07-21
So, I use wireless a lot--Ndiswrapper works wonderfully. The thing is, network-admin doesn't interface well with it, and I'm interested in using the command line for more things anyway. So are there bash programs and commands to do the following tasks:

[LIST]
[*]Scan for wireless networks and indicate strength;
[*]Set ESSID; (Yes, you can do this by editing /etc/network/interfaces, but is there a simple command for it?)
[*]Disable a network connection (as in the Network Configuration program), and enable a different one?
[/LIST]

Thanks in advance.

---

### Post by xSauronx on 2007-07-21
> **grenadier32 said:**
> So, I use wireless a lot--Ndiswrapper works wonderfully. The thing is, network-admin doesn't interface well with it, and I'm interested in using the command line for more things anyway. So are there bash programs and commands to do the following tasks:

[LIST]
[*]Scan for wireless networks and indicate strength;
[*]Set ESSID; (Yes, you can do this by editing /etc/network/interfaces, but is there a simple command for it?)
[*]Disable a network connection (as in the Network Configuration program), and enable a different one?
[/LIST]

Thanks in advance.

to scan wireless networks:

iwlist ethX scanning


this will return whatever APs you can see, with, iirc, a MAC address and signal strength, and indication of security. 

to set ESSID:

iwconfig ethX essid $ESSIDNAME

im not sure, however, that this alone is going to take a dhcp lease as ive never tried it. use

man iwconfig

to get more wireless commands :)

to disable a network interface:

ifdown ethX

then to bring one up

ifup ethX

bringing it up like this will, i believe, cause it to seek a DHCP lease, to bring it up with a static ip i believe the following is what you need:

ifconfig ethX x.x.x.x netmask x.x.x.x up 

where the first set of octets are the IP address, and the second is the network mask

fortunately, my wireless works with the network manager but that should do to get you started

---

### Post by grenadier32 on 2007-07-23
Many thanks, that was exactly what I needed. :)

---

