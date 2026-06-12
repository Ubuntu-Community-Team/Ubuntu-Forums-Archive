---
title: "Mouse no longer works after upgrade to 9.10"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by daedalusman on 2009-11-01
I upgraded my computer to karmic 9.10 today. Using the desktop cd to do a complete reinstall. The installation went fine until I booted in to the new system for the first time. At this point the mouse was no longer working. The pointer doesn't and move and the buttons don't work. Can anyone help out here? Let me know if you need anymore information. Thanks.

---

### Post by NapalmK on 2009-11-01
I have an identical problem after upgrading from 9.4. If anyone can help it would be greatly appreciated. Thanks!

---

### Post by Maxwell Waters on 2009-11-01
Bumped. I upgraded from 9.04 to 9.10 and ran into the mount problem many people had, and I reinstalled 9.04 but backed up my user data, and now my mouse, too, isn't working.

As a side note, how do I get to the panels on Gnome w/out the pointer?

---

### Post by kenyot on 2009-11-02
I have the same problem after upgrading from 9.04.

HP TX2108. AMD64

---

### Post by Spartan-196 on 2009-11-03
Yep... just upgraded from  9.04 on my laptop and the trackpad no longer functions, usb mice work fine. I upgraded a desktop earlier and it worked fine with the PS2 mouse. I think this may just be a problem with the hardware detection unfortunately. I am running on a Lenovo 3000 N100 Pentium Dual-Core.

I am currently poking around to see if i can find anything.

---

### Post by c_07 on 2009-11-27
I am experiencing the same behavior. On the first reboot after upgrading from 9.04 to 9.10, the mouse -- a touchpad on a Compaq Presario C500 laptop -- is frozen in the middle of the screen, although the rest of the OS is responsive (keyboard works OK). I have tried 'dpkg-reconfigure xserver-xorg' to no effect.

If anyone has found a solution to this, I'd love to hear it.

---

### Post by musarraf172 on 2009-11-27
> **c_07 said:**
> I am experiencing the same behavior. On the first reboot after upgrading from 9.04 to 9.10, the mouse -- a touchpad on a Compaq Presario C500 laptop -- is frozen in the middle of the screen, although the rest of the OS is responsive (keyboard works OK). I have tried 'dpkg-reconfigure xserver-xorg' to no effect.

If anyone has found a solution to this, I'd love to hear it.

Try this on your command line:

"echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"

Then restart..

---

### Post by ankspo71 on 2009-11-27
> **Maxwell Waters said:**
> 
As a side note, how do I get to the panels on Gnome w/out the pointer?

Hi, here is some information about keyboard navigation. [http://library.gnome.org/users/gnome-access-guide/stable/keynav-0.html.en](http://library.gnome.org/users/gnome-access-guide/stable/keynav-0.html.en)  The Tab key can be very useful to switch different box/dialogs/prompts in various parts of the desktop etc. Alt+F1 brings up the main menu.

Hope it helps,
James

---

### Post by c_07 on 2009-12-02
Many thanks (musarraf172)! This worked like a charm.

---

### Post by musarraf172 on 2009-12-02
> **c_07 said:**
> Many thanks (musarraf172)! This worked like a charm.

Enjoy your karmic Kola ,  :popcorn:

@ daedalusman,

Please change the thread as solved!!

---

### Post by empath_eia on 2010-06-16
I've tried both possible fixes listed in this thread but my touchpad mouse still isn't working. When I copy/pasted echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe into my command line as root, it did nothing at all. 

I'm using a USB mouse for now, which does work, but I much prefer the touchpad.

---

