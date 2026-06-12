---
title: "Linux Hardware recognition. HOW?"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by Zacinfinite on 2010-09-05
How do flavors of Linux like Knoopix and Ubuntu detect most types of hardware and make them work perfectly, although being small is size?
Certainly you cannot just write device drivers for each and every hardware otherwise size of OS will become enormous.
Whats the secret?

---

### Post by mcduck on 2010-09-06
The secret is that most of the hardware around actually uses same components.

For example network cards; in Windows each network card manufacturer makes their own drivers for each of their own models, while in Linux you only have one driver for the actual network chip used in those cards, and that driver is able to work with every network card that uses that particular chip, regardless of the manufacturer of the card.

Of course you could do the same in Windows, but companies seem to prefer binding their drivers to their own card models instead of working together with their competitors. Later Windows versions actually are able to use a fair amount of hardware without installing any extra drivers.

The high usage of shared libraries and code of course helps keeping the required amount of code small, not to mention the fact that every driver doesn't have to include installer, GUI tool for configuration, and stuff like that as the tools already present on your system can be used instead.

---

### Post by coffeecat on 2010-09-06
> **Zacinfinite said:**
> Certainly you cannot just write device drivers for each and every hardware otherwise size of OS will become enormous.

You'd be surprised. Have a look in /lib/modules. You'll find one folder for each installed kernel. Within each of those folders is a vast number of loadable modules - these are the kernel drivers. Now look in /lib/firmware where you'll find an impressive number of firmware files.

Linux distros also come with CUPS, which is the engine for printing. Included in a default install is an enormous number of printer drivers, but I've not been able to find all of them - somewhere in /usr/share I think. Lastly, there are the open source xserver video drivers.

Each driver is only kilobytes in size. But I agree it is impressive how much is included.

---

