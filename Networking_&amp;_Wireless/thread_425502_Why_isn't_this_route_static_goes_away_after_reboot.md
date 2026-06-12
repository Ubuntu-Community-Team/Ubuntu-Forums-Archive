---
title: "Why isn't this route static? goes away after reboot"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by Underpants on 2007-04-27
I have added this route to my machine: 

```
route add -net 192.168.10.0 netmask 255.255.255.0 dev eth1
```

If I reboot, the route goes away... am I missing a statement that makes the route static? UGH.

---

### Post by spd106 on 2007-04-27
The routing table is not persistent and needs to be rebuilt every time you boot.

Add the command to your /etc/network/interfaces file (man interfaces) or put it in a script and place that in your /etc/network/if-up.d/ folder.

---

### Post by Underpants on 2007-04-27
So I should put 

```
up route add -net 192.168.10.0 netmask 255.255.255.0 dev eth1
```

at the bottom of the file?

---

### Post by Underpants on 2007-04-28
Bump, is that right? it's on a machine I don't have a lot of physical access to.... I don't want to mess the networking up :)

---

### Post by spd106 on 2007-04-28
That line looks okay to me.

It's probably worth while testing on a local machine first though, just for piece of mind.

---

