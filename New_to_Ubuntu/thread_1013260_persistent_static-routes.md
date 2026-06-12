---
title: "persistent static-routes"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by know-it-some on 2008-12-16
What, in ubuntu, is the equivalent of /etc/sysconfig/static-routes for configuring persistent static routes?

---

### Post by Shhnap on 2008-12-17
Don't really know what your looking for but was it perhaps /ect/sysctl.conf?

Sorry, this is probably no help.

---

### Post by Iowan on 2008-12-17
Check **man route**.

---

### Post by zeeple on 2009-01-02
The answer to this will not be found by reading the man page for the route command, unfortunately.  Since I have struggled with this I happen to know a little bit about how this works in ubuntu and other distros as well.  The reason you will not find the answer in the route man page is because this is handled differently depending on the distribution.

To answer the original question, what is gathered together in RedHat's /etc/sysconfig dir is mostly in /etc/network in ubuntu so that is the best place to look first when you need to manually edit some networking or interface properties.  And as to the very specific static-route file that you get in other distros, this does not exist anywhere in ubuntu.  Rather, to add a static route in ubuntu you add it to the interfaces file immediately under the interface block that will be affected by it, as such:

```

root@isengard:/etc/network# more interfaces 
auto lo
iface lo inet loopback


iface eth0 inet static
address 10.80.80.1
netmask 255.0.0.0
gateway 10.44.65.1

# static routes
up route add -net 10.10.11.0/24 gw 10.0.0.1 dev eth0
up route add -net 10.10.12.0/24 gw 10.0.0.1 dev eth0

auto eth0

```

Remember a couple of things though.  If you add these routes simple using the route command, you will lose them next time your networking is restarted, machine is rebooted, etc.  Also, if you go this route to make them permanent (or static) then you need to restart networking to make use of the new routes, via:

```

sudo /etc/init.d/networking restart

```

If you get an error saying something to the effect that the interfaces file could not be read then you are dealing with either a syntax problem or a placement problem. Be careful to place the static routes under the interface you want them to affect.

---

