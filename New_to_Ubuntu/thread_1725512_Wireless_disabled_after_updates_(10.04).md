---
title: "Wireless disabled after updates (10.04)"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2011-04-09
I have a Dell Inspiron 1050 and after updating Ubuntu today (for the first time in about 2 weeks) and I rebooted, I can't conenct to wireless internet.  All it says is "wireless disabled" and when I right click on the network applet, the area to re-enable wireless is greyed out.

---

### Post by TriBlox6432 on 2011-04-09
help please?

---

### Post by Norm Harding on 2011-04-09
> **TriBlox6432 said:**
> I have a Dell Inspiron 1050 and after updating Ubuntu today (for the first time in about 2 weeks) and I rebooted, I can't conenct to wireless internet.  All it says is "wireless disabled" and when I right click on the network applet, the area to re-enable wireless is greyed out.

I am having the same problem with 10.10. This is one of the two reasons I am sticking with windows as a backup. I have both ubuntu and windows in a dual boot setup, but wish I could resolve the wireless issue. I had the version before 10.04 and it worked fine. Then I updated to 10.04 and the "wireless" selection on the drop down menu was greyed out. I deleted Ubuntu and stayed with windows because of this. Now I have 10.10 and still the same problem persists. I love Ubuntu, but am disappointed in the lack of change here. I do not really know much about how to work this OS, and wish I could get help.

---

### Post by Norm Harding on 2011-04-09
BTW, I have a Dell Inspiron 1545 laptop with a Dell Wireless 1397 WLAN Mini-Card if that helps. :)
I have faith in the Ubuntu team!

---

### Post by wep940 on 2011-04-09
I would say it is likely that the update delivered a new kernel version and that wiped out your drivers.  If you had to do anything to install your driver in the past you will probably need to repeat that.
 
To see if a kernel update is to blame, at the grub boot menu select an older kernel version for boot and see what happens.

---

### Post by d3v1150m471c on 2011-04-09
try rebooting with the old kernel and see if that alleviates the problem. you can do so by holding shift at boot and selecting the second most recent kernel at the grub menu.

---

### Post by Norm Harding on 2011-04-09
K, have no idea of where to look for. Can I get a step-by-step how to?

---

### Post by Norm Harding on 2011-04-09
It is telling me "device is not ready (firmware missing)".

---

### Post by d3v1150m471c on 2011-04-10
what is telling you that? did you hold shift at boot and select an older kernel?

---

### Post by norm7446 on 2011-04-10
TriBlox6432 Norm Harding, have you not thought of reporting this as a Bug Report at Launchpad. If you don't have a launchpad account it's easy to set one up. Hope this Helps.

---

### Post by Madskillzz on 2011-04-10
Same thing happened to me on my Dell mini. After the update i rebooted and no more wireless. I had to re install the driver i went in the the driver directory with the install, make install, commands in the terminal so maybe  your driver needs same kind of installation. my card was [FONT=Arial][SIZE=1][COLOR=navy][COLOR=navy][FONT=Arial]RTL8188CE 
[/FONT][/COLOR][/COLOR][/SIZE][/FONT]

---

