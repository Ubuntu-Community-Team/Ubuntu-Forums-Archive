---
title: "pinging past router doesn't work"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by BungaMan on 2005-10-14
Hi

I have on my laptop both a wireless and normal lan card.  Both are configured with DHCP and they receive their configurations without a problem from my router.  However, I cannot connect to any server (www, gaim, ...) beyond the router.  When I try to ping [www.google.com](www.google.com) I can see the address translation to IP is done OK but there is no ping reply.  All internet services work fine from WinXP (dual boot machine) so it has nothing to do with the router.

Does breezer come with a firewall (which I can't find) preconfigured or is there some other problem?

---

### Post by adwait on 2005-10-14
Ubuntu doesn't come with any firewall installed/enabled. Try pinging an IP address instead of a URL, does that work?

---

### Post by dbott67 on 2005-10-14
If you can ping an IP address (try 206.167.78.32 = [www.cbs.com)](www.cbs.com)), then it could just be a DNS issue.

Consumer-level broadband routers can occasionally have some issues that require a re-boot.  Try resetting your router (not to factory state, but just re-boot it):

1. Reboot router
2. Release & renew IP address on computer (or just re-boot it)
3. Login to router & confirm that the DSL/cable connection is active (i.e. you're logged on to your ISP)
4. Ping [www.cbs.com](www.cbs.com) or google.com (keep in mind that some sites do not accept ICMP ping requests)

-Dave

---

### Post by BungaMan on 2005-10-14
here's a quick update..

from my lan card (set as default card to use) I can ping the router, ping the lan card ip address but not the wireless card ip address

switching default card

from my wireless lan card (now set as default) I can ping the router, ping the wireless card ip address but not the lan card ip address

- pinging google works from within windows so it's not google blocking the ping 
- i doubt if it is a dns issue because pinging [www.google.com](www.google.com) brings up its ip address

please keep in mind that when i switch to windows xp everything works without touching the router.  it is not that they don't receive the gateway address either because a ping to google reveils the IP address.

It goes like this (copy paste from within windows now but it is the same result in ubuntu)
```
ping www.google.com

Ping www.l.google.com [66.249.93.99] with 32 bytes of data:
``` and then i wait and wait...

---

### Post by dbott67 on 2005-10-14
Can you post the output of:

```
netstat -r
```

This will display the routing table.  Can you post it for both Windows and Ubuntu?

Thanks,
Dave

---

### Post by BungaMan on 2005-10-14
hmm, it seems the problem can be solved by disabling one of the network cards... that doesn't make much sense.  They should be able to opperate when both are active

---

### Post by BungaMan on 2005-10-14
here's the output when both are enabled

~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.123.0   *               255.255.255.0   U         0 0          0 eth0
192.168.123.0   *               255.255.255.0   U         0 0          0 eth1
default         192.168.123.254 0.0.0.0         UG        0 0          0 eth1
default         192.168.123.254 0.0.0.0         UG        0 0          0 eth0

thanks for helping out

---

### Post by dbott67 on 2005-10-14
I had an issue where I work with multi-homed networks (in my case it was 2 NICs in each computer; each one pointed to a different network).  Whenever someone accessed resources on network 'A' first, they would not be able to access resources on network 'B'.  It was also Windows, not Linux.  I wrote a script that basically set the default route for the computer and since then, I haven't had any issues.

Your case is slightly different --- 2 NICs on the same network.  I'm not sure how linux handles this.

Glad you figured out that disabling 1 can get you up & running.

-Dave

---

