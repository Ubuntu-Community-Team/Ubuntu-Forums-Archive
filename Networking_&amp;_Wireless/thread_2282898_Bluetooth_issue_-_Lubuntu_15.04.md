---
title: "Bluetooth issue - Lubuntu 15.04"
date: 2015-06-17
forum: Networking &amp; Wireless
---

### Post by wagnernico on 2015-06-17
Hi everyone,
I'm pretty new on Lubuntu

I bought a wireless speaker for my laptop. I tried a few things and I installed a lot of packages to make it work (bluez elements), but without success.

And now, I noticed that bluetooth manager has been uninstalled, and I can't install it back (even after having uninstalled other bluetooth packages). The problem is that I normally use it to browse into my mobile.

When I try to reinstall it from Lubuntu Software Center I've got that message:

The following packages have unmet dependencies:


blueman: Depends: libbluetooth3 (>= 4.91) but 4.101-0ubuntu25 is to be installed
         Depends: libc6 (>= 2.4) but 2.21-0ubuntu4 is to be installed
         Depends: libglib2.0-0 (>= 2.31.8) but 2.44.0-1ubuntu3 is to be installed
         Depends: libgtk-3-0 (>= 3.0.0) but 3.14.13-0ubuntu1 is to be installed
         Depends: libpython2.7 (>= 2.7) but 2.7.9-2ubuntu3 is to be installed
         Depends: python (>= 2.7) but 2.7.9-1 is to be installed
         Depends: bluez (>= 4.61) but 4.101-0ubuntu25 is to be installed

I tried to remove some of the dependencies, but without success either.

Thanks for your help.

---

### Post by ajgreeny on 2015-06-17
What version of Lubuntu?

Have you refreshed the repos with **sudo apt-get update**?

Have you enabled any PPA repos which might affect package versions?

---

### Post by wagnernico on 2015-06-18
Hi,
I've just discovered the power of the update command line!

So Bluetooth Manager is back. Now the issue is that I paired my mobile with the computer but I can't browse the device "The specific location is not supported" (which is weird because it worked a few days ago).When I run the setup and when I try to connect to Network I've got an error message "device added succesfully but can't connect". 

I've got a similar problem with the speaker, it's paired but it can"t connect to the input service.

Thanks for your help

---

### Post by ajgreeny on 2015-06-18
Glad the first problem is sorted, but can't help with bluetooth; I don't use it at all on my desktop machine.

---

