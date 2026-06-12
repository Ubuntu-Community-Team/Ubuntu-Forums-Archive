---
title: "Install from iso file"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by avcom on 2010-10-21
Yesterday, I downloaded an iso file and mount it. Inside the iso is an installer file. I run that file using terminal, but it said I need to login as root to install.

I tried sudo i, sudo su, sudo su-, gksudo nautilus, but nothing works. Because when I become root, I don't see the iso drive that I mounted.

So how can I install that?

Thanks

---

### Post by spiky001 on 2010-10-21
Is this a wubi install? or just a straight install no other os?

---

### Post by HarrisonNapper on 2010-10-21
Try switching to root first, then mount with the full path. I usually switch to a single root terminal using "sudo bash" then go from there. Remember that ~/ will not work as a shortcut to your home dir as root since it points to root's home.

---

