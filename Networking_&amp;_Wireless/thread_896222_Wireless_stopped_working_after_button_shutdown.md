---
title: "Wireless stopped working after button shutdown"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by Mozenrath on 2008-08-21
This is like the 3rd time this has happened to me since I've started using Hardy, and I'm getting tired of reinstalling the OS in order to fix it.

Today I needed to restart my computer, and I had Gedit open in one of the other workspaces (this was preventing me from logging out), but for some reason it wouldn't let me switch spaces or do anything.  So I decided that the only way to restart was to just press the button on my computer.

Now my wireless doesn't work at all.  Wireless doesn't show up at all in Network Manager, and the light on my wireless usb card just stays on. (Usually it starts blinking after the Hardware Abstraction Layer is loaded in the boot screen.)

The wireless card works perfectly fine when I boot off of my Gutsy live cd.

I'm using a Belkin USB dongle with the RT2570 linux driver from serialmonkey.

---

### Post by Mozenrath on 2008-08-22
Well if nobody has a solution for this, is there anyone out there that has the same problem as I do?

I'm going to wait another day and downgrade to Gutsy if nobody comes up with a fix.

---

### Post by ajlee on 2008-08-28
I had the same problem.

sudo apt-get check --fix-broken

fixed it for me.  Hope this helps.

---

