---
title: "Bluetooth File Sharing"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by kamuz on 2007-10-02
Hello

First, i don't have problems sharing files between my bluetooth phone and my computer. My question is, where can i modify the default location of the files received? I'm using the Bluetooth File Sharing 0.8.0 that comes with the official ubuntu bluetooth package. Anyway, everything is saved to my Desktop and i really want to choose another path as it can be a chaotic to transfer 100+ pictures at once.

Thank you.

---

### Post by rundee_f on 2007-10-09
hi,,

and where can i install bluetooth file sharing??

---

### Post by reaganf2 on 2007-11-29
got the same question... any way i can change the default save directory....??

---

### Post by onno-itmaze on 2008-01-24
After finding out that the Bluetooth File Sharing Accessory is part of gnome-obex-server I had a look at the strings embedded in the /usr/bin/gnome-obex-server binary.

This is how I changed the destination for this tool.
[LIST=1]
[*]Launch gconf-editor
[*]Browse to /apps/gnome-obex-server
[*]Modify savedir to reflect the preferred destination
[*]Close gconf-editor
[/LIST]

Warning: If this breaks your machine, you get to keep both parts.

---

