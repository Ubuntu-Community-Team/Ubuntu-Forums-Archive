---
title: "dns problem?"
date: 2005-06-29
forum: Networking &amp; Wireless
---

### Post by one_ro on 2005-06-29
Hi all,

New in Ubuntu (5.04 Hoary Hedgehog)
My problem is probably related to the DNS because it gives errors every time I try to connect to any website.
I read the [http://ubuntuguide.org/](http://ubuntuguide.org/)
Q: How to activate/deactivate network connections?
which says:
2 System -> Administration -> Networking
3 Network settings
... but in the "System" menu I do not find "Administration".
I tried with Control Center / Network Settings (where it asks for Administrator Mode) but after I enter the root password it does... nothing.

I edited the /etc/resolve.conf file where I manually entered:
nameserver 192.168.1.254
nameserver 192.168.1.50

and still nothing.
I have a static IP, which is shown by /etc/network/interfaces

auto eth0
iface eth0 inet static
address 192.168.1.104
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

...and I have no more ideas. Help?
TIA,
Adrian

---

### Post by alastair on 2005-06-29
Networking problems - more information required i.e.

- a bit of information on your network setup
- output of "ifconfig -a"
- output of "route -n"

The "interfaces" file just says "configure my network like this" - but this does not mean the h/w is working or configured afterwards ...

---

