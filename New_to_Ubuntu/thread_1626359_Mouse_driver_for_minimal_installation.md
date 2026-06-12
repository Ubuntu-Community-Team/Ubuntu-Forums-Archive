---
title: "Mouse driver for minimal installation"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by peter1608 on 2010-11-20
I am trying to set up a minimal 10.04 installation - my reason for so doing is that I want to tailor it to exactly the packages I want (and a British keyboard), then create custom Live CDs.  My attempts with the standard installation all yielded .isos over 700Mb, which of course would not fit on a CD.

I found the minimal intallation from [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD), downloaded the 32 bit flavour of 10.04 and burned it to CD. I then did a clean install this on a standby machine (not shared with any other os), and followed the instructions from the above site.  The base system installed ok, so I logged in and typed "sudo tasksel" as instructed.

From here it was guesswork, as the instructions stopped at this point.  I was presented with a menu of installation options, and no apparent method of selecting any of them.  Eventually I discovered that the space bar selected the currently highlighted option.  I selected the gnome desktop, and it whirred away for an hour or so downloading packages.

When I rebooted, the familiar desktop was displayed, but the mouse pointer was stuck in the middle of the screen and would not respond in any way.

So my immediate question is 'How can I enable my (USB) mouse'.  It worked fine on previous installations of the full system on the same machine, so clearly something is lacking.  I assume I need to type "sudo apt-get install something", but what is the something?

Peter

---

### Post by northern lights on 2010-11-20
[http://www.ehow.com/how_6470171_install-drivers-command-line-ubuntu.html]("http://www.ehow.com/how_6470171_install-drivers-command-line-ubuntu.html")

---

### Post by peter1608 on 2010-11-20
Thanks for this

But ... booted the system up today and the mouse worked.  Can't explain this - I did try a reboot last night, and the mouse refused to move.

A one off or a precursor of an intermittent problem? 


Peter

---

