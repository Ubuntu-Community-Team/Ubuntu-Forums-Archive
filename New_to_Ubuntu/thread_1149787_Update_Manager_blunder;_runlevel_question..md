---
title: "Update Manager blunder; runlevel question."
date: 2009-05-05
forum: New to Ubuntu
---

### Post by gir9999 on 2009-05-05
hardy 8.04

Update manager came up, i looked at the packages to be installed and one was a kernel update and i think one of these needed to edit my menu.lst file but i turned it down being cautious, this caused my next reboot to end up in low graphics mode.

so,

1: how do i fix menu.lst
also
2: how do i get into runlevel 3 without starting xserver for graphics driver reinstall (i XFIX'ed my xorg.conf)

many thanks

---

### Post by wizard10000 on 2009-05-05
> **gir9999 said:**
> hardy 8.04

Update manager came up, i looked at the packages to be installed and one was a kernel update and i think one of these needed to edit my menu.lst file but i turned it down being cautious, this caused my next reboot to end up in low graphics mode.

so,

1: how do i fix menu.lst
also
2: how do i get into runlevel 3 without starting xserver for graphics driver reinstall (i XFIX'ed my xorg.conf)

many thanks

I'm guessing you're using a video driver that's not in Ubuntu repos.  The driver needs to match the kernel and if you've manually installed a video driver then you need to manually update it  ;)

You can boot into recovery mode and install the video driver - runlevel 3 is multiuser mode but you can boot into single-user mode with networking and install the drivers.

Or - you can just disable or uninstall gdm - which by default will leave you at runlevel 3.

Or - 'sudo init 3' from a terminal window should kill X and leave you at a console prompt.

---

