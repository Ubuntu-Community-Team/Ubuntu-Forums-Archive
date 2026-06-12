---
title: "Activating WLAN on an IBM X24 Notebook"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by Orim Kurowe on 2007-05-05
Hi there.

I recently installed Xubuntu 7.04 on my notebook which has a Prism 2.5 chipset. Xubuntu did install a matching driver but obviously could not activate the WLAN chip.

So lshw tells me that wlan0 is DISABLED. I read in the Ubuntu docs that the solution to this problem varies from chipset to chipset. However, even after several hours of googeling I still have no clue how to activate my WLAN chip. 

Does anybody know how to do that?
Any help is appreciated, thank you.

---

### Post by Candace on 2007-05-05
Hi,
No offense, but I have found that searching the Ubuntu Forums is usually more profitable than google when the problem is so specific (plus you learn a lot that you weren't looking for :wink: ).

...If you want to know, this is what worked for me on a fresh install of Ubuntu 7.04 with an HP dv2000 and wireless card Broadcom 1390 WLAN PCI.

1. [http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505](http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505)
2. [http://ubuntuforums.org/showthread.php?p=2589722#post2589722](http://ubuntuforums.org/showthread.php?p=2589722#post2589722)

I don't know how different Xubuntu is from Ubuntu, sorry, I'm a newb. and can't help much more than this.

---

### Post by Orim Kurowe on 2007-05-05
> **Candace said:**
> Hi,
No offense, but I have found that searching the Ubuntu Forums is usually more profitable than google when the problem is so specific (plus you learn a lot that you weren't looking for :wink: ).


Well, I should have been more specific. Of course I did search these forums and countless others. I've read many different manuals on how to install drivers, set up a connection, etc. But this is not my problem.

The problem is that my WLAN chipset has been deactivated and when I understand the official Ubuntu documentation correctly the procedure to re-activate it can be very different for different chipsets. So I fear that only someone with the same notebook or WLAN chipset can help me :(

---

### Post by Floppyjoe on 2007-05-05
> **Orim Kurowe said:**
> Hi there.

I recently installed Xubuntu 7.04 on my notebook which has a Prism 2.5 chipset. Xubuntu did install a matching driver but obviously could not activate the WLAN chip.

So lshw tells me that wlan0 is DISABLED. I read in the Ubuntu docs that the solution to this problem varies from chipset to chipset. However, even after several hours of googeling I still have no clue how to activate my WLAN chip. 

Does anybody know how to do that?
Any help is appreciated, thank you.

Make sure you have these packages installed:
```
linux-wlan-ng
```
and
```
linux-wlan-ng-firmware
```

Good Luck.

---

