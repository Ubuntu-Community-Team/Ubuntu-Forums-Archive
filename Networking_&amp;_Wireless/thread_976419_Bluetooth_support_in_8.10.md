---
title: "Bluetooth support in 8.10"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by schlauf on 2008-11-09
Hi everybody,
I've installed Kubuntu 8.10 (AMD64) a few days ago. I'm pretty happy with the new desktop environment and the overall improvements involved herein. However, there's a specific issue I've been unable to resolve.

Bluetooth support appears to be somewhat broken. When trying to discover my mobile phone by running "hcitool scan", everything works fine and the bluetooth ID and identifier-string are reported. Trying to "sdptool browse" through the offered services of the reported device doesn't work, though. The command always returns a "connection timed out" error. This happened with two different bluetooth dongles, both of which are working flawlessly on another Kubuntu 7.10 installation.

Any advice of how to proceed? There appears to be no bluetooth environment for KDE 4.x available yet, too: entering "bluetooth://" in the address bar of Konqueror reports back an unsupported protocol error ... however, bluetooth service is started and working, as "etc/init.d/bluetooth status" tells me ...

Any help is greatly appreciated!
schlauf

---

### Post by peter_brewer on 2008-11-09
Hi

8.10 currently has broken bluetooth support.  It will be fixed at some point after its release - so soonish.

Hope this helps.

---

### Post by schlauf on 2008-11-09
Thx a lot, this information helps.

---

