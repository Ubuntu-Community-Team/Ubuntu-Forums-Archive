---
title: "A start job is running for wait on all &quot;auto&quot;"
date: 2015-07-22
forum: Networking &amp; Wireless
---

### Post by Levi_Muniz on 2015-07-22
Upon startup of my Ubuntu 15.04 Server, my boot is stopped by the message:```
A start job is running for Wait on all "auto" /etc/network/interfaces to be up for network-online.target
```This lasts for about 2 minutes and 10 seconds. I also just finished installing DRBL. The server is not meant to connect to the internet.

If anyone has a way to disable or find the cause for this, I would be very grateful.

Here is my interfaces file:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.5.20.2
netmask 255.255.255.0
gateway 10.5.20.1
dns-nameservers 8.8.8.8

auto eth0:0
iface eth0:0 inet static
address 10.5.20.2
netmask 255.255.255.0
dns-nameservers 8.8.8.8

```

---

### Post by TheFu on 2015-07-22
You cannot have to interfaces on the same IP address.  At least I don't think you can.
Also - of the network isn't connected Ubuntu will wait for 2x 60 second periods for the network to come up. You can reduce that time - there is a script in /etc somewhere.  Just grep for the exact message to find it. On my netbook, I've reduced the timeout to 10 sec, so at boot when there isn't any networking I only have to wait 20 sec for the login prompt.  From memory, I think the filename has "failsafe" in it, but don't quote me.

---

### Post by Levi_Muniz on 2015-07-23
Thanks, but it seems to be working with the strange IP config. I don't even really remember why I set up the interfaces file like that. I previously tried to change the /etc/failsafe file but that didn't effect this. I'll try to reboot when I get a chance and see if it gives me the same message.

---

### Post by TheFu on 2015-07-23
Having 2 interfaces with a single IP on the same subnet is an error. 
The eth0:0 stanza isn't helping at all. Best to remove it.

---

### Post by Levi_Muniz on 2015-07-23
Thanks for the recommendation! However, we have yet to see if this stops the waiting problem. I'll post back here when I can access the machine Monday morning.

---

### Post by Levi_Muniz on 2015-07-27
Well that seems to have solved it, thanks for the help!

---

