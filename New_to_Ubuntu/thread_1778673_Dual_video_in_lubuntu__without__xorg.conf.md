---
title: "Dual video in lubuntu _without_ xorg.conf"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by triceratops on 2011-06-09
Hi,  Okay, I've refitted an old pc with lubuntu natty.  It's running dual screen with a very old dual port ati card (raedon 9200 pro).  Under xubuntu I was able to run dual monitors without having to write an xorg.conf file.  Can lubuntu run dual monitors without xorg.conf as well?

     fglrx and the open source ati drivers never worked under xubuntu, but they might work here.  I'd rather avoid using drivers, as they tend to create more problems then they solve.  Drivers might be the only option, though.

  I've tried inserting xrandr into the .profile and .xprofile commands in ~ and /etc.  No luck.    Now I'm running arandr in the autostart file and manually adjusting the screens after bootup.  I'd rather automate the process though.  Any thoughts?

---

### Post by triceratops on 2011-06-09
Problem solved, sort of.  I ran arandr, saved a dual monitor configuration to a shell script, and aliased the shell script in .bashrc.  When I enter lubuntu, I run the alias in a terminal.  This resets the monitors for dual screen.  Not elegant, not automatic, but it works.  Sorta.  I'll work on a more permanent solution when I have more time.

---

