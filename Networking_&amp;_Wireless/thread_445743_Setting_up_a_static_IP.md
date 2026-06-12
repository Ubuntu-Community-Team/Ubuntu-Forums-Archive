---
title: "Setting up a static IP"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by oxygenjunkie88 on 2007-05-16
So I set up a static IP last night which worked fine until I rebooted this morning. It wouldn't connect me to my router. I have all the same details that I used when it was working. Anyone know what's up? Oh, and I have another computer connected to the same router/connection if that's of any significance.

---

### Post by mitch.c on 2007-05-16
Why don't you post the  contents of /etc/network/interfaces. Here is how mine looks:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.250
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1
```

You might check yours against this one (with your own ip addresses of course).

-- 
Mitch

---

