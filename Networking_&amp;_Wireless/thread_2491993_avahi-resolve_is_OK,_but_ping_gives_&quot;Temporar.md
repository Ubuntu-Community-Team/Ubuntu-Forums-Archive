---
title: "avahi-resolve is OK, but ping gives &quot;Temporary failure in name resolution&quot;"
date: 2023-10-27
forum: Networking &amp; Wireless
---

### Post by pkeller1 on 2023-10-27
```

keller@pk-ubuntu-22-04:~$ avahi-resolve -n PT2026-00440.local
PT2026-00440.local    169.254.28.74
keller@pk-ubuntu-22-04:~$ ping PT2026-00440.local
ping: PT2026-00440.local: Temporary failure in name resolution

```

What gives? The failure does indeed seem to be temporary: after a **long** while, the "ping" starts working.

I have a clean Ubuntu 22.04 installation running under VMware. I am connecting to "PT2026-00440" with a point-to-point Ethernet connection to my monitor, which is connected to my computer via USB-C; this is seen as an Ethernet-over-USB adapter (USB CDC-ECM, "USB Communications Device Class – Ethernet Control Module subclass") and ends up creating a link-local network (hence the "169.254.xx.xx" IP address).

The same connection works without a hitch on macOS as well as Windows (oh shame!). I there any way to fix this delay?
Thanks in advance for any help!

---

### Post by TheFu on 2023-10-27
169.x.x.x addresses are placeholders, not real addresses.
Point-to-point connections require routing table entries on both sides of the connection, if one of them isn't a router.

If you setup A and B systems with a direct connection.
a) they need to be using GigE networking to use a standard ethernet CAT5e cable. 100base-tx or less connections need a passthru cable. It is part of the protocol for those slower speeds.
b) A needs to be told which interface to use to find B. This is a  manual command to setup on A.
c) B needs to be told which interface to use to find A. This is a  manual command to setup on B.

Without specifically telling each system which interface to use, it will see the other interfaces and routing table will be automatic for it.  Devices on the same LAN, usually something like 192.168.1.x, will not be sent to the gateway.  All other traffic will be, by default.  If you want 169.x.x.x traffic using a different interface, you need to tell it that through routing table additions and by setting the priority for the specific subnet to be higher than that for the gateway/router.

Name resolution can be performed using any of three methods. The order used is in the /etc/nsswitch.conf file.
[LIST=1]
[*]/etc/hosts (for small LANs)
[*]DNS (what the internet used and most corporate LANs)
[*]mDNS (avahi/zeroconf)
[/LIST]

I'll leave it to you to figure out which if these you'd like to use.  For just 2 systems, I'd use /etc/hosts, since it is 1 line added to each of 2 systems.
Of course, you can always use IP addresses, but then the IPs will need to be known. That isn't hard, if you set static IPs, but humans are better with names than numbers.

---

### Post by pkeller1 on 2023-11-13
Thanks for the reply, but what you're saying is not right: 169.254.x.x addresses are not placeholders; they're real IP addresses that have been auto-generated, rather than assigned in a routing table or via the DHCP protocol. Check out the [Wikipedia article on link-local addresses]("https://en.wikipedia.org/wiki/Link-local_address") for a good summary. One certainly does not need to (or in fact want to) muck with routing tables.

Here's the typical process for when you connect two systems with a direct Ethernet connection, supported out-of-the-box by all modern systems: both will ask for a DHCP server to assign them an IP address for their newly discovered interface. After some timeout period (typically around 30 seconds), they decide that's not going to happen, and they assign themselves an IP address, using link-local addressing. In Ubuntu, you can speed up the process by creating a profile that supports link-local addressing only (Settings -> Network -> <interface name> -> Gear Icon -> IPv4 -> Link-Local Only, ... IPv6-> Link-Local Only); with this, the address is assigned within a few seconds - very nice.

So that takes care of the IP address, but not the name resolution. That's handled by mDNS, described in [RFC 6762 "Multicast DNS"]("https://datatracker.ietf.org/doc/html/rfc6762") and handled in Ubuntu by [Avahi]("https://www.avahi.org/"). Again, no need to muck with routing tables - in fact, I would say that any static routing is to be strongly discouraged on any modern system.

As I said in my original post, the "avahi-resolve" command shows that Avahi's name resolution works great, pretty much immediately after plugging in the Ethernet cable. What seems to take an eternity is communicating that information to systemd-resolved, the daemon that provides name translation to clients like "ping", who (I assume) use the "getaddrinfo" API in glibc. [This article]("https://www.baeldung.com/linux/resolve-conf-systemd-avahi") gives a nice overview of all the actors.

What I don't know is whether - in Ubuntu 22.04 - systemd-resolved talks to Avahi to resolve mDNS, or whether it does that on its own (it's supposed to have its own mDNS resolver service). Who knows about the systemd-resolved configuration?

---

### Post by pkeller1 on 2023-11-13
OK, I have a partial solution, if anyone is interested:

- To examine the systemd-resolved configuration, one can use the [resolvectl status]("https://www.freedesktop.org/software/systemd/man/latest/resolvectl.html#status%20%5BLINK&#8230;%5D") command. In my installation, for the link corresponding to my direct Ethernet connection, above, I see:
[FONT=courier new]   Link 5 (enx0050c24241ba)
   Current Scopes: none
        Protocols: -DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
[/FONT]  I don't understand the difference between "-xxx" and "+xxx" on the "Protocols" line, but mDNS appears to be enabled. And it appears that systemd-resolved and Avahi handle mDNS completely independently.

- My name resolution appears to stop working when I connect a VPN. I assume that the systemd-resolved mDNS packages somehow get mis-routed, whereas Avahi is doing something more robust. If anyone understands this, your insight would be welcome.

---

