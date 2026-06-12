---
title: "[SOLVED] Automatically set hostname across network"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by mark.a.nicolosi on 2008-08-01
The default install of Ubuntu does something really cool; you can ping the hostname you set from any other computer on the network. No need to edit hosts files or remember IP addresses. Other OSes like Mac OS X does the same thing.

I want my Ubuntu server to do the same thing. Sure, I could set a static IP and edit every machine's /etc/hosts file, but that seems like a lot of work, when Ubuntu could do it automatically.

The only difference that I could think of is Network Manager, but I tried installing it and deleting the network configuration from /etc/network/interfaces, but it didn't work either.

Also, from reading interfaces(5), I learned I could ask the DCHP server to set my hostname. I figured this is what my Ubuntu desktop does and my Mac does, but it didn't work either.

Here's what my interfaces file looks like now:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
    hostname bob

```

Does anyone know how to get similar behavior on the server edition of Ubuntu?

---

### Post by mark.a.nicolosi on 2008-08-01
In case I didn't explain well: Somehow my Ubuntu desktop and my Mac tell my router what I set their hostname to be. As you can see in the screen shot the router know their hostnames. My router (its a 2Wire thing) does the DNS, so when I try to ping lothlorien, it resolves to lothlorien.gateway.2wire.net.

I want my server to do the same thing. You can see in the screenshot it is 192.168.1.67. It doesn't have a name, but notice the option to edit the name, that works until it renews its IP address.

So basically I just want my Ubuntu server to do the same thing as my Ubuntu desktop. Anyone have any ideas?

---

### Post by Iowan on 2008-08-01
Your server gets a DHCP Address? Ordinarily, servers get assigned a static IP address (or static lease via DHCP).  Using DHCP DOES make the DNS-thing easier, though.  Under **/etc/dhcp3/dhclient.conf** is an option to "send hostname". Uncomment that line, insert proper hostname, and restart networking.

---

### Post by mark.a.nicolosi on 2008-08-01
Solved! Make /etc/dhcp3/dhclient.conf look like this:

```

send host-name "whatever";

request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, ntp-servers;

```

Basically it was requesting a host-name from the dhcp server, now it tells the dhcp server what it wants its hostname to be.

---

### Post by mark.a.nicolosi on 2008-08-12
> **Iowan said:**
> Your server gets a DHCP Address? Ordinarily, servers get assigned a static IP address (or static lease via DHCP).  Using DHCP DOES make the DNS-thing easier, though.  Under **/etc/dhcp3/dhclient.conf** is an option to "send hostname". Uncomment that line, insert proper hostname, and restart networking.

Hi, I just noticed your reply. I think I must have figured it out while you were trying to tell me. Thanks.

---

