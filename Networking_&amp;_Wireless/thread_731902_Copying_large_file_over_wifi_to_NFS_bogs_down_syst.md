---
title: "Copying large file over wifi to NFS bogs down system"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by EricDB on 2008-03-22
Copying medium-large files (300 megs or so) to my network storage is bogging down my computer to the point of uselessness.  Once the copy completes, the system returns to normal.  Here is some relevant information; I'll be happy to provide more if needed:

[LIST]
[*]Ubuntu 7.10 (2.6.22-14-generic) on a Dell XPS m1210 laptop with 2G RAM 
[*]Gnome is my desktop environment
[*]My wireless module is "ipw3945".
[*]I'm using WPA2 on my wireless router, and Wicd to connect.
[*]The NAS is a SimpleTech SimpleShare, wired to my wireless router.
[*]The line from fstab is:```
192.168.1.102:/shares/SimplePool/SimpleShare        /media/simple     nfs     defaults0       0
```
[/LIST]

---

### Post by Sam Lars on 2008-03-22
You might want to report this as a bug.

---

