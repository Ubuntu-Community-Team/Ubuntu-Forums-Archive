---
title: "Constant crashing, Realtek boot manager won't uninstall"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by El.grincho on 2011-01-02
(Not sure if this is the best forum for my question, but I'll start here since I'm new to ubuntu.)

A week ago I installed ubuntu 10.10 over xp home on a lenovo.  I made the switch because the machine had been badly infected/hijacked s.t. I was unable to update service packs, run cleanup apps, etc.  The install cd was burned from an uninfected computer.

I was unable to boot from the disk, so I ran some utility on the ubuntu  install disk to facilitate an auto boot.  It didn't work, so on the next reboot I followed the prompts to specify a cd boot.

I installed ubuntu over the entire disk, wiping it clean.  The first sign that something was fishy was a crash during updates, that is to say, the screen froze like a screenshot and the keyboard and mouse were wholly unresponsive (incl ctrl,alt,del ctrl,alt,backspace, and ctrl,alt,end).  After waiting an hour with no change, I did a hard reboot.

The freeze keeps happening (about 5 to 10 times with a hard reboot each time) so I decide to reinstall.  More crashes, another reinstall.

After 3 or 4 installs without improvement in the crashes ( and finding nothing obvious in the syslog or messages) I am wondering if there's some holdover from the malware I had on xp?  I find that 'realtek boot manager' is keeping me from booting directly into the cd or flash drive ubuntu boot disks I had made.  I disabled the 'realtek boot manager' from booting off the network and reset the bios to boot from cd then disk.  I also reset the bios by unplugging from the wall then disconnecting the CMOS battery for 15 min then reinstalling ubuntu.

Not only am I still getting crashes, but the 'realtek boot manager is still there and my ubuntu password is from 2 or 3 installation attempts ago.  I've gotten some error messages saying that there a GLib messages that there's some missing password or username.

How can I wipe my computer back to a totally blank slate (including uninstalling 'realtek boot manager' that was installed under xp and erasing a prior ubuntu password)?  Any ideas why my install is so crazy unstable?

---

### Post by cariboo on 2011-01-02
What is this realtek boot manager? Most linux distributions use either grub or grub2 as a boot manager. Your lockup problem may be due to an improperly installed graphics driver.

If you want do clear the hard drive boot from the Live CD and once at the desktop go to System->Administration->Gparted. Gparted is a partitioning tool which allows you create/add/remove partitions.

---

