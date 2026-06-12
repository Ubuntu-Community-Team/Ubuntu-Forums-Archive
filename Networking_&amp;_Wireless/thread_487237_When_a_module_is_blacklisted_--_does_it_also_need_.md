---
title: "When a module is blacklisted -- does it also need to be removed from kernel??"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-06-28
So if I add a module to /etc/init.d/blacklist, for example prism54usb, do I also have to remove the module from the kernel, such as
sudo modprobe -r prism54usb

Thanks :)

---

### Post by kevdog on 2007-06-29
bump

---

### Post by ruibernardo on 2007-06-29
I think that, after you have rebooted, the module will not be loaded. Now, if you still haven't rebooted, then it might still be loaded.

You can try to unloaded it if you don't want to reboot. Did not tested. Depending on the other modules it depends on, unloading it should work.

---

