---
title: "VBox lockup"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by flyfishingphil on 2011-03-18
Have VBox installed but when I try to go in I get this error message:
[I]
Kernel driver not installed [noparse](rc=-1908)[/noparse]

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.[/I]

I also received notice the notice on the upgrade to version:

4.0.4-70112-Ubuntu-Karmic

Downloaded and tried to install but I get this error message:

[COLOR="Red"]*Error: Conflicts with the installed package 'virtualbox-3.2'*[/COLOR] (Currently using Ver. 3.2.12 r 68302 in updated Lucid Lynx.)

I really need to get in so I can do further work on updating my web site. Suggestions? (Step-by-step works best. Like go to Sudo and enter >>>>>)

Just went back in and did some checking. Installed the VBox from the software center but noticed this is a "Karmic" version. Do I need to uninstall this and re-install the "Lucid Lynx" version for the updates to work properly?

Thanks for any assist.

Phil

---

### Post by flyfishingphil on 2011-03-18
Got a notice on the problem while trying to open the XP that gave directions to uninstall and reinstall the drivers using sudo. Did that and it is usable again.

Just wondering if I should remove the Karmic version, that's the one in Ubuntu Software, and download and install the newer version from Oracle that is set for the Lucid i386.

Anybody else go thru this?

---

