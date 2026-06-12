---
title: "Gigabyte X38-DS4 WOL problems"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by devurandom77 on 2008-04-15
Greetings.  I'm having trouble getting WOL (Wake on Lan) to work from S5 on my Gigabyte X38-DS4 motherboard.  I can make it work from S4 without too much trouble by:

First, enabling wakeup from PME in the BIOS.
Then
```
ethtool -s eth0 g
echo IGBE > /proc/acpi/wakeup
```

and finally suspending to S4 via

```
echo 4 > /proc/acpi/sleep
```
I can then trip wol with etherwake without any trouble.

However, if I enter S5 or do a normal shutdown, no luck.

Curiously, the IGBE entry in /proc/acpi/wakeup only shows a sleep state of 4:

```

Device  Sleep state     Status
PCI0       5            disabled
PEX0       5            disabled
PEX1       5            disabled
PEX2       5            disabled
PEX3       5            disabled
PEX4       5            disabled
PEX5       5            disabled
HUB0       5            disabled
UAR1       1            disabled
IGBE       4             enabled
USB0       1            disabled
USB1       1            disabled
USB2       1            disabled
USB3       1            disabled
US31       1            disabled
USB4       1            disabled
USB5       1            disabled
USBE       1             enabled
USE2       1             enabled
AZAL       5             enabled

```

My questions are:

1) Does this mean that wakeup is only supported from S4 or lower (I assume that's what this means.)

2) Is this value controllable via software, or am I at the whim of my BIOS here?  If this is the case, I can't find anything in the BIOS to change this, so I guess I'm left to contacting the vendor.

A quick browse of the kernel source makes it appear as though the underlying dev->wakeup.sleep_state value shown in /proc/acpi/wakeup comes from the BIOS and isn't changabe...

... and No, I do not have winblows XP to compare with.  Sorry. :)

---

