---
title: "Port Forwarding and Network Startup"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by treymok on 2008-08-07
OK here is what I am trying to do. I connect my main machine through my roommates wireless router and can open ports via the router. Now I have a second machine with no wireless that is wired to the first and has internet from that machine. I want to open a port on the first machine so that a bittorrent client is connectable on the second machine. Another issue I am having is when I boot the second machine I have to do a "/etc/init.d/networking restart" for the internet to be usable. Is there a way to get it to do this automatically?

Thanks in advance.

---

### Post by treymok on 2008-08-07
Hmmm... Still no takers?

---

### Post by treymok on 2008-08-08
Nobody knows?

---

### Post by Iowan on 2008-08-08
I haven't done much w/ port forwarding on an Ubuntu machine (first machine is Ubuntu?), but didn't want to leave you talking (typing?) to yourself.  Check **/etc/network/interfaces** for an "auto eth0" line. Is second machine set up w/ static or DHCP address?

---

### Post by treymok on 2008-08-08
> **Iowan said:**
> (first machine is Ubuntu?)

Yes

> **Iowan said:**
> Is second machine set up w/ static or DHCP address?

Static

---

