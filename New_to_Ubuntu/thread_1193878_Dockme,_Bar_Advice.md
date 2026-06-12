---
title: "Dockme, Bar Advice"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by DeadlyAura on 2009-06-22
I've been looking at a couple dock bars, but so far none of them seem to do what I want.

Basically, I hate desktop icons. I would LOVE for all my desktop icons, and ONLY my desktop icons, to load in a dockbar that I can auto-hide off the side of the screen.

When I mount a volume, I want it to appear in my dockbar rather than on my desktop, this includes hard drives, Cds and DVDs, as well as USB devices. It would also be a fantastic place for my desktop shortcuts to certain apps.

The other option may be to remove the mounted volumes from the desktop. They must remain mounted at all times since they contain alot of data I constantly use.

Anyone have any thoughts on this?

Thanks!

EDIT: Sorry for the title, didn't realise I messed it up.

---

### Post by Elfy on 2009-06-22
You don't say what docks you have tried - might be worth letting people know that ;)

As far as mounted volumes on the desktop - you can hide them, that will also make USBs/DVDs you start stop showing on the desktop as well

Open gconf-editor - do Alt+F2 then run gconf-editor

Navigate to /apps/nautilus/desktop - then untick volumes_visible

I mount my drives in /mnt rather than /media - stops them showing on the desktop and then allow USBs etc to show - personal preference

---

### Post by DeadlyAura on 2009-06-22
> **forestpixie said:**
> You don't say what docks you have tried - might be worth letting people know that ;)

\

I haven't *tried* any yet. I've been looking at some of them and checking out features. Currently I have yet to find one that does what I want it to do.

---

### Post by DeadlyAura on 2009-06-24
Shaka-bump

---

### Post by treesurf on 2009-06-24
Gnome-Do/Docky will do most of that I think.  Getting it to appear on the side of the screen would take some tweaking, but it's probably doable.

---

### Post by fluxlizard on 2009-06-24
well since you haven't got a lot of response the past couple of days- have you considered just making a new panel, setting it to the left or right side of the screen, enabling autohide on it, possibling setting the background transparent, increasing the size so your icons are larger, and dragging the icons you want into it? 

grab ubuntu tweak from getdeb.net and use it to disable the mounted drive icons on your desktop. 

This doesn't make the mounted drives appear on the "dock" (panel), but you can always  find them under the places menu in the upper left corner of the screen and in the left column in nautilus.

---

### Post by cjv8888 on 2009-06-24
> **DeadlyAura said:**
> I've been looking at a couple dock bars, but so far none of them seem to do what I want.

Basically, I hate desktop icons. I would LOVE for all my desktop icons, and ONLY my desktop icons, to load in a dockbar that I can auto-hide off the side of the screen.

When I mount a volume, I want it to appear in my dockbar rather than on my desktop, this includes hard drives, Cds and DVDs, as well as USB devices. It would also be a fantastic place for my desktop shortcuts to certain apps.

The other option may be to remove the mounted volumes from the desktop. They must remain mounted at all times since they contain alot of data I constantly use.

Anyone have any thoughts on this?

Thanks!

EDIT: Sorry for the title, didn't realise I messed it up.

I think cairo-dock can do all the above with a bit of customising.

---

### Post by fabounet on 2009-06-25
Indeed, you can set Cairo-dock on the left or right side of your screen, activate the Shortcuts applet that will show your mounted points, their disk usage, and let you mount/unmount them with a mere middle-click.

---

### Post by Ptero-4 on 2009-06-30
You can create a panel and use the disk mounter applet to get your volumes like if it were a dockbar.

---

