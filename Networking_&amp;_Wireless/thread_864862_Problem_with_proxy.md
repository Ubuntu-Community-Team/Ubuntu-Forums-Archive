---
title: "Problem with proxy"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by no_silhouette on 2008-07-20
When i try to run Synaptic Package Manager, everything goes fine until I start downloading the files. When I do, I get this error message:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-16-386_2.6.24-16.30_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-16-386_2.6.24-16.30_i386.deb)
  Could not connect to [www.freebypass.net:8080](www.freebypass.net:8080) (69.80.224.68). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/3dchess_0.8.1-13_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/3dchess_0.8.1-13_i386.deb)
  Could not connect to [www.freebypass.net:8080](www.freebypass.net:8080) (69.80.224.68). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose-modules/virtualbox-ose-guest-modules-2.6.24-16-386_24_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose-modules/virtualbox-ose-guest-modules-2.6.24-16-386_24_i386.deb)
  Could not connect to [www.freebypass.net:8080](www.freebypass.net:8080) (69.80.224.68). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/4/4digits/4digits_0.8-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/4/4digits/4digits_0.8-1_i386.deb)
  Could not connect to [www.freebypass.net:8080](www.freebypass.net:8080) (69.80.224.68). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose/virtualbox-ose-dbg_1.5.6-dfsg-6ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/virtualbox-ose/virtualbox-ose-dbg_1.5.6-dfsg-6ubuntu1_i386.deb)
  Could not connect to [www.freebypass.net:8080](www.freebypass.net:8080) (69.80.224.68). - connect (111 Connection refused)


How do I remove the "www.freebypass.net:8080"?

Thank you.

---

### Post by Psicolonia on 2008-07-20
under gnome setting you have something called "Proxy Settings"
just clear it there.

---

### Post by no_silhouette on 2008-07-20
I also get that same message when I use the Add/Remove Applications

---

### Post by no_silhouette on 2008-07-20
> **Psicolonia said:**
> under gnome setting you have something called "Proxy Settings"
just clear it there.



Where do I find the gnome settings?

---

### Post by no_silhouette on 2008-07-20
I found it and got everything goin right again, thank you for the help.

---

