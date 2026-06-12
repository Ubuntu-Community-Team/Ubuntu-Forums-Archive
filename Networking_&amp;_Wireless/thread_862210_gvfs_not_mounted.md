---
title: "gvfs not mounted"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by tigrezno on 2008-07-17
I bought a laptop and had ubuntu gutsy installed.
Upgraded with update manager to hardy 8.04

When I tipe mount, i don't see this line:
gvfs-fuse-daemon on /home/tigre/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tigre)

That line comes from my desktop.
Mplayer won't play anything over samba and i think this is the cause.
Totem works.

What can i do? I reinstalled gvfs related packages but it's the same.

[SOLVED]

i just deleted all the installation and reinstalled a fresh new hardy 8.04.
Now it's working correctly. Upgrading from gutsy seems to have bad sinergies.

---

