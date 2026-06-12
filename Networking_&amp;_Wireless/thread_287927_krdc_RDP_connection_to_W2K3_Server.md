---
title: "krdc RDP connection to W2K3 Server"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by Thund3rstruck on 2006-10-29
For whatever reason this krdc tool in kubuntu errors out when trying to connect to my W2K3 server through RDP.

I've tried every variation I can think of:
rdp:/192.168.1.1
rdp:/192.168.1.1:0
192.168.1.1:0

And I've tried all the color depths as well but still nothing. Remote desktop from XP and Ubuntu 6.01 works fine. 

Any ideas?

---

### Post by Thund3rstruck on 2006-10-30
Still cannot get this to work. Does anyone know of a remote desktop app for KDE that works (the one included with Gnome works great but I don't want to install Gnome)

---

### Post by Thund3rstruck on 2006-10-30
This one works correctly: rdesktop

```

$ rdesktop -a 24 192.168.1.1

```

---

