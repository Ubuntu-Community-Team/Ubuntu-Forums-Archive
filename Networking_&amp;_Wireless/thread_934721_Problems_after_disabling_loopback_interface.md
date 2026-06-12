---
title: "Problems after disabling loopback interface"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by ittiam on 2008-09-30
I was not getting any dhcp offers or dhcp was not being executed for some reason for my wireless interface during startup. (i blacklisted ipv6)


Hence I was fiddling with my /etc/network/interfaces file and removed loopback entry from it.

```
auto lo
iface lo inet loopback

```

once I did a reboot, the terminal opened but froze, firefox never opened and nautilus had some problems. Can somebody explain reason for this?

Once i restored those lines in the interfaces file, things were restored back to normal but still not getting dhcp during startup.

---

### Post by cariboo on 2008-10-01
Have a look at this page:

[http://www.manpagez.com/man/4/lo/](http://www.manpagez.com/man/4/lo/)

This will explain why you need the lo interface.

Jim

---

### Post by ittiam on 2008-10-02
thanks!

---

