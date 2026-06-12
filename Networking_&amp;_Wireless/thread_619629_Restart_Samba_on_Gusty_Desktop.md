---
title: "Restart Samba on Gusty Desktop"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by itzabo on 2007-11-21
Where is samba hidden?:confused:

It sure isn't at /etc/init.d/

Every other linux box I use samba on has it there.
I have to reboot when I make changes to /etc/samba/smb.conf

Suggestions??

TIA

Robert

---

### Post by Blutack on 2007-11-21
My gutsy has samba at /etc/init.d/samba

Did you install the samba package?

---

### Post by mrmiserable on 2007-11-21
sudo /etc/init.d/samba restart

---

