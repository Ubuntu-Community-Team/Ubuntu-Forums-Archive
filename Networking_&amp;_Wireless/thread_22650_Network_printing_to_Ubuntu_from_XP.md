---
title: "Network printing to Ubuntu from XP"
date: 2005-03-28
forum: Networking &amp; Wireless
---

### Post by z993126 on 2005-03-28
The printer I have is an HP PSC 1210.  I got it working properly in Ubuntu, but need to be able to print to it from a WinXP machine on the network.  Windows' install new printer sees the PSC 1210, but says the server doesn't have the proper drivers and I need to select them myself.  Not in the inbuilt list, and the software driver package from HP doesn't have the needed drivers (as far as the printer installer cares).  I do still have the drivers installed from the previous incarnation of the machine presently running Ubuntu...I wonder if it's possible to tell it to use those, and if possible, how?

---

### Post by localzuk on 2005-03-29
This isn't so much a ubuntu problem as a windows xp not finding drivers problem. But here is some help anyway:

The driver disks that come with any HP printer contain the required drivers for the printer in Windows XP. You need to look on the disk for a .inf folder  (probably in a folder named winxp or something similar). This is the driver file. In XP, use the printer installer to navigate to the correct directory and select the file. That should do it. If it doesn't try going to the HP website and downloading new drivers.

---

### Post by z993126 on 2005-03-29
Unfortunately, Windows is 'unable to find drivers for the specified device' in any of the .inf files on the original CD...HP's site suggests the PSC 1210 not be used over a network, but I was using it fine between networked XP machines.  If I need to switch back to XP on the machine my printer's attached to whenever I need to print (which only happens once a month), so be it, but I'd rather not.

---

### Post by Crazy Man on 2006-01-18
So after all the samba configuration and cupsd configuration, NOTHING?

:(

---

