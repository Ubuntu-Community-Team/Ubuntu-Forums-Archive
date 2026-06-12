---
title: "changing loopback IP?"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by SYmek on 2008-04-04
hi everyone!

I'm trying to install Sun Grid Engine on Ubuntu 7.10 32bit. The install script fails:

> "It is not supported for a Grid Engine installation that the local hostname
contains the hostname "localhost" and/or the IP address "127.0.x.x" of the
loopback interface."



My /etc/hosts:

```
127.0.0.1	localhost
127.0.1.1	ubu
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


Does it mean that I need to change loopback IP for my computer? If so, which number this could be? I would rather ask this question before screw up all networking on my ubu...

Thanks for any help,
cheers,
skk.

---

### Post by SYmek on 2008-04-04
Ok, little progress, the scripts tells me:
> 
The "localhost" hostname should be reserved for the loopback interface
("127.0.0.1") and the real hostname should be assigned to one of the
physical or logical network interfaces of this machine.


What should I do than? How to assign hostname to a logical of physical interface?
by editing /etc/network/interfaces?

---

### Post by SYmek on 2008-04-06
Problem solved by assigning static IP to the second line in above /etc/hosts.

cheers,
sy.

---

