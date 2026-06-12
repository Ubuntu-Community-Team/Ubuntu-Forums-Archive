---
title: "[SOLVED] Wireless icon on T60p not glowing...what's wrong?"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by IvanIvan on 2008-06-11
Hi!

I am having trouble getting my wireless to work.
The wireless lamp on my laptop is not glowing indicating that wlan is OFF (even though the wlan swtich on the lower side is turned ON).
What seems to be te problem?
How do I check if my drivers are working?

---

### Post by jbrown96 on 2008-06-11
Ubuntu switched to an immature driver with Hardy. The supported hardy version does not support the LED. You can install an updated version with ```
sudo apt-get install linux-backports-modules-hardy-generic
```
You will need to enable some extra repositories. You will need to add unsupported updates and maybe a couple more things on that page in Synaptic. Then reload the sources and install the package above. Restart and it should work. It worked on my T61p

---

### Post by IvanIvan on 2008-06-12
> **jbrown96 said:**
> You will need to enable some extra repositories. You will need to add unsupported updates and maybe a couple more things on that page in Synaptic.
what extra repositories and unsupported updates?

**edit: working! thanks!**

---

