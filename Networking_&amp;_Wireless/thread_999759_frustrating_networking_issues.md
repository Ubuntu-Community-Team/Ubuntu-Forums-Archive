---
title: "frustrating networking issues"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by redgsturbo on 2008-12-02
k... computer goes like this

internet<---------(eth1)->desktop<-(eth0)------------(eth0)->laptop
                    |                 |                 | 
                   dhcp              192.168.0.1       dhcp

desktop masquerades for the laptop.  everytime I plug in the laptop, networkmanager brings eth0 on the desktop back up (good), but the adds a default route of 192.168.0.1 (bad).  So I have 2 default routes at the point and nothing routes anywhere.  I keep having to manually remove that route to get connectivity back together.  how do I make network manager stop doing that?

---

### Post by superprash2003 on 2008-12-02
have you configured the interface in the /etc/network/interfaces file??explicitly mention the default route.

---

### Post by redgsturbo on 2008-12-03
> **superprash2003 said:**
> have you configured the interface in the /etc/network/interfaces file??explicitly mention the default route.

I've tried a number of things.  Currently interfaces looks like this:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
	address 192.168.0.1
	netmask 255.255.255.0

This however, kills network manager which now shows no managed devices and no connectivity.  Since I'm posting here thats incorrect.  I'd like networkmanager to function properly (trying to set the static IP on eth0 and dhcp on eth1 in networkmanager is what caused the routing issues.) but that didn't work either.  How does interfaces AND networkmanager supposed to be configured?

---

### Post by superprash2003 on 2008-12-03
this should give you an idea on what you have to put on the /etc/network/interfaces file [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

### Post by redgsturbo on 2008-12-03
> **superprash2003 said:**
> this should give you an idea on what you have to put on the /etc/network/interfaces file [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

well I've got networking working properly through /etc/network/interfaces... it doesn't even add routes when 192.168.0.1 (eth0) comes up and down when my laptop is unplugged.  Still though, network manager shows no active connections.  Is it not possible to get network manager to play nice?

---

### Post by superprash2003 on 2008-12-03
well there were problems initially with the 8.10 network manager, im not too sure if they have been sorted out.. have you updated?

---

### Post by redgsturbo on 2008-12-03
> **superprash2003 said:**
> well there were problems initially with the 8.10 network manager, im not too sure if they have been sorted out.. have you updated?

Yup.  All the way up to date

---

