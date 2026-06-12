---
title: "Static IP Address does &quot;Stick&quot;"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by Soda Ant on 2008-03-21
I just installed the 8.04 beta on my machine and the default was to use DHCP to assign an IP address. I used the System->Administration->Network tool to try to assign a static IP address to eth0, but it doesn't take. In fact, after I do this, eth0 has no IP address at all.

I can add an IP manually using 'ifconfig eth0 10.1.1.7...' and that works, but why doesn't the Network utility set the static IP correctly?

What file does the OS keep the IP address info when a static IP is configured?

---

### Post by Eiríkr on 2008-03-22
Have a look at [font=courier]/etc/network/interfaces[/font] for starters.  Static IP setups (in 7.10 at least) should look something like:
```
auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.10
```

HTH,

Eiríkr

---

