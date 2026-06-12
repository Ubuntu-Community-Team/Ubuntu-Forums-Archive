---
title: "newbie dual boot grub menu failure"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by gribbsy on 2010-05-24
Hello.  I'm running a dual-boot with linux mint and Windows.  Being a close relative of Ubuntu, I thought it couldn't hurt to post here.  I have an E-machines desktop with :
760 GB Hard Drive
6GB RAM
NVidia GeForce Graphics card 6150se Integrated
AMD Athalon II X2 235e dual-core processor

My problem is getting my grub to boot into Linux Mint, and the problem may lie with my graphics card.  Whenever I install the linux mint for the first time, I am prompted to activate my proprietary NVidia graphics driver, which I do.  Then I am asked to reboot.  Upon reboot, the system gets to the grub menu, accepts my selection to boot linux mint, then the "progress dots" appear on the screen.  After about 8 seconds, the screen switches into command prompt mode.  I never get to the graphical sign-on screen.  All I get is the console sign-on prompts.  From there my only option seems to be to reboot. (sudu reboot).  After which, of course, I am forced to go into Windows vs. Linux to avoid the problem.  Once Windows has loaded up, I do a restart and go back into Linux Mint .  Finally, I get to the Linux sign-on graphical  screen.

To summarize, i cannot restart linux mint without getting stuck staring at a console screen.  I can get back into linux mint if i use the command 'sudo reboot', and, from the grub menu, choosing to go into Windows.  From Windows, I then do a restart and end up back at the grub screen again, but this time when I select linux mint, things work and I am given the sign-on gui.

If I choose to not install the graphics driver (and put up with the annoying reminder to activate one), the system dual boots without a problem.

---

### Post by cariboo on 2010-05-24
If you log in, and type:

```
startx
```

Does it boot to the desktop?

---

### Post by nhasian on 2010-05-24
use of the proprietary nvidia driver is not mandatory.  you can disable it from reminding you to install it by disabling "Check for new hardware drivers" in System-> Preferences-> Startup Applications.  If you choose to use the open source Nouveau driver built in the linux kernel instead of the proprietary nvidia one, you should consider upgrading to the latest stable linux kernel 2.6.34 instead of 2.6.32 that comes with Ubuntu Lucid Lynx 10.04 

Deb packages are already built for you here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

---

