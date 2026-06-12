---
title: "Network card not found - 7.04 server"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by RyanNutt on 2007-08-19
I installed 7.04 server on a computer that had previously been running Mandrake 10.  A crash necessitated reinstalling the operating system so I decided that was a good excuse to go to Ubuntu instead which I've found to be easier to work with than Mandrake.  

During the install I got a message that a network card could not be found.  At then end of the install I went back to the network page and didn't get an error that time so I assumed that it worked.

When I log in I cannot access the network.  ifconfig doesn't show an eth0, only lo.  lspci shows "00:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)".  

Any suggestions where to start?  Aside from a new hard drive this computer had been running Mandrake for a while without any problems so I figure the network card has to be workable with Linux.

---

### Post by RyanNutt on 2007-08-19
Ok, so I've found that the 8139too module is what I'm supposed to be using.  At least that's what I've seen on other boards.  In dmesg I see the line "8139too: proble of 0000:00:09.0 failed with error -16".  It's repeated several times, I would assume once for each reboot, with "8139too Fast Ethernet driver 0.9.2" a few lines above.

And I also found "PCI: Unable to reserve I/O region #1:100@de00 for device 0000:00:09.0" which seems like it would be a problem :)

---

### Post by RyanNutt on 2007-08-19
A'ight, I sort of feel like I'm talking to myself, but I found a solution.  I added acpi=off to /boot/grub/menu.lst which made eth0 show up and dhclient eth0 to /etc/rc.local which brings up a network connection.

So unless there is a better way it seems to have worked.

---

