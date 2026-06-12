---
title: "Wireless not connecting on startup"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by artjermyn on 2008-11-01
I have a broadcom 4328 wireless card.  When my computer starts it has no wireless.  I do :

sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl

and boom it works.

I put the b43 b44 and ssb in the /etc/modprobe.d/blacklist file but when I reboot, I still have to enter the commands above to get my wireless working.  Anyway to automate the process or did I put the blacklist in the wrong file?

Thanks,
art

---

### Post by artjermyn on 2008-11-01
Sorry about replying to my own post, but it seems I found a solution.  After blacklisting the drivers, I ran:

sudo update-initramfs

Boom.  Worked like a charm.  I guess the image needs to be rebuilt after adding to the blacklists.

art

---

