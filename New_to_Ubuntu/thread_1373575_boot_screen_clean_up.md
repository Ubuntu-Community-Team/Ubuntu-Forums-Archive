---
title: "boot screen clean up"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by purvis on 2010-01-05
How can I clean up the many Ubuntu versions and their associated recovery options from by boot screen?

---

### Post by drs305 on 2010-01-05
Welcome to the Ubuntu forums purvis. 

This post assumes you have Karmic, 9.10 and Grub 2. (You can put what OS you have next to your icon via the user Control Panel).

Some things have entries in */etc/default/grub* that you can modify to hide (Recovery mode). Some you can disable by turning off the executable bit in the script that generated the entry (MEMTEST86+ >> */etc/grub.d/20_memtest86+*).

And then the geeks can go to town by modifying the configuration scripts in the /etc/grub.d folders. Some examples, such as hiding the Windows Recovery partition, are detailed here. Just be careful, it's geekdom at its worst.  ;-)

[Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")

Unfortunately, there isn't a simple GUI for doing this with Grub 2 - yet.

---

### Post by JimmyBEng on 2010-01-05
Another option is to remove any old versions of the linux kernel that you have installed and no longer need.  In most cases this will automatically clean up the list in GRUB.

First go to the system monitor (System->Administration->System Monitor). Select the System tab.  Look for a line like "Kernel Linux 2.6.31-16-generic" and make note of the version numbers listed.

Start Synaptic (System->Administration->Synaptic Package Manager).

Search for linux-image. you will find several entries like this (linux-image-2.6.31-14-generic).  One of these will have version numbers that match your current version that was in system monitor.  Mark the other (older) versions for removal, but do NOT remove your current version.  Accept the changes.  The next time you reboot you should see fewer entries in the GRUB menu.

---

