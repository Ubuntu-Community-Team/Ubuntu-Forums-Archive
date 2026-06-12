---
title: "ath5k wireless issues"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by KinderX on 2008-11-29
i just upgraded to intrepid from hardy with the promise that my endless wireless issues with my Atheros ar5007eg card would end. bs.

i have been pointed to [this guide[](http://wireless.kernel.org/en/users/Download#Buildingandinstalling) and its not working, after i install i try to unload the original drivers using the "sudo make unload" command in the correct directory, and it gives me this:

```
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1

```

i am unable to do anything with this. i have tried searching everywhere for the answer. any answers.

---

### Post by JohnSGruber on 2009-01-22
I'm sorry to hear you are having trouble.

I also have a wireless card that isn't supported out-of-the-box by Hardy or Intrepid.

If you can remove the software you installed manually you might try to install linux-backports-modules-intrepid-generic (assuming this is a desktop or laptop rather than a server). This package includes ath5k and may be the reason someone suggested you install Intrepid.

In order to get this to work you need to go to System-> Administration->Hardware Drivers and disable the Atheros driver there (ath-pci) and reboot.

 I found it desirable with the current package to enter the command suggested by the ath5k developers:
```
sudo iwconfig wlan0 rate 11M
```

This is suggested at [http://wireless.kernel.org/en/users/Drivers/ath5k]("http://wireless.kernel.org/en/users/Drivers/ath5k") on the same site you were quoting. If I don't do this I get about 11% packet loss.

Alternatively you can try the madwifi - 0.3862-1 package from last August available at [http://ppa.launchpad.net/timg-tpi/ubuntu]("http://ppa.launchpad.net/timg-tpi/ubuntu"). This installs a newer version of the legacy drivers enabled in System->Administration->Hardware Drivers.
Installing this package will install a package called dkms and may install a couple other prerequisites.

Once I have both installed I find I can go back and forth betwee the two
drivers by, for example, 
```
sudo modprobe -r ath_pci
sudo modprobe ath5k
``` and they both work.

I find I don't have to deal with the 802.11 or other modules, they come and go automatically--modprobe must take care of it has part of its dependency handling.

==

If you simply wish to go from where you are now I'd suggest disabling the current proprietary driver and rebooting, as above. That should remove the old ath_pci and their cohorts so you can try what you downloaded. I don't know if you will have to do something special to get the 802.11 drivers when dealing with the software you downloaded directly.

I find the following command useful to see where I am:
```
lsmod | grep ath
```
which will tell you what Atheros related drivers you have loaded and what modules each module dependes upon.

The web site [http://madwifi-project.org]("http://madwifi-project.org") may be useful to you.

I hope you get something to work. I think the intrepid backports would be the simplest.

Good luck.

---

