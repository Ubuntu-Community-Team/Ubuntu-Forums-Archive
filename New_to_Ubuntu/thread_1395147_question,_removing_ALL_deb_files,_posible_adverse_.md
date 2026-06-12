---
title: "question, removing ALL deb files, posible adverse affects? karmic"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by kronictokr on 2010-01-31
ive done this on a previous install , searched for the deb file using gksudo nautilus, the deleted them using shift del . it made my computer way faster, way faster. but i dont know if any of my programs need the debs to be installed. i wouldnt think so , but im not sure thats why im here. any help would be great:D

---

### Post by adam814 on 2010-01-31
If you mean the files in /var/cache/apt/archives you can safely delete them with "sudo apt-get clean", although I don't know how much that will help performance.

---

### Post by SuperSonic4 on 2010-01-31
The deb file is a glorified tarball really, it decompresses itself and puts the files in the right place. It is comparable to an exe file on windows

---

### Post by kronictokr on 2010-01-31
so once the program is installed the deb is useless, so it should be safe to remove them.
im going through the install log of that install, something i did increased my computer speed at least ten fold. trying to figure out what it was, had dual monitor 3d graphics blazing fast.
tx for the info!

---

