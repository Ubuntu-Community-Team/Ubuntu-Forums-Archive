---
title: "blacklist iwl3945"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by ethanay on 2008-03-27
Hello,

Does anyone know how to successfully blacklist iwl3945?  I have it in my /etc/modprobe.d/blacklist file:

blacklist iwl3945
blacklist mac80211

but it still loads the kernel modules on startup....which is telling me that the blacklist additions aren't working.

I tried IWL3945 from IPW3945 and it was more buggy so I switched back, but haven't been able to permanently unload the iwl3945 driver... :mad:

Ethan

---

### Post by chili555 on 2008-03-28
Is iwl3945 still listed in /etc/modules? If so, please edit the file to remove it. You will probably then have to reboot to see if it worked or if we must look elsewhere.

---

### Post by ethanay on 2008-04-25
ahh, it was listed there!  i am in the middle of a backup operation, but will assume that it does the trick.  thank you very much!

ethan

---

