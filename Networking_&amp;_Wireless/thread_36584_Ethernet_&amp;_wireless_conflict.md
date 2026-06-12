---
title: "Ethernet &amp; wireless conflict"
date: 2005-05-23
forum: Networking &amp; Wireless
---

### Post by MechR on 2005-05-23
It seems that being connected to ethernet and wireless at the same time causes neither to work (both connections are from the same router, if that matters... works in Windows though).  Is there a way to automatically resolve such conflicts in Ubuntu?

---

### Post by Sam on 2005-05-23
[QUOTE=MechR]It seems that being connected to ethernet and wireless at the same time causes neither to work (both connections are from the same router, if that matters... works in Windows though).  Is there a way to automatically resolve such conflicts in Ubuntu?[/QUOTE]
You can activate/deactivate interfaces in System / Administration / Networking

---

### Post by MechR on 2005-05-23
This is true, and I thank you :)  However...[quote=MechR]Is there a way to **automatically** resolve such conflicts in Ubuntu?[/quote]Not that manually switching is a huge bother, but it would be nice if Ubuntu could work it out on its own :)

---

### Post by anders.ostling on 2005-05-24
A package called NetworkManager (network-manager-gnome) does exaktly that, but unfortunately NM is hmmm "defunct" on Ubuntu. Works great though on Fedora & other RPM based systems. I guess we have to wait for the package to be ported to Ubuntu.

In the meantime, install a package call netapplet. It will give you a panel menu where you can select ethernet or wireless. Kind of a manual NetworkManager.

Anders

---

### Post by MechR on 2005-05-25
Ah, thanks for the info :)

---

