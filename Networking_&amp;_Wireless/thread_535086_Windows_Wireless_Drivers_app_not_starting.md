---
title: "Windows Wireless Drivers app not starting"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by icntdrv on 2007-08-26
Hello all.
I'm new to Linux, having only a basic working knowledge.  Just enough to get into trouble.

I installed Xubuntu 7.04 AMD64 and everything was going great.  I installed the Windows Wireless Drivers package and pointed it at the INF file for my wireless adapter.  It said that the driver was installed but that the device was not present.  After a restart it was still not present so I attempted to remove the driver and start over but the driver would not remove.  I figured it was just a buggy install of WWD so I uninstalled the package and reinstalled.  Now when I try to start Windows Wireless Drivers the window briefly flashes onto the screen and disappears. 

Any ideas whats up?

---

### Post by icntdrv on 2007-08-26
Nevermind.  I managed to blindly struggle my way through the command line, and found that there were two, apparently conflicting, drivers loaded at the same time.  I deleted both and the GUI went back to working fine.  The adapter still isn't recognised though.  Are there any issues with Broadcom internal adapters?  I'm not sure what series it is.

---

