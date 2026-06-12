---
title: "NVidia Config Shell Script"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by Dr.Tommy on 2009-07-05
I'm a complete noob - dabbled with Ubuntu for ~2 weeks a year and a half ago - it fried my system (dual boot didn't play nice...)  I'm back again after using wubi - and loving it all over again.  I'm useless with the terminal - here's my problem:

- I have a double monitor setup and an NVidia graphics card.  I downloaded the NVidia proprietary driver.  When I launch the NVidia config manager, my 2nd monitor is disabled.  I config the second monitor to "TwinView", choose its position as "on the left" - Apply settings and I'm good to go.  When I try to save the config, it won't let me (it can't make the xorg.conf.backup file in the X11 directory).  I logged in as root - saved the config file, rebooted and the graphics crashed - Ubuntu wouldn't evne load.  I had to reinstate the bakcup xorg.conf file through the terminal (no small feat for me).  So, it seems if I setup the display config within Ubuntu it works fine.  If I save that config and it loads up at boot, it crashes the display settings.  

As a work around, I'd like a macro that sets the display config to what I want through the NVidia manager each time Ubuntu is done booting - as an autorun at startup, but I can't find an app for such a macro (tried xnee and xmacro - installed both with synaptic, but couldn't find them in Ubuntu after install).  From what I'm reading, I need a shell script, but being useless with the terminal, I don't know where to start.

Any help would be greatly appreciated!
- Tom

---

