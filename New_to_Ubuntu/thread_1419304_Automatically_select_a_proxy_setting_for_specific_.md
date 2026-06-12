---
title: "Automatically select a proxy setting for specific wifi network?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by sleepee on 2010-03-01
ok, this might be somewhat of a dumb question, because i'm sure there's a very simple answer, but ill ask anyway because i searched the forums and really didn't find an answer...

so here's the deal...
i frequently travel to and from my home and college.  i've got my network preferences set up so that when i'm at home, it automatically connects to my home network, and when i'm at school, it connects to their network automatically too...

now, at my college, we use a proxy, and at home i don't..  so in network proxy preferences (system -> preferences -> network proxy) i created two "locations": home (no proxy), and school (uses proxy)

so what i'd love is for the proxy location to automatically be set according to the network i'm in..
For example, when i'm in my home network, set the proxy location to "home" (and therefore use no proxy), and when at my college campus, set the proxy location to "college", and use those proxy settings.
Is there a way to do this so i don't have to manually set the proxies every time i change a network?

---

### Post by 121Lazz on 2010-03-16
-bump-
exact same problem here

---

### Post by aeiah on 2010-03-16
have a look at wicd, i believe it allows you to launch a command upon connection (and disconnection etc). this command could be to set the proxy, for instance.

---

### Post by 121Lazz on 2010-03-16
no thanks, spent all day yesterday getting wifi to work, WICD didn't function at all.
I believe /etc/network/if-up.d can be used to execute scripts after the connection has been brought up, but I'm not sure how.

---

### Post by sleepee on 2010-03-17
> **121Lazz said:**
> no thanks, spent all day yesterday getting wifi to work, WICD didn't function at all.
I believe /etc/network/if-up.d can be used to execute scripts after the connection has been brought up, but I'm not sure how.

noobie question here:

what is wicd??  and how does it work?

---

