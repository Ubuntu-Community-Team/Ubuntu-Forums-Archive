---
title: "DHCP lease?"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by mattgaunt on 2007-01-10
Hey every1

Im having some problems connecting to my network at my university halls

My computer is giving me a DHCP lease, now i dont know what that is or what it means, so if anyone has any ideas of what to do to fix the problem then help would be greatly appreciated

Thanks alot

Matt

---

### Post by mattgaunt on 2007-01-10
this is what i get when i try dhclient eth0
> 
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted


This is my /etc/network/interfaces
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

auto eth0


---

### Post by maxamillion on 2007-01-10
```
sudo dhclient
```

---

### Post by mattgaunt on 2007-01-10
i hav tried that as well but doesnt seem to work so dnt kno what to do

---

### Post by koenn on 2007-01-10
> sudo dhclient  
> **mattgaunt said:**
> i hav tried that as well but doesnt seem to work 

what **_exactly_** do you get when you run ```
sudo dhclient
```

---

### Post by mattgaunt on 2007-01-11
I finally got it to work using sudo dhclient, i was using sudo dhclient eth0 and that when it didnt work.

But i have to do that everytime my computer reboots, is there anyway i can jus make it work from the start without having to type sudo dhclient???

Thanks for gettin it workin

---

### Post by maxamillion on 2007-01-11
Technically you could edit you /etc/init.d/networking script ... but I don't recommend it unless you are confident you know what you are doing poking around in that file.

---

### Post by mattgaunt on 2007-01-11
i was told by my university internet provider i could change my /etc/network/interfaces file, and i had changed that to change a wireless connection setting for my home network, so if you know what to add in that file to make it do sudo dhclient on start up that would be great but if you dont recommend it then ill stay well away

Thanks alot

---

### Post by koenn on 2007-01-11
your /etc/network/interfaces is says this ?
```
# The primary network interface
iface eth0 inet dhcp
auto eth0
```

Try changing the order - I not sure thatif it matters but usually it says something like
```

auto eth0
iface eth0 inet dhcp

```

---

### Post by koenn on 2007-01-11
is eth0 the network inteface you're having trouble with or do you have more than one ?
run```
 ifconfig
``` and post the output if you have no idea what i'm talking about.

---

