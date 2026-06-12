---
title: "[SOLVED] MAC Address, but no name for this Computer! ;)"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by Andavane on 2008-12-16
My friend has an internet cafe.
On his router ( A netgear ADSL Firewall Router)
I see the names of the other PC's, and the MAC Address of this obe,
and yet under device name there is "Unknown"
even tho in system / admin/system monitor settings the name of this machine is correctly displayed.

Any idea why?

regards

john

---

### Post by flanagan on 2008-12-16
As long as the results of these commands return the same host name, the router ought to pick it up:```
uname -n

hostname

cat /etc/hostname
```
You can edit the /etc/hostname file and reboot to change the hostname. If all that seems consistent on the Linux side and the router still does not pick up the name, perhaps the router itself is limited. Are all the other machines in the cafe running some variant of Windows?

---

### Post by Andavane on 2008-12-17
> **flanagan said:**
> As long as the results of these commands return the same host name, the router ought to pick it up:```
uname -n

hostname

cat /etc/hostname
```
You can edit the /etc/hostname file and reboot to change the hostname. If all that seems consistent on the Linux side and the router still does not pick up the name, perhaps the router itself is limited. Are all the other machines in the cafe running some variant of Windows?
Thanks.
The cafe owner is not here for a while, so will ask on his return.
In the meantime - yes all his machine are running some variant of windows,
except for one machine here (which is mine) and on that one I have windows XP dual booted with Ubuntu. 
I believe his route picks up the name of the machine (rajacre)when in Ubuntu;
will certainly revert soon, and with more info.

Regards

John

---

