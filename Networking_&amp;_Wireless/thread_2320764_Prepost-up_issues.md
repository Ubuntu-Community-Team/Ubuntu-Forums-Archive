---
title: "Pre/post-up issues"
date: 2016-04-17
forum: Networking &amp; Wireless
---

### Post by pingaan on 2016-04-17
Hi,

I'm trying to make my laptop run a script when plugging and unplugging the ethernet. This is my /etc/network/interfaces:

```
a[COLOR=#222426][FONT=Consolas]uto lo
[/FONT][/COLOR]iface lo inet loopback

auto eth0
iface eth0 inet dhcp

post-up /home/x/test.sh
pre-up /home/x/test2.sh
```

Nothing happens. The ethernet doesn't even connect.

What am I doing wrong?

Regards.

---

### Post by ian-weisser on 2016-04-17
If the pre-up script fails, the interface is not configured.
If the post-up script fails, the interface is not marked as configured, and an error message is generated.
(Source: man interfaces(5))

Comment out both scripts. If you can then connect, you know at least one script is causing the failure.
Enable one script at a time until you identify the script causing the failure.

---

### Post by pingaan on 2016-04-17
I removed both scripts and nothing happens still. Interfaces now looks like:
```
[COLOR=#000000][FONT=Ubuntu Mono]a[/FONT][/COLOR][COLOR=#222426][FONT=Ubuntu Mono][FONT=Consolas]uto lo[/FONT][/FONT][/COLOR]iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

If I remove oth "eth0" lines the connection works just fine.
Is it dhcp? The router is set to give the mac number a specific IP.

---

### Post by Bucky Ball on 2016-04-17
If you are using Network Manager as well as tweaking your /interfaces file, don't think it will make much difference what you put in /interfaces. Network Manager takes preference.

---

### Post by pingaan on 2016-04-17
Oh well, I am using network manager. But if what you say is true and network manager over runs interfaces, why then won't the ethernet port work when adding those lines tocinterfaces?

---

