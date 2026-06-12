---
title: "Wake on LAN &quot;umb&quot; functions?"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by njparton on 2007-11-02
OK, here's what I'm trying to do: setup a headless NAS device using ubuntu as the OS. It's set to sleep after 30 mins so I need to be able to wake it up from elsewhere within my home LAN (from a Windows PC).

My PCI-E NIC (Intel PRO/1000 PT) supports the "umbg" wake on lan functions.  If I do:

```
ethtool -s eth1 wol g
```

I can wake it up with a magic packet without a problem.  However I'd also like to wake it up with a TCP or UDP packet if possible. I'm hoping that one of the umb functions will let me do this?

However, if I do:

```
ethtool -s eth1 wol gumb
```

my ubnutu NAS will go to sleep for 2-3 mins and then just spontaneously wake up even though all other computers on the LAN are shutdown.  I'm assuming it's receiving a packet from my router that's waking it up?

My question: in addition to the g function, which of the additional "umb" functions do I also need to use to enable TCP and UDP broadcast wake ups but prevent spontaneous wake ups?

My other PC's are connected to the NAS via a gigabit switch which is in turn connected to a router.

Sending magic packets isn't a great solution for the other members of my household ;-)

---

