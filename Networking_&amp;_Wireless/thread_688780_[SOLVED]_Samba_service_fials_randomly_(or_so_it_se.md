---
title: "[SOLVED] Samba service fials randomly (or so it seems)"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by ryanVickers on 2008-02-05
I finally got my network working*, but there's a snag: [SIZE=1][COLOR=Silver]*Folder on Linux box read/writable by all Linux and Windows on LAN (this is good FYI)

[/COLOR][/SIZE]The access to the folder, from any OS, even on the host computer, seems to randomly stop working.  Usually after a hibernate, but when everything comes back online, should Samba not as well?? :confused:

I have also tried running "sudo /etc/init.d/samba start" and "sudo /etc/init.d/samba reload" - no help.

Any ideas? ](*,)

---

### Post by ryanVickers on 2008-02-05
No one has any clue... wow
Usually people are just jumping on the toughest things and they're done by now :p

---

### Post by ryanVickers on 2008-02-06
Ok, I think I solved it: turns out the Samba service was fine all along, which makes sense, but Firestarter had something to do with it I think... It was off all the same, but ... :confused: oh well, it works now :D

---

### Post by bigken on 2008-02-07
the correct command is [B]

sudo /etc/init.d/samba restart

[/B]anyhow pleased you solved your problem[B] :)
[/B]

---

### Post by ryanVickers on 2008-02-07
yea, I had tried all of them, but it was no help, must have been firestarter... ;p;

---

