---
title: "How do I reconfigure my system when motherboard is changed?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by bwallum on 2010-03-01
Hi

I've just changed my motherboard. I kept my Ubuntu 9.10 installation on an existing hard drive as I made the swop. Now I'm finding that chipset related functions (lan, vga, etc) are not working. I don't want to risk a fresh install of Ubuntu but I think I need to reconfigure to get the appropriate chip set drivers installed.

Any ideas on how I would do that?

---

### Post by thatguruguy on 2010-03-01
If ever you would do a fresh install, I think now would be the time.

---

### Post by crlang13 on 2010-03-01
This may or may not help, but I just had to do a bios update by flashing the motherboard.  Updating the bios is pretty easy in windows, but if you don't have windows, you have to go through Dos.

I made a bootable USB with freedos on it and put the bios flash on there, booted into dos and ran the file.

Although these two links aren't specific to your problem, they may give you an idea:
[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

[http://jamsubuntu.blogspot.com/2008/12/upgrading-msi-wind-to-10a-bios.html](http://jamsubuntu.blogspot.com/2008/12/upgrading-msi-wind-to-10a-bios.html)

---

### Post by bwallum on 2010-03-03
I just flashed the BIOS on my Biostar MB. It had a utility in the CMOS that upgraded the BIOS. All I had to do was download the BIOS file from Biostar, put it on a floppy, run the BIOS Upgrade utility in CMOS and with 3 taps of the keyboard the BIOS was upgraded. Biggest problem was finding a floppy disk that still worked.

I now have the on-board graphics working fine. Only downside is the on-board LAN adapter still refuses to work.

This is now a network specific problem so I'll start a new thread in the network forum.

Thanks a lot for all the help,
Regards, Bob.

---

### Post by bwallum on 2010-03-04
> **thatguruguy said:**
> If ever you would do a fresh install, I think now would be the time.

Apparently the 'driver' required for my ethernet hardware is forcedeth and that is loaded during installation. Could I just re-install the kernel?

---

