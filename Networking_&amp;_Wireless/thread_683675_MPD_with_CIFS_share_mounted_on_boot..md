---
title: "MPD with CIFS share mounted on boot."
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by danbee on 2008-01-31
Hi guys, I've got an interesting problem that's been niggling me for a while now.

I use MPD to play music on my desktop machine, and it's configured to look at a CIFS share that mounts on bootup.

The problem is that, although the CIFS share mounts ok and is available when I log in, it doesn't seem to be available in time for MPD to find the directory of music on it and MPD fails to start. Therefore I end up having to start MPD manually every time I boot the machine up.

I've tried fiddling with the bootscript priority using update-rc.d and figured the script waitnfs.sh might be what I'm after but I can't get it to work.

---

