---
title: "Is Avahi necessary?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2009-05-03
I have been checking out my Firestarter log and noticed a ton of hits on the port running the Avahi process.  In fact, it is a process running under root.  I know it is included in the Distro, but what are the inherent dangers of having it?

I get about 100 blocked probes a day trying to hit the port.

Thanks in Advance

---

### Post by nandemonai on 2009-05-03
> **J0hnnyBr@v0 said:**
> I have been checking out my Firestarter log and noticed a ton of hits on the port running the Avahi process.  In fact, it is a process running under root.  I know it is included in the Distro, but what are the inherent dangers of having it?

I get about 100 blocked probes a day trying to hit the port.

Thanks in Advance

From wiki:

> Avahi is a free Zeroconf implementation, including a system for multicast DNS/DNS-SD service discovery. It allows programs to publish and discover services and hosts running on a local network with no specific configuration. For example, you can plug into a network and instantly find printers to print to, files to look at and people to talk to. It is licensed under the GNU Lesser General Public License (LGPL).

Is it needed? I guess not if you don't want auto discovery of samba shares and the like. Inherent dangers? Minimal I'd say, unless you want to stealth yourself on the LAN.

---

### Post by J0hnnyBr@v0 on 2009-05-03
> **nandemonai said:**
> From wiki:



Is it needed? I guess not if you don't want auto discovery of samba shares and the like. Inherent dangers? Minimal I'd say, unless you want to stealth yourself on the LAN.

Thanks for the feedback.  I saw that on wiki too, but was undecided.  Wondering if people are just curious about the port number (no services are listed for that specific port) and are trying to further probe for more info.

Just wasn't sure with it being a root process, etc. That I may be opening myself up to potential exploitation.

Thanks,
Eric

---

