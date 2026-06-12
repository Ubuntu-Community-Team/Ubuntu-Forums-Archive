---
title: "GRUB menu issues with new install"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by rexh on 2009-11-01
I did a fresh install of Ubuntu 9.10 to an old laptop with a Pentium M 1.4ghz processor 2gigs RAM and an ATA-6 160 gig hard drive. I have only one partition on the drive and I am not going to use a dual boot configuration.  When I boot from the hard drive I get an error message that "no such device found."  I figured out how to get to grub menu and edit the menu.  I delete the line in the menu that has to do with searching for a floppy and setting the UUID for the hard drive.  When I hit Control-X from there, the systems boots.  How do I save the changes from that menu and do I need to save them from inside the GUI or do I need to do it from the command line?

---

### Post by cariboo on 2009-11-01
HAve a look at this [wiki]("https://wiki.ubuntu.com/Grub2") page, it should tell you all you need to setup grub2.

---

### Post by sandyd on 2009-11-01
> **rexh said:**
> I did a fresh install of Ubuntu 9.10 to an old laptop with a Pentium M 1.4ghz processor 2gigs RAM and an ATA-6 160 gig hard drive. I have only one partition on the drive and I am not going to use a dual boot configuration.  When I boot from the hard drive I get an error message that "no such device found."  I figured out how to get to grub menu and edit the menu.  I delete the line in the menu that has to do with searching for a floppy and setting the UUID for the hard drive.  When I hit Control-X from there, the systems boots.  How do I save the changes from that menu and do I need to save them from inside the GUI or do I need to do it from the command line?
try typing in
```

sudo update-grub

```

---

### Post by drs305 on 2009-11-01
> **rexh said:**
> When I boot from the hard drive I get an error message that "no such device found."  I figured out how to get to grub menu and edit the menu.  I delete the line in the menu that has to do with searching for a floppy and setting the UUID for the hard drive.  When I hit Control-X from there, the systems boots.  How do I save the changes from that menu and do I need to save them from inside the GUI or do I need to do it from the command line?

If this is the line that displays "root" and you have to change it to "uuid" or delete the line (GRUB error 11) the ubuntu documentation has an example with graphics.

I've written the Ubuntu doc [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2") which is an expansion of and improvement to the wiki mentioned in the previous post, and the original [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") thread.

You will need to make the changes after you boot to your system.

---

