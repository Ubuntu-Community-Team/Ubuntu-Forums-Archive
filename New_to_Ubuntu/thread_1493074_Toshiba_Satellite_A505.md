---
title: "Toshiba Satellite A505"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by mikesmith00 on 2010-05-25
I bought a new laptop when my old laptop died, and was excited about this one, but the install hangs every time I try to do anything with it.  Has anyone had any luck installing Ubuntu 64 LTS edition on one of these?  I'm getting no output at all from the attempted install, it just boots from CD, then hangs.  If there's any help to be had, that would be greatly appreciated.  

Specs are at
[http://laptops.toshiba.com/laptops/satellite/A500/A505-S6030](http://laptops.toshiba.com/laptops/satellite/A500/A505-S6030)

I've already split my main partition, so everything is set up and ready to go, but linux doesn't seem willing.

Thanks for any help

---

### Post by warfacegod on 2010-05-25
Your disc might be bad. Are you sure you created an .iso disc and not a data disc?

I generally use an USB jumpdrive for installs. In my experience they are less likely to cause problems.

---

### Post by mikesmith00 on 2010-05-25
How did you set up your flash drive? I tried unetbootin (because the only partitions I can get to are in windows until I install), but then when I reboot, it pops up the unetbootin menu, I chose typical (I believe that was the wording) and then got nowhere from that.

---

### Post by Catharsis on 2010-05-25
How far into the bootup process do you get before the LiveCD blacks out?

At the purple screen with a keyboard and stickfigure at the bottom, press any key to get to the menu. Then check your disc for defects. 

If there aren't any, make sure "Try Ubuntu without making changes" is highlighted and hit F6. Select "nomodeset" and hit enter. If that doesn't work try "noacpi". If that doesn't work either, hit Esc in that F6 menu, delete "quiet splash" and replace it with "xforcevesa noapic noapci nosplash irqpoll".

---

### Post by mikesmith00 on 2010-05-25
Well, nomodeset got me to a GUI, and I was able to install, so that was a huge step forward, but after installing and rebooting, I got the error nouveau 0000:01:00.0:  Pointer to BIT loadval table invalid and then it hangs.  Nouveau is the NVIDIA driver isn't it?  Is there any way to disable it and just run a generic driver?  I just need an environment where I can code easily without all of the external crap that comes with windows, and I've grown pretty fond of Ubuntu.  FYI: I'm running the 64-bit version of ubuntu

---

### Post by Catharsis on 2010-05-26
Try just booting normally without changing the boot options at all.

You can also try booting the vesa driver by putting "xforcevesa" into the kernel parameters. You can also try booting into Recovery Mode. (The best suggestion here is to try anything and everything that could possibly work.)

Once you get to a workable desktop, go to System->Administration->Hardware Drivers to enable the proprietary nVidia drivers.

---

### Post by warfacegod on 2010-05-26
You may need to check the md5sum or whatever it's called for the .iso you have.

---

### Post by mikesmith00 on 2010-05-26
The install is done, the NVIDIA drivers are installed, the wireless is working, everything seems to be going well, although I still have a problem.  After rebooting, I still had the same problem, so I started trying all of the switches individually, and now everything works fine when I put the noapic switch in.  How would I go about fixing this?  Just keep leaving the switch or else is this a fixable situation?

---

### Post by Catharsis on 2010-05-26
You can permanently enable "noapic" by adding it to the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub

You can also try the mainline kernel and see if you like it better
[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)

It also might not be a bad idea to file a bug against the kernel so it has a chance of being fixed
```
ubuntu-bug linux
```

---

### Post by mikesmith00 on 2010-05-26
Bug report is submitted, thank you Catharsis, I'm trying the mainline Kernel as soon as summer vacation starts, school's kind of in the way now.  Again, thank you for all of your help.

---

