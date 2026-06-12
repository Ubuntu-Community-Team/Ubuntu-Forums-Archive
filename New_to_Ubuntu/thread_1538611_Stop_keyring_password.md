---
title: "Stop keyring password"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by KWLLC on 2010-07-25
I have just made the jump to use UBUNTU full time. Can I set an option somewhere to stop requiring a password/phrase for the keyring, Synaptic pkgmgr etc? My frame is in a secure location so there is no risk to doing this.

---

### Post by Res2216firestar on 2010-07-25
You can add stuff like:
```
NOPASSWD: /usr/sbin/synaptic
```
to the /etc/sudoers file. I would add it to the admin group line, although I seriously don't recommend doing this. If your computer was attacked, on or offline, it would make it a lot easier for a hacker compromise your system.

---

### Post by KWLLC on 2010-07-25
Good point...I gues I'll just live with it then. Thank you

---

