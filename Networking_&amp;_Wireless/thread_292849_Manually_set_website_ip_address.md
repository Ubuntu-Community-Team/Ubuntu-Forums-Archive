---
title: "Manually set website ip address?"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by Statik on 2006-11-04
Hi all,

Is there a place that I can set the IP address for a website manually? I have a website to do for a client and I need the server to recieve the request in the name of the domain, but the domain itself is not yet active. Is there a place that I can just enter the domain name and the server IP?

Thanks
Statik

---

### Post by kidders on 2006-11-04
Hi there,

You can't make a website answer to an address that isn't its own, since packets destined for somewhere else won't be sent to it anyway. I *think* that's what you're asking!

You could however set up the domain you have yet to register on your own LAN. Packets from *outside* the LAN still won't be sent to your server, but I guess that's obvious.

---

### Post by spd106 on 2006-11-04
If it's only one PC that needs to resolve the domain name to an IP address temporarily, then you can add the details to the /etc/hosts file.

eg host wants to contact server.somewhere.com

host    ->    server.somewhere.com (200.0.0.1)

then change

you@host:~$ **gksudo gedit /etc/hosts**

```

127.0.0.1       localhost
127.0.1.1       host
200.0.0.1       server.somewhere.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Now host will resolve the server. When the DNS comes on line you can remove the entry. You could also update your own DNS server, if you have admin control over it. Is this what you mean?

---

### Post by Statik on 2006-11-04
spd106, this is EXACTLY what I mean. Thankyou muchly.

Statik

---

