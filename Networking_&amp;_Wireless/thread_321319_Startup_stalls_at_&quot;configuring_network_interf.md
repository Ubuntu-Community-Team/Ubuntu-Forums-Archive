---
title: "Startup stalls at &quot;configuring network interfaces&quot;"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by cully on 2006-12-18
I've looked around all over for a suitable solution to this problem and have found nothing but hacks.

Anyway, my problem is that my startup/boot stalls for a minute or two at the "configuring network interfaces" step.

The reason this is happening is that startup is trying to get DHCP info. for both of my interfaces (eth0: wired, eth1: wireless).  It can't, since eth0 is not connected and eth1 is handled by KNetworkManager (and probably something else).  So, it waits for like 60 seconds on each interface.

After I finish startup, KNetworkManager is able to create a wireless connection on eth1.

I'm thinking that the network interfaces are being configured before some other program runs that does something that allows them to be configured.  I think this is the case because I tried removing the 'auto eth0' and 'auto eth1' lines from /etc/network/interfaces.  This solved the problem of the long wait (since no longer was startup trying to get DHCP info for my interfaces), but then KNetworkManager was unable to find my interfaces.  Just doing an ifup eth0, ifup eth1 doesn't allow KNetworkManager to see the interfaces.

Anyone have any ideas as to a solution?  Thanks.

---

### Post by stupidkid on 2006-12-18
What does the interfaces file show?

---

### Post by cully on 2006-12-18
This is what my interfaces file looks like

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

---

### Post by cully on 2006-12-18
I've actually found a pretty hacking solution.  I'm not sure if I like it but it works fine.  Anyway, the program that set up the network interfaces (other than 'lo') is /etc/init.d/networking.  So, I just disabled this in init.d:

```
% cd /etc/rcS.d
% mv S40networking K40networking
```

It works great.  KNetworkManager can still see the interfaces on startup and can create a wireless connection without problem.  It seems to confirm my idea that something else is running that configures the interfaces pre-KNetworkManager.  I just can't find it  :)

I would still like to find a non-hack solution, so if anyone can think of anything I would love to hear it.

---

### Post by martinrandau on 2006-12-20
I'm having similar problems and will try your solution if only I could get past that step - how do you turn off the network-interface at boot?

---

