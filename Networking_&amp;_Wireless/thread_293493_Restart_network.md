---
title: "Restart network"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by spotslayer on 2006-11-05
Morning,   I am new to kubuntu but have used linux for five years. In other distros I could use /etc/rc.d/network (start, stop or restart) to do these things. Is there a corresponding script for this distro?

David

---

### Post by noswitchport on 2006-11-05
sudo /etc/init.d/networking restart

---

### Post by wpwood3 on 2006-11-05
sudo /etc/init.d/networking restart

Be sure to put the **[COLOR="Red"]ing[/COLOR]** in networking!

---

### Post by spotslayer on 2006-11-26
I am working away from home and have limited access to internet. Will give it a shot when I return home.

David

---

### Post by clinto on 2007-09-25
Gee, I hope David here made it home. :/

Does this not work with Feisty? When I try giving this command, it says I'm using it incorrectly. I'd paste exactly what it said, but I'm in Windows because I'm having troubles fixing my network settings. But it says something like:

```
usage: /etc/init.d/networking {stop|start|restart}
```
I used this format:
```
sudo /etc/init.d/networking restart
```
and I tried other formats like:
```
sudo /etc/init.d/networking --restart
sudo /etc/init.d/networking {restart}
```
etc.

---

### Post by nooblot on 2007-11-03
> **clinto said:**
> 
Does this not work with Feisty? When I try giving this command, it says I'm using it incorrectly. I'd paste exactly what it said, but I'm in Windows because I'm having troubles fixing my network settings. But it says something like:
.

it does.

Guess you have your networking problem sorted out.

if not, tell us what the shell complains about

---

### Post by baskinsy on 2007-11-04
I have a similar problem.

I want to add a static route to be activates at boot time.

My /etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

iface eth0 inet static
address 10.215.2.218
netmask 255.255.255.248
gateway 10.215.2.217
up /sbin/route add -net 10.0.0.0 netmask 255.0.0.0  gw 10.215.2.217 eth0

```

I try to test if everything is ok by restarting network with the command

```
sudo /etc/init.d/networking restart
```

The static route is not added (even after reboot) and i have the following error

```
 sudo /etc/init.d/networking restart
[sudo] password for strzol:
 * Reconfiguring network interfaces...
SIOCADDRT: File exists
Failed to bring up eth0.
                                                                         [ OK ]

```

After that the network works ok but without the static route. I was using the same configuration in Ubuntu 7.04, but now with 7.10 is not working.

For those that will mention that the static's route gateway is the same as the default, i have to say that i'm using an openvpn tunnel with "redirect gateway" configuration option that changes the default gateway after establishing the vpn connection. So i want the static route to point to the 10.0.0.0/8 network and all other traffic to go through the tunnel. It is working flawless on other systems and on my previous installation with 7.04. 

Any hints?

---

