---
title: "Toshiba Satellite A20 - Ubuntu 10.10 - Display not filling screen"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by davinci28 on 2010-11-03
Good evening everyone. 

I'm new to Linux, and don't really know anyone who uses it, so I figured this is the best route to take for help...

I just installed Ubuntu 10.10, Maverick Meerckat, on my Toshiba Satellite A20 from a Live CD.  Install went perfectly, everything works as it should, except for the display.

The laptop supports a max. resolution of 1024x768.  In the "Monitors" settings under System>Preferences, the max. listed resolution is 800x600.

I have a feeling this may be a driver issue, but I was hoping someone can either confirm that and point me in the right direction, or suggest a different cause.

Thank you for your kind attention.

---

### Post by Zzl1xndd on 2010-11-03
If you have an ATI or Nvidia Card you will likely need to install the drivers.

Go to System > Administration > Additional Drivers to do so.

---

### Post by davinci28 on 2010-11-03
Running "lspci | grep VGA" in the terminal turns up that it has a Trident Microsystems CyberBlade XPAil (rev 82).

Additional Drivers confirms that "no proprietary drivers are installed on this device."

---

### Post by Zzl1xndd on 2010-11-03
Looks like an issue with the Card (honestly never heard of this make before). But it looks like these folks have solved it.

[http://ubuntuforums.org/showthread.php?t=1054304](http://ubuntuforums.org/showthread.php?t=1054304)

Hope this works for you.

---

### Post by davinci28 on 2010-11-03
Yep.  That worked like a charm.  Simple, quick...lovely.

Thanks a ton tweakedenigma!

---

### Post by Zzl1xndd on 2010-11-03
Glad I could help out and welcome to Ubuntu/Linux.

PS: you should mark this as Solved.

---

