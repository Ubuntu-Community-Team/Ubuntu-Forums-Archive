---
title: "Multiple menu.lst and Grub"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by depuyc on 2009-03-23
I installed Ubuntu and Kubuntu awhile back to figure out which one I like.  Now I'm ready to get rid of Kubuntu but noticed that Grub is using the Menu.lst on my Kubuntu partition for booting.  I'm assuming that Grub is also running off of this partition.  Here's a basic list of the partitions;

SDA1  Windows
SDA2  Windows
SDA3  Ubuntu
SDA4  Linux Swap

SDB1  Windows Backup
SDB2  Kubuntu

How can I change Grub to point to the SDA3 partition so I can wipe the Kubuntu partition?

---

### Post by MaindotC on 2009-03-23
There's a file called device.map in the /boot directory.  It tells you which /dev/s* maps to (hd*,*).  I'm betting you'd need to tell grub to boot sda3 by calling it (hd0,2).

---

### Post by depuyc on 2009-03-23
I guess I'm not understanding or I didn't explain well.  Ubuntu is at 0,2 and the Menu file is setup correctly to reflect that.  What I'm having an issue with is I have a menu.lst file on the Ubuntu partition and another on the Kubuntu partition.  I have noticed that my boot menu is using the menu file on the Kubuntu partition that I want to get rid of so I need to point grub to use the menu.lst on the Ubuntu partition.  I am also concerned that grub itself is running off of the Kubuntu partition so do I have to change anything else before I wipe that partition?

---

### Post by MaindotC on 2009-03-23
Is Kubuntu the primary partition?

---

### Post by egalvan on 2009-03-23
> **depuyc said:**
> I installed Ubuntu and Kubuntu awhile back to figure out which one I like. 
**Grub is using the Menu.lst on my Kubuntu partition for booting.  I'm assuming that Grub is also running off of this partition.**  Here's a basic list of the partitions;

SDA1  Windows
SDA2  Windows
SDA3  Ubuntu
SDA4  Linux Swap

SDB1  Windows Backup
SDB2  Kubuntu

How can I change Grub to point to the SDA3 partition so I can wipe the Kubuntu partition?

to test this assumption, check the boot order in the BIOS.
GRUB stage 1 (IPL part of the MBR) is on the drive that BIOS boots.

If your machine is booting the second drive,
then try changing this to the first drive, 
dis-connect the second drive, and see if it boots windows and Ubuntu.
If this works, GRUB is set up correctly for what you want to do.

If not, then some more work lies ahead.

If the initial parts of GRUB are on the sdb sdb2, or point to it from the first drive sda, then you need to re-install GRUB (the IPL is hard-coded during install)

Follow this how-to:, it's very well written...

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by depuyc on 2009-03-23
I found another thread that gave me enough info to take care of this.  I ran grub from the command line and changed root to hd0,2 (my Ubuntu partition) and setup to hd0.  Rebooted and everything came up exactly as I expected.  Wiped out the partition for Kubuntu and rebooted again.  I need to still do some cleanup on the menu.lst file since it's an old one but happy to be settled again.

Thank you for the assistance.

---

### Post by MaindotC on 2009-03-23
I should have just advised you to use the root (hd0,2) command.  Sorry about that and glad you got it fixed.

---

