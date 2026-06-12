---
title: "Change IP address and make it stick"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by ceviche on 2008-07-15
I did the following on my new ubuntu server install that has as default a 10.x.x.x ip address.

```
ifconfig eth0 down
ifconfig eth0 192.168.1.111 netmask 255.255.255.0 up
route add default gw 192.168.1.254
```

But when I reboot it reverts.
How do I make it stick?

Thanks!

---

### Post by chiefchimp on 2008-07-15
My way of doing it (in kubuntu) is go to system settinngs --> network settings --> network connections --> nework interfaces --> configure and set manual:
 ipaddress: 192.168.1.111
 netmask 255.255.255.0
Activate when computer starts
advanced settings:
 gateway: 192.168.1.254

system settinngs --> network settings --> network connections --> Routes:
Dafault Gateway
 IPaddress: 192.168.1.111

system settinngs --> network settings --> network connections --> Domain name system:
static hosts: Add 192.168.1.111 <hostname>

this works for me, hope your milage doesn't vary

---

### Post by ceviche on 2008-07-15
> **chiefchimp said:**
> My way of doing it (in kubuntu) is go to system settinngs --> network settings --> network connections --> nework interfaces --> configure and set manual:

Thanks, but I don't have a GUI installed. I need to do this via command line.

---

### Post by chiefchimp on 2008-07-15
> **ceviche said:**
> Thanks, but I don't have a GUI installed. I need to do this via command line.

this may be (probably is) incomplete, I haven't done it for a couple of years:

in /etc/hosts replace the line:
127.0.1.1 <host>
with
192.168.1.111 <host>

in /etc/hostname 
<host>

in /etc/network/interfaces
iface eth0 inet static
address 192.168.1.111
netmask 255.255.255.0
gateway 192.168.1.254

auto eth0

make sure you have saved a copy of all files you changed then

finish with /etc/init.d/newtorking restart

---

