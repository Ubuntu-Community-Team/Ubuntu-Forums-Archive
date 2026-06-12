---
title: "[SOLVED] howto add permanent route entry"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by MatsB on 2006-08-11
How can I add a permanent route entry so it stays after a reboot?

I guess I need to edit the /etc/network/interface file, but what and how should I add the string?

Running this command is only a temp solution:
route add -net 192.168.2.0 netmask 255.255.255.0 gw 192.168.1.1

---

### Post by tomtom_in_eire on 2006-08-11
Hi,

You're right: you need to edit /etc/network/interfaces.
what you need to put in there is:
```
up /sbin/route add -net 192.168.2.0/24 gw <gateway_IP>
down /sbin/route del -net 192.168.2.0/24 gw <gateway_IP>
```

Reboot and you're done!

Enjoy.

---

### Post by MatsB on 2006-08-11
Perfect! Thanks

---

### Post by jplinux on 2006-08-11
More simple and really efficient ...
Create that file /etc/network/if-up.d/static-routes as follow

#!/bin/sh
# Set static routes
#
/sbin/route add -net 192.168.10.0 netmask 255.255.255.0  gw 192.168.1.254
/sbin/route add -net 192.168.0.0 netmask 255.255.0.0  gw 192.168.1.1

---

### Post by nebid on 2007-07-16
/etc/network/if-up.d is a directory that contains scripts that are run after networking is started. So when you create the file "static-routes" you need to make it executable.

chmod 755 /etc/network/if-up.d/static-routes

---

### Post by mrit on 2007-10-03
very strange! neither of the two solutions works here:

i want to have a second virtual ip-adress, so 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.7
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
# up "/sbin/route add default gw 192.168.1.1 eth0"
up /sbin/route add default netmask 255.255.255.0 gw 192.168.1.1 eth0

# second virtual network for ssh
auto eth0:1
iface eth0:1 inet static
address 192.168.1.22
# gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

```

this works, both IPs are present.

but: when rebooting, no route is present

```
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

i also tried to add a little script /etc/networking/if-up.d/staticroute. also no route! 
but it seems that those scripts are not called at all...

thanxs

markus

---

### Post by TitanKing on 2007-10-29
> **jplinux said:**
> More simple and really efficient ...
Create that file /etc/network/if-up.d/static-routes as follow

#!/bin/sh
# Set static routes
#
/sbin/route add -net 192.168.10.0 netmask 255.255.255.0  gw 192.168.1.254
/sbin/route add -net 192.168.0.0 netmask 255.255.0.0  gw 192.168.1.1

This is the most effective way:

[http://www.pcbuyersguide.co.za/showthread.php?p=62262#post62262](http://www.pcbuyersguide.co.za/showthread.php?p=62262#post62262)

---

### Post by netztier on 2007-10-29
> **mrit said:**
> 
```

# up "/sbin/route add default gw 192.168.1.1 eth0"
up /sbin/route add default [COLOR="Red"]netmask 255.255.255.0[/COLOR] gw 192.168.1.1 eth0
[CODE]


That statement does not make sense. A *default* route alwas has 0.0.0.0 as destination and 0.0.0.0 as destination mask. So the statement you have commented-out in the line above is correct - the "default" keyword implies 0.0.0.0/0.0.0.0.

Instead of the old route command, you could also use the newer "ip" command. I like it's syntax better than the route command.

[CODE]ip route add to 0.0.0.0/0 via 192.168.1.1
```

best regards

Marc

---

