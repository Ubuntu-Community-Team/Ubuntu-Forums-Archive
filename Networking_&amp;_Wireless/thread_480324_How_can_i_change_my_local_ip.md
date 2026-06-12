---
title: "How can i change my local ip?"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by Erdem on 2007-06-21
hey
i'm using ubuntu 7.04 server edition... and i dont have x on server pc...
my router give me ip 192.168.1.25 but i need to change that 192.168.1.100 (its local ip)

how can i do that?

thanks for helping...

---

### Post by Rui Pais on 2007-06-21
hi,
```
sudo nano /etc/network/interfaces
```
and change for:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1

assuming your router has the 192.168.1.1 ip

hth


edit: oops and assuming eth0 as your interface. (Change according yours :))

---

### Post by Erdem on 2007-06-21
thank u so much Rui Pais :D
it's working very well now::D

---

### Post by Rui Pais on 2007-06-21
:)
glad i could help.

---

