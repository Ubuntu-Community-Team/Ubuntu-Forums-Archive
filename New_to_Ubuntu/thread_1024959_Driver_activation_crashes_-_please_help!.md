---
title: "Driver activation crashes - please help!"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by unknownwarrior33 on 2008-12-29
Hey guys.  I'm trying to install this driver: 
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

The installer works great, but when I go into "Hardware Drivers" and try to activate it, the progress bar shows up for a little while and then closes without activating anything.  Rebooting didn't help; any ideas?

---

### Post by w4ett on 2008-12-29
What Card are you trying to install the driver for?  Did you try the restricted driver already available in Ubuntu?

---

### Post by unknownwarrior33 on 2008-12-29
It's an Ati Mobility RadeonX 1400.  Installing the drivers from the Ubuntu repository didn't help; now, it still crashes, but the drivers window thingy says "This driver was just disabled, but is still in use."  I would think that might mean it worked, but it didn't.

---

### Post by w4ett on 2008-12-29
Try removing and purging the previous attempted installs and try installing again.

```
sudo apt-get remove --purge xorg-driver-fglrx
```

---

### Post by unknownwarrior33 on 2008-12-29
When I remove it, it still appears in the list of drivers; probably because I originally installed it differently.  I uninstalled that version, so the only version that remains is the one I installed without synaptic, if I'm viewing this right.  When I try to activate that, it gets to 100% with "Downloading and installing driver", then crashes.  It might be good to uninstall that one, but I don't have a clue how I'd do that.

---

