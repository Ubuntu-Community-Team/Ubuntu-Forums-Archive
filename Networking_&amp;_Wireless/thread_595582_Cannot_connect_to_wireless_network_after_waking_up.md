---
title: "Cannot connect to wireless network after waking up from sleep"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by samosamo on 2007-10-28
Feisty w/ ndiswrapper drivers for my bcm43xx.  When waking up from sleep I cannot connect to my wifi network.

Things I tried:
1) in /etc/default/acpi-support, I have added "networking" to STOP_SERVICES and then rebooted.  I tested this and it fixed the problem on one occasion.

2) I wrote a script to restart dbus after resuming from sleep, this worked well except for the fact that my Power Management preferences were reset.  I don't really know understand why.  I don't know what else this reset but I guess I'll find out.

3) Let's hear it!

---

### Post by Lambert on 2007-10-29
As a small suggestion and bump for your thread try adding the following in /etc/default/acpi-support file

```

MODULES="ndiswrapper"

```

---

