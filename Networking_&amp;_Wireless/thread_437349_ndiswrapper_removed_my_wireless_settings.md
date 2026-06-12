---
title: "ndiswrapper removed my wireless settings"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by rgraves22 on 2007-05-08
I ran the ndiswrapper for the WUSB54GC card, to use the drivers supplied off of the CD. I rebooted and poof! 

When I do a lsusb, it shows my wireless card in there.. but its not under networking options...

Thoughts?

---

### Post by spd106 on 2007-05-10
May I suggest that you check ndiswrapper has been added to the list of modules that should be loaded at boot. The list is in the /etc/modules file.

You can check that it has been loaded by running this command
```
lsmod | grep ndiswrapper
```

If it fails to give any results then you will need to load it with this command
```
sudo modprobe ndiswrapper
```

---

