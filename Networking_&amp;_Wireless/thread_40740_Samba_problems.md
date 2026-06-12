---
title: "Samba problems"
date: 2005-06-10
forum: Networking &amp; Wireless
---

### Post by rodneyorpheus on 2005-06-10
I'm trying to share files between my laptop and desktop machines, both running Ubuntu. I figured the easy way was to run Samba on the desktop and log in as a client from the laptop.

After some fiddling around I have it so that if I use smbclient on the terminal on the laptop I can log in and browse and copy files from the desktop, but when I try to do it with Nautilus I can see the shares, but can't see any files or folders on those shares. What am I doing wrong?

Rodney

---

### Post by rodneyorpheus on 2005-06-10
I found a quick & dirty solution in the end by simply installing the rather wonderful nautilus-share:

[http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil](http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil)

It just worked right away, no configuration needed at all... That's the way it should be. Now if it only worked with Zeroconf, Gnome networking would be a considerable amount easier!

Rodney

---

