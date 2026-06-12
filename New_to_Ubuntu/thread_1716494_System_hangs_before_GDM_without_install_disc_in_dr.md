---
title: "System hangs before GDM without install disc in drive"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2011-03-28
Just finished a reinstall of Ubuntu Lucid 10.04 from the alternate installer disc.  I restarted after the installation and the machine hangs.  I put the disc back in, after the first few seconds to allow the system to boot from the hard disk and it sees the optical disc and completes the boot process.  I have no idea what to make of things.

The system is an older P4 system with 1GB of RAM, an older nvidia GeForce4 MX 440 white box that previously ran Windows without issue, but I need to move that license to another box, so am trying Ubuntu on this hardware.  I was able to successfully run without issue around Feisty and Gutsy releases so I'm perplexed at these issues now.  Anyone have any ideas what I'm looking at?

--bornagainpenguin

---

### Post by bornagainpenguin on 2011-03-28
When I get to GDM and click to login, I get a message about power-manager still running.  The dialogue offers me a button to "log out anyway", which when pressed allows me to get to my desktop.

If there are some commands I need to run and copy the output of to here I will, just tell me what to do!

--bornagainpenguin

---

### Post by rosencrantz on 2011-03-29
Could this be caused by your BIOS settings and do you have any other drives connected (external, internal, flash, ipod)? In that case, check your BIOS boot priorities (usually, F2 or Esc during boot) and unplug anything that's removable before booting. If this doesn't help, try a grub update (sudo update-grub).
Best of luck
rosencrantz

---

