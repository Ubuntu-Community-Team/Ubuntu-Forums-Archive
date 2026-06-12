---
title: "Disabling network from grub commandline?"
date: 2013-11-11
forum: Networking &amp; Wireless
---

### Post by cogset on 2013-11-11
I would like to know if there's a way to boot my system disabling the network during the boot phase,by using grub commandline options or otherwise editing the current boot line as found in /var/log/dmesg ```
BOOT_IMAGE=/boot/vmlinuz-3.0.0-20-generic root=UUIDxxxx ro quiet splash
```I know I could always add a script in rc.local but I'd like to know if this could be done from the grub menu,before even booting a freshly installed system.

---

### Post by nebileix on 2013-11-11
Try adding "nonet"?

Didn't really tried it b4. :p

---

### Post by cogset on 2013-11-12
OK,I will try this for you...BTW,where is this stuff documented? I reckon there are quite a few arguments that you can add to the grub commandline,but I couldn't find this **nonet **option anywhere.

---

