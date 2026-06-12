---
title: "Where'd my desktop go?????"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by nitroguy on 2009-09-16
I just installed xubuntu 9.04 on my old laptop. I click the red arrow up top declaring I need to download and install updates. 169 updates, and half hour later, I restart, to be greeted by a light blue sreen and my mouse - and that's it.

I can do alt+f2 and launch firefox, or alt+f4 to shut down, but can't right click on the desktop and have anything happen. And there's no bars top or bottom, and no icons. Anyone else have this problem?

I tried alt+f2 then startx, and it errored.

Please help.

---

### Post by ~sHyLoCk~ on 2009-09-17
Check your /var/log/Xorg.0.log

---

### Post by Mike_IronFist on 2009-09-17
> **nitroguy said:**
> I just installed xubuntu 9.04 on my old laptop. I click the red arrow up top declaring I need to download and install updates. 169 updates, and half hour later, I restart, to be greeted by a light blue sreen and my mouse - and that's it.

I can do alt+f2 and launch firefox, or alt+f4 to shut down, but can't right click on the desktop and have anything happen. And there's no bars top or bottom, and no icons. Anyone else have this problem?

I tried alt+f2 then startx, and it errored.

Please help.

Ah yes. This same problem happened to me with the GNOME desktop (regular Ubuntu, as you likely know) and I was worried that I'd have to re-install. I don't know if the problem has the same cause as mine did, so I'll spare you the details for now.

First, try to create a new user and see if the problem persists for that user account. press alt+f2 and type:
gksudo user-admin

Let me know what happens if you login as a different user, even Guest.

---

