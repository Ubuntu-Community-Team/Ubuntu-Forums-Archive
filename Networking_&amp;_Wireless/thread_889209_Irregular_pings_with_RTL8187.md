---
title: "Irregular pings with RTL8187"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by impactdni on 2008-08-13
Having an interesting problem that I can't seem to trace down...

I have an Asus P5B with on-board RTL8187.  Running Hardy.

Connecting/general use through wireless works fine, however, there are occasional drops in speed/ping.

I've tried multiple wireless routers, and a few different USB cards to point it at the RTL8187.

Nothing gets logged in dmesg, or /var/log/messages, nothing noted in NetworkManager etc...

The connection doesn't seem to fully drop, but every 20s-60s I get pings that look like this:

64 bytes from 10.1.2.1: icmp_seq=3 ttl=127 time=2.44 ms
64 bytes from 10.1.2.1: icmp_seq=4 ttl=127 time=2.97 ms
64 bytes from 10.1.2.1: icmp_seq=5 ttl=127 time=2.37 ms
64 bytes from 10.1.2.1: icmp_seq=6 ttl=127 time=1.89 ms
64 bytes from 10.1.2.1: icmp_seq=7 ttl=127 time=1.41 ms
64 bytes from 10.1.2.1: icmp_seq=8 ttl=127 time=1.06 ms
64 bytes from 10.1.2.1: icmp_seq=9 ttl=127 time=2695 ms
64 bytes from 10.1.2.1: icmp_seq=10 ttl=127 time=1696 ms
64 bytes from 10.1.2.1: icmp_seq=11 ttl=127 time=698 ms
64 bytes from 10.1.2.1: icmp_seq=12 ttl=127 time=2.91 ms
64 bytes from 10.1.2.1: icmp_seq=13 ttl=127 time=1.31 ms
64 bytes from 10.1.2.1: icmp_seq=14 ttl=127 time=1.33 ms
64 bytes from 10.1.2.1: icmp_seq=15 ttl=127 time=1.10 ms

The normal ping is anywhere from 1-4ms (reasonable).  But every 20-60s 3 packets jump in ping times, the first is normally 2-3s, the second 1-2s, and the third is around 700ms.  

Using a different wireless card for the time being, does anyone know a reason this would be happening?  Or has anyone seen anything similar in the past?

- impact

---

### Post by impactdni on 2008-08-13
Update:
It also happens (but to a lesser extent) with a "Ralink 54M.USB" - just a crappy USB 54g card.

This one only spikes to 700ms once every 30-60s, instead of a multi-second spike...

Is it driver based?  Should I give ndis-wrapper a chance?

---

### Post by kbnessa on 2008-08-21
> **impactdni said:**
> I have an Asus P5B with on-board RTL8187.  Running Hardy.

Connecting/general use through wireless works fine, however, there are occasional drops in speed/ping.

I've tried multiple wireless routers, and a few different USB cards to point it at the RTL8187.

I have the exact same motherboard, hardy, and the same problem. :(
The spikes seem to come fairly regular at every 2 minutes.

Also maybe once a day the driver seems to 'crash', I loose connection entirely and can't associate with any AP. Removing the driver hangs, only solution is to reboot.

Too bad, because I bought this motherboard because of its (apparently) good linux support. I haven't tried it on windows though, so I don't know if it is the same problem there.

---

