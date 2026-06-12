---
title: "Wired connection keeps dropping!"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by talz13 on 2007-02-16
Last week I noticed that I could no longer connect to my server over the network.  Everything is wired, so it wasn't a wireless problem.  I couldn't ping the machine and all the network shares went down.

I went over to the machine itself and checked out the network status.  Well, it had an IP address, but it wasn't the one I gave it!

I have all my machines configured with static IP addresses, none overlapping or anything, and here my server is pulling a DHCP address!  Needless to say, it's hard to find the machine on the network when you're looking in the wrong place...

I went into the network panel and checked that it still had staic IP set, which it did, and went back and hit apply.  It started up with its static IP again, and all was well until it decided to switch to DCHP again not more than a couple hours later!  The interfaces file even explicitly stated "static" by eth0...

After fighting with trying to get it to stay on the static IP that I wanted it on, I gave up and tried setting it to DHCP.  I went into my router and made a static DHCP for my server's MAC address so that even if it was getting DHCP, it would get the right address.

Well this worked for a while, but now, every once in a while, it just completely loses its IP address.  I mean, I'll do an ifconfig, and it just won't have an IP listed for eth0!  (I mainly notice that when my mac starts throwing fits about lost network locations)

Here's my /etc/network/interfaces right now:
```
auto lo eth0
iface lo inet loopback

iface eth0 inet dhcp
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1

```

As you can see, it still has the address and everything from when it was set up as static, but is currently reflecting dhcp in the iface line (which is ok right now).

Is my network card dying?  Are aliens playing with my mind?  Is it simply a configuration error somewhere?

---

### Post by Floppyjoe on 2007-02-16
I have not yet seen the interfaces file set up the way you have it here:
```
auto lo eth0
iface lo inet loopback

iface eth0 inet dhcp
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1
```

Usually it would look like this:
```
auto lo 
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#address 192.168.1.5
#netmask 255.255.255.0
#gateway 192.168.1.1
```

---

### Post by talz13 on 2007-02-16
That is just how it came up after switching back and forth using the network settings applet

---

### Post by talz13 on 2007-02-25
I'm trying to pinpoint some of these occurrences in time, but all I've found so far are incidents where it appears that the server can't get a DHCP address for an extended period of time:

```
Feb 24 12:04:30 server dhclient: bound to 192.168.1.5 -- renewal in 228 seconds.
Feb 24 12:08:18 server dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Feb 24 12:08:57 server last message repeated 3 times
Feb 24 12:10:11 server last message repeated 4 times
Feb 24 12:11:00 server last message repeated 3 times
Feb 24 12:12:07 server last message repeated 4 times
Feb 24 12:13:10 server last message repeated 4 times
Feb 24 12:13:17 server dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Feb 24 12:13:49 server last message repeated 2 times
Feb 24 12:14:17 server last message repeated 3 times
Feb 24 12:14:32 server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 24 12:14:39 server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Feb 24 12:14:48 server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Feb 24 12:14:59 server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Feb 24 12:15:13 server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Feb 24 12:15:28 server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Feb 24 12:15:28 server dhclient: DHCPOFFER from 192.168.1.1
Feb 24 12:15:28 server dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Feb 24 12:15:28 server dhclient: DHCPACK from 192.168.1.1
Feb 24 12:15:28 server dhclient: bound to 192.168.1.5 -- renewal in 278 seconds.
```

Looks like it loses its IP for somewhere between 10 minutes and who knows how long, until it obtains an address again.

It looks like there are some strange things in my samba logs, that shouldn't be there:
```
[2007/02/08 15:45:16, 0] lib/util_sock.c:get_peer_addr(1225)
  getpeername failed. Error was Transport endpoint is not connected
[2007/02/08 15:45:16, 0] lib/util_sock.c:get_peer_addr(1225)
  getpeername failed. Error was Transport endpoint is not connected
[2007/02/08 16:20:01, 0] lib/util_sock.c:get_peer_addr(1225)
  getpeername failed. Error was Transport endpoint is not connected
[2007/02/08 16:20:01, 0] lib/util_sock.c:get_peer_addr(1225)
  getpeername failed. Error was Transport endpoint is not connected
```

---

