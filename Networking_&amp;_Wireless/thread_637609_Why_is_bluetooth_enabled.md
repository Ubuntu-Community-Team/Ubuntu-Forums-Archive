---
title: "Why is bluetooth enabled?"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by daniel_victoria on 2007-12-11
I have an old Fujitsu P2120 and I need to get it as clean as possible since it's not a very powerfull machine. I took a look at the loaded modules and bluetooth is loaded. The laptop does not have any bluetooth devices and I don't pretend to use any. So I tried to unload it using modprobe -r bluetooth and rmmod bluetooth but it says the module is being used. It's used by rfcomm and l2cap.

Is it safe to unload these modules? What are they used for? How can I unload them?
Thanks

---

### Post by bollix47 on 2007-12-11
Try going to System>Administration>Services.

Look for and remove the check beside Bluetooth.

---

### Post by daniel_victoria on 2007-12-11
Sorry, I forgot to mention that I'm using fluxbuntu so there is no system/administration/services options...

---

### Post by bollix47 on 2007-12-11
I'm not too familiar with fluxbuntu but you could try installing sysv-rc-conf via synaptic and see if it lists bluetooth.  Perhaps you can turn it off there.

---

### Post by daniel_victoria on 2007-12-12
Thanks,

I installed sysv-rc-conf and turned of bluetooth. On this laptop that I have I must free all ram necessary :) That's the problem with subnotebooks, especially old subnotebooks

---

