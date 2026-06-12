---
title: "New Instal Guide: XP, Ubunutu, Windows 7 Beta"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by axiomata on 2009-01-28
A few years back, with help from this forum I set up a dual boot with XP and Ubuntu.  That computer has been scrapped and I'm interested now in setting up a tri-boot of XP (already installed), Ubuntu and the new Windows 7 beta.

I only have one 640GB harddrive ATM, and would prefer not getting another unless absolutely necessary.

What I'm looking for help on is the ideal step-by-step process to setting up this system as a tri-boot including partitioning instructions.

---

### Post by yeats on 2009-01-28
I think you're going to have to do some serious planning here, but these are good guides:

Windows 7 with XP installed:

[http://lifehacker.com/5126781/how-to-dual-boot-windows-7-with-xp-or-vista]("http://lifehacker.com/5126781/how-to-dual-boot-windows-7-with-xp-or-vista")

Linux with XP installed:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")

I would suggest:

1.  going ahead and creating enough free space in the gParted step for both OS's - I don't know enough about Win7 to know whether it will assume you want it to take up all available free space - if so, you might use these guides:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")
and, if necessary,
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

2.  install Ubuntu last - this ensures that GRUB is your bootloader without having to go back and install it later.  Ubuntu should detect both Windows partitions without a problem and assumes that you want to keep them by default.

Good luck!

---

