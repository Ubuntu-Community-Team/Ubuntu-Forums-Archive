---
title: "Upgraded - Wifi don't work :("
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by tegguN on 2008-04-27
Just upgraded to hardy, wifi no longer works, I can see networks but can't connect. No light on the LED. Using an Intel 3945abg card.

One of the error messages in a log file:

Apr 27 13:19:31 *****-laptop kernel: [  282.546194] eth1: privacy configuration mismatch and mixed-cell disabled - disassociate

Can I downgrade to 7.10? This is pretty poor.

---

### Post by chili555 on 2008-04-27
There are a couple of long posts about the 3945ABG, especially post #33 here: [http://ubuntuforums.org/showthread.php?t=765647&page=4](http://ubuntuforums.org/showthread.php?t=765647&page=4)  Try it and let us know.

---

### Post by felker2 on 2008-04-27
After my upgrade, my WEP-connection was not working anymore (Centrino Wifi onboard). I could make a new WPA2-connection, though.

Workaround 1: I've put in a Orinico PCMCIA card, and thay way I can connect to my WEP AP.

Workaround 2: Use an older kernel (2.6.22, not 2.6.24) from the boot menu. See [https://bugs.launchpad.net/ubuntu/+bug/223111](https://bugs.launchpad.net/ubuntu/+bug/223111)

---

