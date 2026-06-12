---
title: "ASUS X550c needs wireless enabled"
date: 2014-05-25
forum: Networking &amp; Wireless
---

### Post by robertfickel on 2014-05-25
I have tried many different things to enable the wireless on this laptop;

1. ran "rfkill list all" and all I got back was the wireless called was "Hard blocked" with the answer "yes" on the 0: phy0: Wireless LAN
2. I have tried the FN+F2 keys and still remains the same.
3. I have ran a "rfkill unblock all" and got no change.

Any idea where to go from here?

---

### Post by praseodym on 2014-05-25
Hi,

add this module parameter:

```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```
Reboot and check the buttons.

---

### Post by robertfickel on 2014-05-25
Tried the above... came back with "file or dir not found" I did how ever read another post that stated I could hit FN+F1 and then resume, and wireless would be enabled. That worked, of course I have to do each time I boot, but at least it is working until a patch comes out to fix the problem.  Thank you for taking the time to help!

---

### Post by praseodym on 2014-05-26
Typo? Try that command (its one line!) by copy/paste.

---

