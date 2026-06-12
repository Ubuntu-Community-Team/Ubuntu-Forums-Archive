---
title: "trouble with ndiswrapper"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by kanh on 2008-01-07
I have a fresh install of 7.10 and am trying to get encrypted wireless to work with Linksys wpc11 v 5 card.  I'm having trouble w/ ndiswrapper.  When I run ndiswrapper -v I get the line.  "couldn't create /etc/ndiswrapper/net8180: permiission denied at /usr/sbin/ndiswrapper-1.9 Line 152. I installed ndiswrapper using Synaptic Package Manager which loaded the files from my Gutsy CD.  I've also tried using the ndisgtk to no avail.  I have the driver on my desktop.  Anyone have any ideas?

---

### Post by adasilva on 2008-01-07
did you try using
```
sudo ndiswrapper -v
```
in my (very limited) experience, usually permission is denied when the command requires superuser privileges.

---

### Post by kanh on 2008-01-10
I've tried installing several drivers for the linksys wpc11 card and they all are all "invalid drivers".  Seems that ndiswrapper doesn't like any of them but they're the ones for my card....The version I'm using is the release on 7.10,

---

### Post by kanh on 2008-01-11
I got my wireless card to work!  I reinstalled ndiswrapper and ndisgtk using the packages downloaded using the links on the Ubuntu site and not from my 7.10 CD.  I also went back to Realtek and downloaded the WINXP driver again.  Guess that did the trick.

---

