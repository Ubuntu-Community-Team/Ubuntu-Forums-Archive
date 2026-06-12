---
title: "RT2500 Wireless knocked out by recent Kernel update."
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by shivans on 2008-06-04
Hey all, hoping someone can help me out.

Last night I allowed Adept to update the kernel to .18 from .17. The problem is it's knocked out my Wifi.

I originally had problems when I updated to Hardy, but that was resolved by following this thread:- [http://ubuntuforums.org/showthread.php?t=766724](http://ubuntuforums.org/showthread.php?t=766724)

I tried the above again, however when I use the command Iwconfig, all I get is:-

lo no wireless connection
eth0 no wireless connection
eth1 no wireless connection
(hope that is correct, I'm not on home PC atm).

Its as if it can't detect my wlan0 or ra0.

Its not the end of the world since I can switch back to the .17 kernel and not have any issues, but it would be good to get up and running on .18

Any/all suggestions welcome :)

---

### Post by chili555 on 2008-06-04
When you say you followed the procedure in the link, may I assume it was the procedure in post #11? If so, when you did this, it built a driver module for the kernel you were running at the moment. Whenever you install a new kernel, -18 in this case, you must build a module for the new kernel. Simply boot into the new kernel, and do:```
cd rt2500-cvs-2008042510/Module/
make clean
make
sudo make install
```A module will be created and you may continue to configure your interface. Substitute your version of rt2500 if it's not 2008042510.

When -18 is superceded, repeat the process. If you are as obsessive as I am, you might download a newer version of rt2500 before you restart after the Update Manager suggests you do so. That way, you will always have the latest!

---

### Post by shivans on 2008-06-05
Many thanks.

All up and running again. It seems I missed the 'Make clean' line.

---

