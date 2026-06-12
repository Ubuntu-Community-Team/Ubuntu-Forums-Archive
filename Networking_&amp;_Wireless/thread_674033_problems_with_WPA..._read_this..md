---
title: "problems with WPA... read this."
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2008-01-21
I have been having issues with WPA since I installed gusty and just fixed them using Debian packages.  The problem was that I could connect to a WPA network once, but upon reboot, wireless would never connect.  It seemed to hang at trying to find a valid key.  I read a ton on the issue and installed various bugfixes and packages to no avail.

I finally fixed the issue by installing Debian packages for wpasupplicant, and networkmanager.

I'm running an ipw2200, so fIrst I installed the latest ipw2200 drivers and firmware from sourceforge. I believe this is already included with Gusty so you may not need to do this.

Download the following files from Debian distrib packages: libiw28_28-1_i386.deb wpasupplicant_0.5.5-2_i386.deb network-manager_0.6.4-6_i386.deb network-manager-gnome_0.6.4-6_i386.deb

Install the packages in the above order with " sudo dpkg -i [package name] "

update your icon cache " sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/ "

reboot and setup your wireless connection.
lock the above packages in synaptic.

I hope this helps someone with WPA problems.
-J

---

