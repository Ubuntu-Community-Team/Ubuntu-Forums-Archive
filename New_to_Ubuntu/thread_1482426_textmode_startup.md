---
title: "textmode startup"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by bouncingwilf on 2010-05-13
Sorry I'm a novice with limited knowledge and could not find an answer to my problem in the forum (wrong search terms I expect).

Just Upgraded from Karmic to lynx and all went well except on second re-boot ( it was ok on first re-start) the system complained that it was going into low resolution mode because it could not load the nvidia drivers.

To cut a long story short, I cut and pasted a monitor section for my screen (Acer AL1916W) into the xorg.conf file of the Internet  and now the computer just hangs on startup.

I'm sure I can eventually sort things out BUT I can't seem to find a away of getting the PC into textmode on startup?

How do I do this please?

---

### Post by quadproc on 2010-05-13
> **bouncingwilf said:**
> ...
Just Upgraded from Karmic to lynx and all went well except on second re-boot ( it was ok on first re-start) the system complained that it was going into low resolution mode because it could not load the nvidia drivers.

To cut a long story short, I cut and pasted a monitor section for my screen (Acer AL1916W) into the xorg.conf file of the Internet  and now the computer just hangs on startup.

I'm sure I can eventually sort things out BUT I can't seem to find a away of getting the PC into textmode on startup?

How do I do this please?
The usual installation provides both a standard and a recovery selection for the operating system release.  The recovery one is usually the selection just after the standard one.  If you boot into that selection then you will get a command line interface which you can use to examine and change things.

Also, if you have a CDROM or a USB flash drive with the operating system on it then you can boot from that.  You should then be able to make repairs.

You may also be able to make some progress by renaming your xorg.conf file.  The new OS does not require xorg.conf; if it needs to, it will probe the hardware and attempt to do what makes sense.  Renaming the xorg.conf file prevents the system from finding it but still leaves it on your disk in case you want to fix it and use it.

quadproc

---

### Post by bouncingwilf on 2010-05-13
Sadly, at no point do I get a chance to choose an alternative startup the as the system boots straight to a graphical environment and I've yet to find any key combination that will allow me into text mode. Also my PC, an Acer l100 has no boot from USBoption  and my only means of burning a cd is on the dead PC

What I'm looking for is some sort of keystroke combination that will allow a texmode startup ( Once I achieve that, I have backups of the xorg.conf file).

Grateful for any ideas.

---

### Post by new_tolinux on 2010-05-13
> **bouncingwilf said:**
> What I'm looking for is some sort of keystroke combination that will allow a texmode startup ( Once I achieve that, I have backups of the xorg.conf file).

Grateful for any ideas.
I assume that you'll have grub2.

Both Karmic (9.10) and Jaunty (9.04) had a brief option just after your bios screen to press 'ESC' to enter the boot options menu (the grub2-menu in case of Lucid). It's a short one, so easy to miss.
From there you'll shoud be able to choose a recovery-promt. Then you should be able to rename/remove your xorg.conf

But I only have a Karmic-machine ATM which I can't reboot yet (it's busy ;)), so I can be totally wrong about my guess for Lucid.

---

### Post by quadproc on 2010-05-13
> **bouncingwilf said:**
> ...
What I'm looking for is some sort of keystroke combination that will allow a texmode startup ( Once I achieve that, I have backups of the xorg.conf file).

I am not clear about how far you get in the boot process but here are a couple of ideas:

ctrl-alt-F1 should initiate a terminal session if the system is running.  Not sure if yours is.

ctrl-alt-backspace _may_ kill the X server; not sure about this because this behavior used to be standard but was removed at one point and may not have been restored in standard releases.

ctrl-alt-F7 should give you an X session once you have a working graphics setup.

quadproc

---

