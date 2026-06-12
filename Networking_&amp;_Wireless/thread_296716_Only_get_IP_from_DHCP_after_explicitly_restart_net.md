---
title: "Only get IP from DHCP after explicitly restart networking"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by vairoj on 2006-11-10
I'm running Ubuntu Server 6.06. The problem is when the server is booted up, it won't get its IP from DHCP server. So it could not make any connection to any machine. However, if I explicitly restart the networking interface by either:
```
ifdown && ifup
```
-or-
```
/etc/init.d/networking restart
```

Everything will be back to normal. Why is that? How could I fix this problem so that the IP will be assigned from the first start without user intervention?

---

### Post by Iowan on 2006-11-10
Post the **/etc/networking/interfaces** file.  DHCP for server??? Is it being assigned a static lease?

---

### Post by vairoj on 2006-11-13
The setting is very standard with no configuration at all.

/etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

```

This machine obtains IP address from a DHCP server.

---

### Post by vairoj on 2007-02-13
Anyone ever encounter this kind of problem?

---

### Post by mozetti on 2007-02-13
I'm having this problem right now with my HP ze2315 laptop with built-in Broadcom (4318 i think?--at work) Air Force One wifi card. Is your nic hard-wired or wifi?

---

### Post by vairoj on 2007-02-14
The network card is hard-wired. It is run on Dell PowerEdge 750 Server.

---

### Post by vairoj on 2007-06-18
Ok, after searching around this forum and trying several approaches, I managed to fix the problem.

What I did is edit /etc/network/interface

add this line:
```

pre-up sleep 5

```

after the line
```

auto eth0
iface eth0 inet dhcp

```

This is to delay the service for 5 sec before trying to obtain the ip from dhcp server.
I don't know why I need this line since in my VMware setup every works perfectly from the start. However, this problem seems to occur on my Dell PowerEdge 750 only and this solution works for now.

---

