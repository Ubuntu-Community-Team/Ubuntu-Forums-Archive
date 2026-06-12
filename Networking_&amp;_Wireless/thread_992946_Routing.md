---
title: "Routing"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by Drezard on 2008-11-25
I have an Ubuntu Linux Server with 3 interfaces:

eth0 – internet connection A
eth1 – internet connection B
eth2 – internal network (10.1.1.1)

What I want to do is have traffic from 10.1.1.1 go out ONLY eth1, all other traffic go out eth0.

How do I set this up on my linux box? Any documentation people can recommend?

Daniel

---

### Post by timcredible on 2008-11-25
routing is normally done by looking at the destination address.  if you want to base routing on the source address, that's called policy based routing.  i know how to do that on a cisco router, but i have no idea how to do it on a linux machine, but maybe a search on pbr will help.

---

### Post by superprash2003 on 2008-11-25
you could use firestarter which has ICS( internet connection sharing) feature, or you could use this [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

