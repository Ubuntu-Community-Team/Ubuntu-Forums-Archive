---
title: "once again black screen after update and restart"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by jrandolph on 2009-10-22
I jus got an update for the kernel and after the restart all I get is a black screen with my mouse pointer - it like X doesn't start
this has happened to me 3 times since I upgraded to 9.04
can anyone give me a suggestion or a way to fix this I'm getting so tired of having to go through another fresh install

---

### Post by jrandolph on 2009-10-22
does this have to do with my video card I know my vid card is no longer supported considering that I have looked into the to a great extent
right now I have a radeon x550 - but if that's it then why does it work for a little while and then out of nowhere not come back after a restart

---

### Post by tarps87 on 2009-10-22
I could well be related to the driver. You say that you update the kernel and then it gets a back screen next reboot, this could be because the restart will load the new kernel which does not contain the driver for your card. What happens if you select an older kernel from grub?

---

### Post by jrandolph on 2009-10-22
same thing no matter what kernel I choose

---

### Post by kmuzheri on 2009-10-22
When you are installing your Ubuntu 9.04, there is an option to press F4 for more installation MODES. So press F4 and select the Lower Graphics Mode. You are currently trying to install while in the Normal Graphics Mode, so by default you may not have the appropriate drivers. By choosing the lower graphics mode, you can install and later look for the appropriate drivers for much nicer GUI.

Keep me posted.
Good luck

---

### Post by jrandolph on 2009-10-22
but I have had this installed 3 different times and it works great for some time then jus likei said out of nowhere it doesn't want to work

---

### Post by tarps87 on 2009-10-22
Have you tried using the fail safe driver (vesa)?

Can you post the output of cat /etc/X11/xorg.conf

---

### Post by jrandolph on 2009-10-22
so is there a way that I can boot into a lower graphics mode from the grub menu

---

### Post by jrandolph on 2009-10-22
well I really can't post the output cuz I'm on my mobile

---

### Post by jrandolph on 2009-10-22
ok how about this - I'm going to switch to 8.04 LTS - I wud like to make a small backup of my current drive - within the drive - can anyone tell me how to do so from the command line

---

### Post by HarrisonNapper on 2009-10-22
Depends on how you're going about the new install, but it might be a good idea just to keep a separate partition for your home folder anyway. Unfortunately, I'm not at my computer right now and I could really screw something up by pasting the wrong command, but you can read the man page on gparted to create the partition from command line, mount the partition, and then move a copy of your home folder over to the new partition.

Hopefully, someone will get the commands out soon, but I can do it when I get off of work if no one else has by then. But that's in 8 hours, so it might be better just to check out what man pages and apropos (if you need it) have to offer.

---

