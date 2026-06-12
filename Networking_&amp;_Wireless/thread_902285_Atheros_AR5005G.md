---
title: "Atheros AR5005G"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by MiguelCosta on 2008-08-27
hi there!

I'm using ubuntu since feisty and since then I always had issues with my wireless card! Having problems I always solved them by using the acer_acpi available on google code.

Now with the 8.04 I can't do it anymore and the pages on google code tell me that it is shipped with ubuntu! My wireless still doesn't work...

I'm trying to compile a source I found for it but I can't eithe! Can anyone help??

---
EDIT / UPDATE
---

I managed to compile the source afterall. If I enable the feature with echo 1 > /proc/acpi/acer/wireless and then reboot, the wireless will work. The problem is that when I boot from shutdown the module won't have the feature active. How can I get it to activate during boot?!

---
2ND UPDATE
---

Managed to make the led turn on during boot. It should also enable the wireless but it doesn't! I still need to reb00t! I followed this instructions with little changes:

[http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi](http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi)

The only thing I changed was:

removed the "enable:" and only left the number or it wouldn't work! apart from that didn't change a thing...it should work..but it doesn't! anyone has the answer?! :)

---

### Post by MiguelCosta on 2008-08-27
tried to change the runlevels..but it still only works after the reb00t...

please help!

---

### Post by MiguelCosta on 2008-09-02
couldn't solve it yet! can anyone help?!?!PLEASE!

---

