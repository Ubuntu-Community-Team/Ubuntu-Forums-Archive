---
title: "Static IP Interface file different than others"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by SailBlue5 on 2008-10-07
Hi, I looked online to see how to set a static IP on ubuntu (Hardy Heroin) and I see people saying that the interfaces file would look like this

auto eth0
iface eth0 inet dhcp

for dchp, but mine looks like

auto lo
iface lo inet loopback

So I am unsure how to change the file, since the file is different than what everyone on the web says it would be before I change it.

Thanks
Michael

---

### Post by willca on 2008-10-08
Edit /etc/network/interfaces

auto eth0
iface eth0 inet static
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x

Save and restart networking.

sudo /etc/init.d/networking restart

For example.

iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.254

---

### Post by willca on 2008-10-08
oh forgot...if you need dns...then you need to edit /etc/resolv.conf

as such it looks like..

search whateverdomain.com
nameserver x.x.x.x
nameserver x.x.x.x

---

### Post by SailBlue5 on 2008-10-08
Thanks for the help. Just so I understand, what was the stuff I originally had doing? It was:
auto lo
iface lo inet loopback 

Thanks

---

### Post by Iowan on 2008-10-08
> **SailBlue5 said:**
> Thanks for the help. Just so I understand, what was the stuff I originally had doing? It was:
auto lo
iface lo inet loopback 

Thanks
You still need that - don't take it out... "lo" is the loopback device (the "loopback" on the iface line is a dead giveaway :) ) which is used internally by the system.

---

