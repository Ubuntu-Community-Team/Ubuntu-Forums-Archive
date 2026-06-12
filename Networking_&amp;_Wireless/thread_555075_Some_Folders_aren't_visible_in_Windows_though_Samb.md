---
title: "Some Folders aren't visible in Windows though Samba/Unionfs"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by apocalip on 2007-09-19
Hello!

I've got a problem here.
I user unionfs to merge 4 different Harddrives Virtually together with Partially the sam Folder Structure.
In Linux all of the Folders are visible in the Merged Folder.
But Through Samba on my Windows Machine there are some Folders missing. I can navigate Manually to these Folders by adding the Name to the address, but there are simply not visible.( BTW: I have the option to show hidden files in WIndows activated of course.) Has anyone have an idea why this is happening?

Greetz&Thankz aPo

---

### Post by touser on 2008-04-16
Sorry to bring back such an old thread, but i have the exact same problem. Is anyone else having trouble with this as well? I'm thinking of switching to aufs but the documentation for it is terrible for a regular user.

---

### Post by waster on 2008-04-24
you have to export every independent mount point. i think they can still appear as a single tree in the client machine.

---

