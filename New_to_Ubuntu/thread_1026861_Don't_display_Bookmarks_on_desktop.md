---
title: "Don't display Bookmarks on desktop"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by MockY on 2008-12-31
By default Nautilus is set to show volumes on the desktop when ever they are mounted. This is fine for thumbdrives and mp3 players, but I don't want network shares to show up when I mount them. To clarify, whenever a CD media is inserted or Flash drive is plugged in, I want it to show up automatically on the desktop (which it does). But I have plenty of network shares saved as bookmarks and whenever I click on them they are as well displayed on the desktop as *Networkfolder on ipnumber* (which it should since it is a mounted device so to speak), but I specifically don't want these to show up and clutter down my desktop.

Is this possible?

---

### Post by donkyhotay on 2008-12-31
I've never tried doing that myself but I found this other forum post which is similar to your issue, hope it helps.
[http://ubuntuforums.org/showthread.php?t=1026357](http://ubuntuforums.org/showthread.php?t=1026357)

---

### Post by fubbleskag on 2008-12-31
> **donkyhotay said:**
> I've never tried doing that myself but I found this other forum post which is similar to your issue, hope it helps.
[http://ubuntuforums.org/showthread.php?t=1026357](http://ubuntuforums.org/showthread.php?t=1026357)

note: this is an all-or-nothing switch, not specific to network shares etc.

---

### Post by MockY on 2008-12-31
> **fubbleskag said:**
> note: this is an all-or-nothing switch, not specific to network shares etc.

That is too bad. Whether Gnome will be implemented with such in the future is obviously unknown to me, but I would think that more people than me would like to separate them two (or use another method to access network shares) so hopefully it will work in the future.

---

### Post by FrankVdb on 2009-01-12
Not showing the volumes mounted is easy:

Press alt+F2 and open gnome-conf. Go to apps and scroll down to Nautilus. 

When unfolding that entry, you'll see a number of entries. Go to Desktop and check 'volumes invisible'.

This will remove all volumes. I know it's not what you want but I'm afraid we'll have to wait for it to be implemented.

I guess it's /schemas/apps/nautilus/desktop/network_icon_visible that we should be able to check or uncheck. Currently this is linked to the schema used.

---

