---
title: "Unable to connect to a unsecured wireless network"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by justdedict on 2007-06-23
I am unable to connect to a unsecured wireless network. I can see them, but when I try to connect to this, it tries it for a while and then gives it up. Secured wireless networks are not a problem.
Anyone familiar with this?

Just

I am using Ubuntu 7.04 on a Dell Inspiron 1501 laptop

---

### Post by Maxtorm on 2007-06-23
Is the unsecured wireless network yours?  If not, the owner could be using something other than encryption to secure the network (e.g. MAC filtering).  It would still show up in your list of wireless networks as unsecured, but since your MAC address is not in the approved list, it wouldn't be able to connect.

---

### Post by justdedict on 2007-06-23
It are networks like in the university or hotels to which I should have access.

---

### Post by Maxtorm on 2007-06-23
Are you using network-manager to connect (i.e. the built-in wireless tool in 7.04)?  If so, have you tried using others like Wifi Radar*  to determine whether the problem is specific to network-manager?  

* see: [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/) - available via Add/Remove, though I'm not sure which repo it is in.

---

