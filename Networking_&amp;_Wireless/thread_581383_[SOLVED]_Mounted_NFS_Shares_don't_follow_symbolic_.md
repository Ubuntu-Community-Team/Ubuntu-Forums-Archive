---
title: "[SOLVED] Mounted NFS Shares don't follow symbolic links"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by jspangler on 2007-10-19
I recently set up a server for print and filing sharing. Setting up NFS and exporting folders was a piece of cake. Then I set up symbolic links on the server, in folders I was sharing. The reason is that i have an external drive. So, for example, I had a home folder called movies, and within that a symbolic link to the folder on my external usb hdd called movies. Navigating works fine in the server, but when I look at the mounted movies folder on my desktop computer, it shows the symbolic link to movies as a bad link, and tries to look for the folder on my own computer. Is there a workaround for this?

---

### Post by jspangler on 2007-10-19
I answered my own question! There's no real workaround. I had to also mount the external drive as an nfs share to the same point /media/(external drive) as on the server.

---

