---
title: "How to keep dmfe from loading?"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by RembrandtQEinstein on 2007-07-27
dmfe is causing kernel errors. If I can get my computer to boot and run long enough I can unload it manually. I put 'blacklist dmfe' in /etc/modprobe.d/blacklist but on the next reboot it is loaded again. How do I get rid of it once and for all?

Thanks

---

### Post by RembrandtQEinstein on 2007-07-29
No ideas?

Sometimes after a reboot the system stays running long enough for me to manually unload it but it can take several reboots to do that. Also, when I try to debug other issues with dmesg, it is worthless because it is loaded with dmfe errors.

Any help on getting this out of the kernel or not loaded at all during boot would be very much appreciated.

---

