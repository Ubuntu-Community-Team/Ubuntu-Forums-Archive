---
title: "server set to static ip, but router gives it dhcp address"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by jdcnosse on 2008-10-19
Hi all, I have Ubuntu 8.04 server edition, and I've edited the /etc/network/interfaces file so that it is set to static, but every 24 hours or so for some reason the server looses it's static address and get's an address from the dhcp server on my linksys wrt54gs router.

The router's ip is 192.168.1.1, so I set the server's static ip to 192.168.1.2, and the router's dhcp range 192.168.1.100 through 105.

EDIT: I've also went through and edited the /etc/dhcp3/dhclient.conf file to include this:
```
alias {
interface "eth0";
fixed-address 192.168.1.2;
option subnet-mask 255.255.255.0;
}
```

why do i keep loosing my ip address?

---

### Post by Iowan on 2008-10-20
Might need to set up the static lease on the DHCP server.  Otherwise, the static address could (should?) be set up in */etc/network/interfaces*.

---

### Post by jdcnosse on 2008-10-20
> **Iowan said:**
> Might need to set up the static lease on the DHCP server.  Otherwise, the static address could (should?) be set up in */etc/network/interfaces*.

> **jdcnosse said:**
> ...and I've edited the /etc/network/interfaces file so that it is set to static...

I think so far its working though...

---

### Post by Iowan on 2008-10-20
> **jdcnosse said:**
> ... and I've edited the /etc/network/interfaces file so that it is set to staticSorry, my bad... I noticed the /etc/dhcp3/dhclient.conf settings - put 1&1 together and came up with 3.
BTW, having DHCP server issue a static lease is perfectly viable way to manage IP addresses.

---

### Post by jdcnosse on 2008-10-21
> **Iowan said:**
> Sorry, my bad... I noticed the /etc/dhcp3/dhclient.conf settings - put 1&1 together and came up with 3.
BTW, having DHCP server issue a static lease is perfectly viable way to manage IP addresses.

I'm not sure how to do that though...

It does seem to go away after I run */etc/init.d/networking restart*

---

### Post by Iowan on 2008-10-21
You'd need to set it up on the DHCP server - Your server may be different, but you can get some ideas from but [this]("http://www.linuxhelp.net/guides/dhcp/") shows how dhcpd.conf is set up.  [Here]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch08_:_Configuring_the_DHCP_Server") is another.
BTW, what goes away after a restart, and is it good or bad?

---

### Post by jdcnosse on 2008-10-21
when I restart the networking, it uses the settings that I set up in /etc/network/interfaces

---

### Post by jdcnosse on 2008-10-22
Okay I've replaced the Linksys default firmware with DD-WRT (which I like because there's a spot to put in static IP leases).

Hopefully this will always work.

---

