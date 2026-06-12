---
title: "Can u Connect To Networks At The Same Time"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by bulmer247 on 2008-03-18
What i would like to do is have one wirelles connection and one wirred or two wirless
is this possible?

---

### Post by Eiríkr on 2008-03-18
You can connect to as many different networks as you have network interfaces (real or virtual).  For instance, my workstation runs Kubuntu, is connected via eth0 to the LAN, via eth1 to VMware host-only, and via eth2 to VMware NAT (i.e. the VMware guest connects through eth2 and thence through eth0 to the home LAN / web).  Both eth1 and eth2 are virtual interfaces, software-only.  

So long as you have a wired and a wireless interface in your computer, you should be able to connect to both a wired and wireless network at the same time.  

Cheers,

Eiríkr

---

### Post by Iowan on 2008-03-19
Not absolutely sure... but there might be an issue if they're both in the same subnet - otherwise should work.

---

### Post by netztier on 2008-03-19
> **Eiríkr said:**
> So long as you have a wired and a wireless interface in your computer, you should be able to connect to both a wired and wireless network at the same time.  


Not if both/all interfaces are managed by network-manager. It has the (severe) limitation of allowing only one active interface at a time.

You can however manage some (even multiple) interfaces via the config file **/etc/network/interfaces** and leave the rest to network-manager to do it's WPA magic.

Each interface in /etc/network/interfaces needs a statement like:

```
auto eth0
iface eth0 inet <method>
 ...

auto eth1
iface eth1 inet <method>
 ...
```

Where <method> can be "static" or "dhcp" or others (see **man interfaces**). Any interface that has such an entry in /etc/network/interfaces will be ignored by network-manager. It will only try to manage the others it finds on the system.

One issue you will always have to resolve when using multiple interfaces is the one with the **default route**. Check the output of **netstat -r**. The destination network 0.0.0.0 with destination mask 0.0.0.0 is your default route, and you'll see the IP address of the "next hop" router.
If there are two default routes in your routing table, only the first entry will ever be used - which might be the one with the wrong next hop if you want to connect to the Internet... 

It is possible to do some advanced routing black magic to be able to use multiple default routes towards the Internet, but that's really advanced stuff.

regards

Marc

---

### Post by Eiríkr on 2008-03-19
And thanks again to Netztier :D -- 

I knew Network Manager had problems from the **many** posts on this forum that could be traced back to that, but I had no idea it only allows one active interface at a time.  Whah????  I'm baffled that such a severely limited piece of crufty software should be the default in Ubuntu.  What happened to basic quality testing?  Anyway, thanks to your post here, a few other bug-posts suddenly make sense as to why one of the network interfaces keeps dropping out.  :-|

Cheers,

Eiríkr

---

