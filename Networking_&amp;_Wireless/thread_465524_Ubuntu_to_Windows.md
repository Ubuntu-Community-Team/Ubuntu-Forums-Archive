---
title: "Ubuntu to Windows"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by madmagic on 2007-06-05
ok so i found out that i can share, and my windows computer does see the linux shared folder (the said folder is a windows folder) but i cant seem to find out how to put a local user and password in. I am trying to connect from my windows laptop... help?

---

### Post by kevdog on 2007-06-05
Did you install samba on the ubuntu machine??

---

### Post by madmagic on 2007-06-05
> **kevdog said:**
> Did you install samba on the ubuntu machine??

yes its all there, i set every thing up, enabled the shared docs, ect...

---

### Post by robertpolson on 2007-06-05
To share files with windows, edit gksudo gedit /etc/samba/smb.conf

Change ;security = user to security = share

This is also the place to edit which folders you want to share

Then sudo /etc/init.d/samba restart

---

