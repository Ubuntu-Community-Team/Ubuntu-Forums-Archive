---
title: "Network interface keeps &quot;falling asleep&quot; on Ubuntu 6.10 Server"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by CaptSaltyJack on 2007-04-19
Something's up with this server I set up.  Here's the /etc/network/interfaces file:

```

auto eth0
iface eth0 inet static
        address 10.1.4.93
        netmask 255.255.255.0
        network 10.1.4.0
        broadcast 10.1.4.255
        gateway 10.1.4.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 10.1.4.49 10.1.4.59

```

It works fine and other computers can connect to the server (ssh, http, etc).  Then randomly, it is unreachable, can't ping it, nothing.  I go to the server's console, do "ifup eth0"..says it's already up.  ifconfig shows everything fine, yet nothing can connect to it at all or ping it.  THEN, from the server console, I do "ping www.google.com" and that somehow "wakes up" the server, and all clients can connect to it once again.

What the heck is going on?? :confused:

---

### Post by CaptSaltyJack on 2007-04-20
Anyone?

---

### Post by CaptSaltyJack on 2007-04-27
OK, actually I found out it falls asleep and comes back a few minutes later.  Very odd.  Anyone know what might be causing this?

---

