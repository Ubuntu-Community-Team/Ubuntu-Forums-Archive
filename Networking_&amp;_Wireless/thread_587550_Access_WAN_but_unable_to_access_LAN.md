---
title: "Access WAN but unable to access LAN"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by LaserCobra on 2007-10-22
This could be another one of those known things but I'm rather new to the world of Linux. I started with 7.04 and had this issue then and now with 7.10. I can access the web, I'm typing this on the problem computer but I can't access my router's config via 192.168.0.1 or my NAS via its network address. Other Windows based systems can access both without an issue. This is very strange and Google was no help. Every attempt to connect is greeted with a "cannot connect" message. Attempting to mount a network drive ends with a "time out" message.

Any thoughts?

---

### Post by darjeeling on 2007-10-23
> **LaserCobra said:**
> This could be another one of those known things but I'm rather new to the world of Linux. I started with 7.04 and had this issue then and now with 7.10. I can access the web, I'm typing this on the problem computer but I can't access my router's config via 192.168.0.1 or my NAS via its network address. Other Windows based systems can access both without an issue. This is very strange and Google was no help. Every attempt to connect is greeted with a "cannot connect" message. Attempting to mount a network drive ends with a "time out" message.

Any thoughts?

Same type issue here.

If you could cat your /etc/network/interfaces file, that would be helpful.

---

### Post by LaserCobra on 2007-10-23
I appreciate the offer to help. Here's the requested info:

```
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1


auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

```

My wired connection should be disabled. I did that to ensure all local requests were going out of the correct network interface.


*JAW DROPS ON FLOOR*

Just before I posted this I decided to attempt a router connection one more time and it worked! I've done NOTHING different over the last 4 days trying to get this working and boom- it worked today. I should be happy but I would rather have figured out the issue. I'm sure it's going to come up again.

Thanks to all that at least read this post.

---

