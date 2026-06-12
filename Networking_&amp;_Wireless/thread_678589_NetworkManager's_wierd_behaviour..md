---
title: "NetworkManager's wierd behaviour."
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by TRANQU111TY on 2008-01-26
The first problem is NetworkManager does not save all my settings (password, WPA2, TKIP etc...) when I reboot.

Second, when I boot up Ubuntu, it always tries to connect the first time but fails, but on every second attempt it is successful. 

These little things are bugging me could someone help please :)

---

### Post by TRANQU111TY on 2008-01-26
For some strange reason the settings were saved for the first time and hopefully not the last. How do I disable the keyring password thing that pops up before nm-applet can connect to the net?

---

### Post by RebounD11 on 2008-01-26
Go to System -> Administration -> Keyring Manager and remove the entry from there. I guess this could do it. Hope it doesn't break anything (or better said you don't lose an important password) this way.

Good luck.

---

### Post by TRANQU111TY on 2008-01-26
Ah now I see how it works. What I actually want is to keep the passphrase but stop the prompt for a password when I login to Ubuntu, which is similar to enabling automatic login for Ubuntu.

---

### Post by ugm6hr on 2008-01-26
> **TRANQU111TY said:**
> Ah now I see how it works. What I actually want is to keep the passphrase but stop the prompt for a password when I login to Ubuntu, which is similar to enabling automatic login for Ubuntu.

This was a solution for Feisty: [http://ubuntuforums.org/showthread.php?t=192281&page=11](http://ubuntuforums.org/showthread.php?t=192281&page=11)

However, I though Gutsy had this as default (it certainly did on mine).

Although someone has posted to say it doesn't work with auto-login.  Maybe that's your problem?

---

