---
title: "Jaunty black login"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by nilsolaris on 2009-09-17
Ive have been trying to re-install ubuntu for about 3 days now, this is the first time ive ever had serious problem involving the installations. Started off with burning an ISO of Jaunty but was never able to successfully install it. Gave up and decided it was better off to install the liveCD of hardy and upgrade from there. The update to intrepid went fine, then the upgrade to Jaunty has my computer loading up until where the login screen should appear but all i see is pixelized ubuntu logos as well as a line simuler to HG/HFD/HFJHDJKF.....(sorry didnt write it down).

I have gone through everything in the recovery mode setting and everything seems to be fine in there. Im wondering if it may be possible this problem is from me not installing the restricted drivers for my ATI Radion HD2400 Pro? If so is there a way i can install these drivers through command prompt?

---

### Post by relay_man on 2009-09-17
If you can get to the command prompt, you can try:

sudo apt-get update

I did this at the command line a minute ago and got a line about restricted repos being checked, but I know they are enabled.  I'm not sure what you will get.  My guess is they are not enabled by default if your install is new.
If that is the case, I believe this will get them done from the command line:

sudo apt-get install ubuntu-restricted-extras

I believe you may have to run the update command again to get things squared up.

---

### Post by mapes12 on 2009-09-18
Upgrading from one version to another can be problematic at times. On the basis that you have no critical data on the machine then I would start again with a fresh install but this time totally clean the HDD with something like this: [http://www.dban.org/](http://www.dban.org/)

Then use an Alternate text based CD to run the install: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Your graphics driver should still run even in low res with a basic install. Once installed you can then enable any restricted drivers System>Administration>Hardware Drivres and activate the recommended driver. You may not need any graphics drivers though.

---

