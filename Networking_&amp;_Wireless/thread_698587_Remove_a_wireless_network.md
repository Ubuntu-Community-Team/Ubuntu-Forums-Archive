---
title: "Remove a wireless network"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by JeSTeR7 on 2008-02-16
I once connected to an AP with the essid "linksys" and would like to remove it.  Now, everytime there is a network with that name (and there are a lot of them) the computer tries to connect to it first.

Is there any way to remove previously connected ESSIDs?

---

### Post by ethanay on 2008-04-03
wow, no replies for this one?

I'd like to know the answer, too...

ethan

---

### Post by ethanay on 2008-04-03
found a way, via here:

[http://ubuntuforums.org/showthread.php?t=299367](http://ubuntuforums.org/showthread.php?t=299367)

but it isn't very user-friendly at all...that's a feature request for the network-manager team at launchpad!

I had success w/this by disabling all networking, and the radio via the rfkill switch, and then opening the gconf-editor and deleting each key within each separate network.

It crashed on me once through the process, and was overall more tedious than it should be.

---

