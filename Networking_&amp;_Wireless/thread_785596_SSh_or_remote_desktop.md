---
title: "SSh or remote desktop"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by jdelasalas on 2008-05-07
How can I remotely log into a laptop that is in a different town?  I have installed ssh and I noticed I have remote desktop.  Can I use either of those and how?  I want to log into this laptop to aid with the installaion of ndiswrapper.

---

### Post by Monicker on 2008-05-07
[https://help.ubuntu.com/community/VNCOverSSH]("https://help.ubuntu.com/community/VNCOverSSH")

EDIT: Just to clarify, the Remote Desktop which is integrated into Ubuntu is VNC. So you can skip the portion of the instructions above which deal with installing VNC Server on the host.

---

### Post by bluefrog on 2008-05-07
you can use either one, ssh being the fastest. In both cases, you need either ssh server to be installed on the target or remote desktop enabled.
You also need your target router to forward the corresponding ports (ssh 22, desktop 5900) to your target computer and you will need to know his public IP

---

