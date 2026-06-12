---
title: "CRD grey screen lightdm"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by petermoffat on 2014-09-24
I'm trying to Remote Desktop into my media server, which has lightdm installed, however, after getting to a login screen and entering username and password, I get a grey x session with x cursor. I'm almost sure it's a configuration issue and drop doesn't know to use lightdm, but I have no idea what to put in /etc/xrdp/startimg.sh...

---

### Post by petermoffat on 2014-09-24
Sorry, title should read xrdp..

---

### Post by petermoffat on 2014-09-24
Never mind, solved it. I installed xfce and use that for xrdp. Got the server stuck in a login loop for my user, but figured out the chown .Xauthority from a quick search and sorted it.

---

