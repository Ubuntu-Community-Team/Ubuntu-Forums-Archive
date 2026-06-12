---
title: "upgrade 10.04"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by northicert on 2010-09-04
Out of range display. I'm logged in as a second user because I can't get past the blue death screen. I changed the refresh rate and it left me with a screen I can't use. Trying to reboot didn't make it default to old settings. I need to reset the refresh rate but don't know how. The second user log-on is fine. I've tried a few terminal commands but no success.

---

### Post by Brinstar on 2010-09-04
> **northicert said:**
> Out of range display. I'm logged in as a second user because I can't get past the blue death screen. I changed the refresh rate and it left me with a screen I can't use. Trying to reboot didn't make it default to old settings. I need to reset the refresh rate but don't know how. The second user log-on is fine. I've tried a few terminal commands but no success.

sounds like you just need to rebuild your xorg.conf, or try and restore the backup and restart the X server.

---

