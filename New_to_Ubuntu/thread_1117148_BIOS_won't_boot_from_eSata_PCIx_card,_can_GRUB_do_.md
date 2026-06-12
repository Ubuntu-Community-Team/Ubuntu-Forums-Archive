---
title: "BIOS won't boot from eSata PCIx card, can GRUB do this?"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by blackstripes on 2009-04-05
I have Ubuntu 8.10 installed on a 250GB SATA drive connected to my PC via a PCIe controller card.  My BIOS will not allow me to boot from this card; it only gives me the option for internal drives.  I have a 400GB internal SATA drive with Windows installed, can I make a small partition for GRUB and will that give me the option to boot from the eSATA drive that my BIOS doesn't see?  :???:

---

### Post by -kg- on 2009-04-05
You don't even need to make a partition for GRUB.  GRUB is located in the boot sector (called the Master Boot Record) of the hard drive that you boot to, and will refer to the appropriate bootable partition on any drive that the computer can see (once loaded from BIOS).

You'll need to install GRUB to the MBR, which of course will list any viable OS which you can boot to.  Refer to the following link, then follow the instructions in the 3rd message down:

[http://ubuntuforums.org/showthread.php?t=1114171]("http://ubuntuforums.org/showthread.php?t=1114171")

If you have any problems or further questions, post back.

---

