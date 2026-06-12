---
title: "Setting Up Network Printer"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by ColCommunism on 2007-02-22
Hello.  I'm actually using Debian 4.0, but I hope it shouldn't make too much of a difference.  If it does, please let me know.  These forums are so much quicker and better than Debian's.

I'm trying to set up a network printer (specifically, a Canon MultiPass MP5350).  The machine that the printer is hooked up to is a Windows box.  I get through the graphical installation process just fine, but when it gives me a list of drivers, I'm stuck.  I have the correct driver, but if I click "Install Driver" and find it, it tells me that it's already installed.  The driver's not in the list of available drivers, though.

If there's any additional information you need, please tell me.

Edit: Oh yeah.  I'm running GNOME and if this is in the wrong place, feel free to move it.

---

### Post by gradedcheese on 2007-02-22
I would try restarting cups and then trying to add the printer again.  As root:

```

/etc/init.d/cupsys restart

```

I'm not sure, but that might force it to rescan the PPD directories and then offer you the driver.

---

