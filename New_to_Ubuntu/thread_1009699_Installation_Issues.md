---
title: "Installation Issues"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by spooly on 2008-12-12
I have an old desktop built with random parts I had lying around and I'm trying to install Ubuntu 8.10 on it.  Using the graphical install, it never makes it to the installation.  After the loading screen pops up, it drops to busy box.  If I select 'try ubuntu' instead of installing it, the same thing happens.  I've tried installing in safe graphics mode and in OEM install mode with the same results.  Can anyone help?

Thanks in advance
spooly

---

### Post by tuxxy on 2008-12-12
Have you tried the alternate CD avilable from the main download page, check the option near bottom of page, the alternate CD provides a text based installer

---

### Post by spooly on 2008-12-12
Not yet, downloading now.
Thanks

---

### Post by spooly on 2008-12-13
The same thing happens.  I suspect it may be a hardware issue, but I'm not sure.  Whenever it boots from the CD, i get a blinking cursor for about 5 minutes (maybe more) before it finally starts booting.  Does anyone have any ideas?

Thanks
spooly

---

### Post by halw on 2008-12-13
> **spooly said:**
> The same thing happens.  I suspect it may be a hardware issue, but I'm not sure.  Whenever it boots from the CD, i get a blinking cursor for about 5 minutes (maybe more) before it finally starts booting.  Does anyone have any ideas?

Thanks
spooly

This is certainly hardware related. How fast the cd device reads, amount of memory, processor speed, etc.

---

### Post by CatKiller on 2008-12-13
> **spooly said:**
> I have an old desktop built with random parts I had lying around and I'm trying to install Ubuntu 8.10 on it.

So what are the specifications of those parts? Ubuntu 8.10 is a modern operating system, and so has modern requirements. I believe the minimum amount of RAM to run the live cd is 384 MiB, for example. If your old computer isn't up to the task of running Ubuntu, there are lighter-weight alternatives available.

Of course, it could just be a configuration problem. I seem to recall that some older computers had problems with ACPI and APIC. There are kernel options that you can use to change these behaviours. I can't remember quite how one enters these options in the first Ubuntu installer menu, but if you post back that this is the case, then I'm sure someone will tell you how to do so.

---

### Post by spooly on 2008-12-13
The specs should be fine: 1.8 GHz Pentium 4, 512 MB ram, Nvidia MX440 (not sure if that's the correct model number off the top of my head) w/ 64mb onboard memory.  The drive it's running from is a sony 16x dvd drive.  The HD is either 40 or 80gb, and was given to me by a friend - he claims it's filled with viruses.  I intend to format it if I can get the ubuntu installer working.  The MOBO is a soyo SY-P4VSA.  The cpu, MOBO, ram, and video card are all out of the same machine and worked fine together until the hard drive went out.

During startup, the full ram and video memory are detected.  I do get an error because no floppy drive is detected (who needs one?), but it allows me to continue bootup.

I'm not sure how to find out if it's an ACPI or APIC issue.  What should I look for?

Thanks
spooly

---

### Post by CatKiller on 2008-12-14
> **spooly said:**
> I'm not sure how to find out if it's an ACPI or APIC issue.  What should I look for?

I'm not entirely sure.

You could try putting kernel options in to see which ones work. As I say, I can't remember how to enter them on the first menu of the installer. It might have been one of the options at the bottom, or it might have been pressing Esc. It was a _long_ time ago that I last fiddled with the installer.

Actually, [this page]("https://help.ubuntu.com/community/BootOptions") on the Ubuntu wiki seems to cover it.

---

