---
title: "no proprietary drivers installed?"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by Bodhibear420 on 2009-11-14
Hey All,

I've been looking around this site for a couple of days, and I can't seem to find the answer.  I'm trying to find and download the right driver for an intel integrated video 82915G/GV/910GL .  When I run SYSINFO it is listed under motherboard>host bridge, but when I click on graphics card it just states VGA compatible controller.  Is there a way to find and download a more specific or compatible driver for my video.  I've tried looking into xorg.conf but it's empty.  And alot of threads point to 915resolution that is not on 9.10  So I would greatly appreciate any help.  Thanks

---

### Post by jocko on 2009-11-14
> **Bodhibear420 said:**
> Hey All,

I've been looking around this site for a couple of days, and I can't seem to find the answer.  I'm trying to find and download the right driver for an intel integrated video 82915G/GV/910GL .  When I run SYSINFO it is listed under motherboard>host bridge, but when I click on graphics card it just states VGA compatible controller.  Is there a way to find and download a more specific or compatible driver for my video.  I've tried looking into xorg.conf but it's empty.  And alot of threads point to 915resolution that is not on 9.10  So I would greatly appreciate any help.  Thanks

There are no proprietary (= closed source) drivers for intel cards . Only ATI and nvidia make closed source drivers for their cards. The open source intel drivers are installed by default, and should be activated automatically on supported hardware.
And there is no xorg.conf anymore because it is not needed. The hardware is detected automatically, and the appropriate driver is loaded with some default options. But if you want to tweak some settings you can generate your own xorg.conf to override the default settings.

---

### Post by Bodhibear420 on 2009-11-14
Great!  Thank you.  Could anyone tell me how to create an xorg.conf to tweak the resolution so I can set it at 1280x768 .

---

