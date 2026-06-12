---
title: "Static IP addresses behind my firewall. . ."
date: 2009-04-21
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-04-21
Hi!  I have an Ubuntu 8.10 server running behind my firewall that provides file sharing, printer sharing, and other home server things like that.  However, I have to "guess" at it's IP address whenever I try to SSH to the server, because my router gives it a new address every so often with DHCP.  Can I give my server a static IP address, just behind my router?  What configuration file(s) would I edit to make this work?

Thanks in advance!

---

### Post by amingv on 2009-04-21
Often you have to ask your ISP for a static IP, or set it in your router yourself (if your ISP allows it).

In either case you should contact your ISP.

EDIT:
Sorry! Didn't see the behind my router part.

You can either set it in the box (edit /etc/network/interfaces) or in your router's DHCP settings, if it allows it.

Or maybe you could SSH the host's name (DNS)?

---

### Post by garyed on 2009-04-21
Here's what my file looks like:

/etc/network/interfaces
```
 
auto lo
iface lo inet loopback
iface eth0 inet static
address 192.168.1.136
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
auto eth0

```

Hope this helps

---

### Post by pi.boy.travis on 2009-04-21
Thanks!  Just what I was looking for!

Now that my server has it's own static IP behind my router, could I give it a domain name, just for use behind my firewall?

---

### Post by amingv on 2009-04-21
Most routers pick the name of the machine and make a DNS entry automatically that relates it to the ip. So for example if your router has an integrated DNS server that is active you should be able to make (asuming your server is called "ubuntu-server")

```
ssh ubuntu-server
```

If that doesn'n work you could:

a. Check your router to see if DNS is enabled, or if you must manually add the entries.

b. In there's no DNS functionality in the router, you could install a DNS server in your server box. ([See here]("https://help.ubuntu.com/8.04/serverguide/C/dns.html"))

---

### Post by pi.boy.travis on 2009-04-21
Awesome!  Thanks!  Just what I was looking for!

---

### Post by hyperyoda on 2009-04-21
> **pi.boy.travis said:**
> Hi!  I have an Ubuntu 8.10 server running behind my firewall that provides file sharing, printer sharing, and other home server things like that.  However, I have to "guess" at it's IP address whenever I try to SSH to the server, because my router gives it a new address every so often with DHCP.  Can I give my server a static IP address, just behind my router?  What configuration file(s) would I edit to make this work?

Thanks in advance!

Hi,

These sources should give you enough info to get it working:

$ man 5 interfaces

[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)
[http://en.kioskea.net/faq/sujet-979-having-a-static-ip-address-under-ubuntu-8-10](http://en.kioskea.net/faq/sujet-979-having-a-static-ip-address-under-ubuntu-8-10)

---

