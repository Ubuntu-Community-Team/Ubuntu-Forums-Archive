---
title: "Server somehow gets dynamic address"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by MobiusNZ on 2007-09-29
Hi guys, I have an ubuntu feisty server. It's set up with a static ip, and is also my dns and dhcp server. This was fine on my last install, but since then I've reinstalled with a new gigabit nic. Now, every couple of hours or so, it switches to a dynamic ip address, even though its set to static. I have to restart networking, dhcp and bind. It's really annoying!!

I get this a lot in my /var/log/syslog
```
Sep 30 10:39:09 sarge dhclient: DHCPREQUEST on eth0 to 192.168.1.5 port 67
Sep 30 10:39:48 sarge last message repeated 3 times
Sep 30 10:40:50 sarge last message repeated 4 times
Sep 30 10:41:51 sarge last message repeated 5 times
Sep 30 10:42:39 sarge last message repeated 3 times
Sep 30 10:43:48 sarge last message repeated 6 times
Sep 30 10:44:51 sarge last message repeated 5 times
Sep 30 10:45:45 sarge last message repeated 3 times
Sep 30 10:46:48 sarge last message repeated 6 times

```

Here's my /etc/network/interface in case you're wondering...
```
al@sarge:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1

```

Any help would be most appreciated

---

### Post by helgman on 2007-10-04
I've had a similar problem. Make sure that dhclient/dhclient3 is not running on the server (it was on mine for some reason).

Regards,
Helgman

---

