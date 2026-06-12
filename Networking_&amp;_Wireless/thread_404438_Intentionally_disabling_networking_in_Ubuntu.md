---
title: "Intentionally disabling networking in Ubuntu?"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by Valatar on 2007-04-08
I was in a discussion about secure work environments for people handling sensitive data and brought up live CD environments as being invulnerable to everything short of a hardware keylogger or an active network intrusion, which lead me to wonder just what would be necessary to cut Ubuntu completely off from any attempt to activate network cards.  No attempts to get an IP address, no APIPA, just completely isolated from any networks.

Assuming the user doesn't manually yank any cables or antennae from the computer, the obvious but kinda dirty solution, does anyone know what would need to be modified to disable the networking features on the live CD?

---

### Post by heimo on 2007-04-08
> **Valatar said:**
> Assuming the user doesn't manually yank any cables or antennae from the computer, the obvious but kinda dirty solution, does anyone know what would need to be modified to disable the networking features on the live CD?

How about custom kernel without network stack, no loadable module support and no support for any network devices?

---

### Post by Valatar on 2007-04-08
That would certainly do the trick, but mucking around with kernel compiles is head and shoulders above my level.  I don't suppose the network drivers are all in one easily-deleted location?

---

### Post by heimo on 2007-04-08
> That would certainly do the trick, but mucking around with kernel compiles is head and shoulders above my level. I don't suppose the network drivers are all in one easily-deleted location?
I'd guess that lots of them are in loadable modules under /lib/modules, some may be compiled into kernel binary. Simplistic solution might be to let all those be as is, and just setup the live-CD to not bring up any network interfaces (perhaps other than lo). That should probably be enough, and quite easy to do (wouldn't break many / any programs).

---

