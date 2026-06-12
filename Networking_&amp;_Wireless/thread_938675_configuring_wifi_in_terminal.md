---
title: "configuring wifi in terminal"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by linkxs on 2008-10-05
is tehre a decent utility to configure wifi in terminal? i dont use gnome,  i use MWM so it's a problem. i tried Wicd (not terminal, but still. i tried to get some gnome network managers working, upgraded from 7.04 to 7.10 to 8.04, tried network-admin on each of them, but on 8.04 it is all locked, and i can't get it unlocked even if i sudo it.)

---

### Post by jmbargar on 2008-10-05
For configuring your network connection using the terminal, you have to modify a couple of files:

> /etc/network/interfaces

in order to define your netmask, your gateway, your broadcast address or your ip private address and method for getting it. Also, this file permit you to establish your WEP key. If you are using WPA method you may have a quick look at the wpasupplicant documentation.

> /etc/resolv.conf

in order to configure your dns servers unless your router had sent it via dhcp.

For further information about the parameters you can put into this files accoding to your network configuration, your can use the man typing in a terminal something like:

> man interfaces

and

> man resolv.conf

Don't forget you must restart your network services when you have finished your configuration, typing something like:

> /etc/init.d/networking restart

Good luck!

---

### Post by linkxs on 2008-10-06
well, i was actually also wondering of any way i could scan availible wifi networks in nrange in terminal..

---

### Post by wanfahmi on 2008-10-06
> **linkxs said:**
> well, i was actually also wondering of any way i could scan availible wifi networks in nrange in terminal..

you could 
```
iwlist eth1 scan
```
(Replace eth1 with your wifi device.)

Which would dump all the wifi networks in range.

---

### Post by bionnaki on 2008-10-06
how would you connect to a wep encrypted network via terminal? I've had it with network manager and wicd and would rather use CLI.

---

