---
title: "Updates in kubuntu destroy system"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by edseagle287 on 2009-04-06
I've been a kubuntu user for almost a year now, and I've used the adept updater regularly with no problem. Last week, I ran updates that destroyed my xorg core, leaving me to boot into command line only. I reinstalled and ran the updates again, disabling the xorg update. The updates removed almost every application the install came with- amarok, dolphin, konqueror, etc., and the next time I booted my xorg core was again missing.  I reinstalled. Now the same updates have shown up, and I see that there are updates available for all of these applications, but for whatever reason adept chooses to remove instead of upgrading. I try to click the upgrade option instead of the remove option, but adept ignores. Is anyone else having this problem, and how do I fix it?

---

### Post by edseagle287 on 2009-04-06
I disabled the repository at deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main (needed for installing amarok 2) and found that this is the source of the bad updates. Does anyone know what's going on with this?

---

