---
title: "sadms install hosed my samba"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by rollOver on 2007-01-25
I tried to install sadms under edgy and got all the way to realizing I would have to have a separate kdc and apt-get removed it. Now samba is hosed and I cannot find any info on what all sadms does to my system and how to undo the damage. Does anyone know? I did not use it to configure PAM btw.

---

### Post by rollOver on 2007-01-27
Got this fixed, there was no help here so I figured it out myself. The reinstall wiped my smbpasswd settings and I had an incorrect bind statement in my smb.conf that was causing nmbd to error out.

---

### Post by DrClaw27 on 2007-01-30
Did you uninstall sadms? If so how?

---

