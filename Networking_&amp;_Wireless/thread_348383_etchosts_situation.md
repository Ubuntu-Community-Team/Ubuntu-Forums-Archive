---
title: "/etc/hosts situation"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by jaymz on 2007-01-28
I've been trying to get wireless on Ubuntu for ages, I've tried everything time and again with no result...

But the ammount of different solutions I've tried have had some side effects, perhaps by my own incompetence...

I seem to have accidentally (and unknowingly) erased my /etc/hosts file... Now I have absolutely no idea how to replace it and I am without wired net.

Help...

---

### Post by taurus on 2007-01-28
Boot into recovery mode from GRUB menu and edit /etc/hosts.

```
nano /etc/hosts
```
Paste the stuff below to it.  However, replace **taurus** with the actual name of your machine, the _same_ one that you have in /etc/hostname.  This is really important, okay.

```

127.0.0.1       localhost
127.0.1.1       **taurus**

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by jaymz on 2007-01-28
Done :)

Thank you very much

For some reason I can't get wired internet anyway...

---

### Post by taurus on 2007-01-28
Wireless card!  What is it anyway?

---

### Post by jaymz on 2007-01-28
Didn't really understand what you meant but if you're asking what my wireless card is then it's an Intel Corporation PRO/Wireless 3945ABG Connection

But I can't get wired internet either now... I thought it was the hosts, but now I've got them in place too and still nothing :(

---

### Post by taurus on 2007-01-28
Does your machine connect to a router?

---

### Post by jaymz on 2007-01-28
I didn't understand the question... It connects fine with network-manager and in my university (which uses a VPN client).

But at home, with a static IP the NM doesn't work and I just can't get it to work without it...

---

