---
title: "Installing Ubuntu completely seperate of everything else..."
date: 2010-03-31
forum: New to Ubuntu
---

### Post by Dreakon on 2010-03-31
Hello, I'm not on Ubuntu at the moment so you'll have to excuse me if I can't be very specific.

However, my goal is to install Ubuntu completely seperate from everything else.  I understand partitioning, I normally keep my /home directory seperate from my / (the Ubuntu directory), and of course set aside some area for the swap.

Am I wrong that if I install VirtualBox and a copy of Windows, that it does into the / area rather than the /home?  What about other software like OpenOffice and Empathy and Skype (when I install it)?  Is there any way to keep those completely seperate from the actual Ubuntu installation as well?

The reason I ask is because I am conflicted between going with Ubuntu 10.04 or finding a rolling release distro.  I don't mind upgrading every 6 months or whatever, as long as everything else I have and have gotten on my laptop remains intact.

So basically, I want Ubuntu to sit on it's own 5GB partition or whatever and have nothing else really go on or off of that partition until I upgrade 6 months or so from now (in which case, that partition will be the only one touched when 10.10 is released).  Is that possible?

---

### Post by Nisal on 2010-03-31
open office comes with ubuntu so nothing to worry about

and please refer this 

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Dreakon on 2010-03-31
Well, I suppose my biggest concern are the things that aren't OpenOffice, like VirtualBox/Windows and Skype.  If I install those and choose to upgrade Ubuntu 7 months from now, will I need to reinstall VirtualBox/Windows and Skype and whatnot?

If so, is there any way to avoid that?  Like installing those programs and others elsewhere so I can dedicate a partition to Ubuntu system files and _only_ Ubuntu system files?

---

### Post by halitech on 2010-03-31
Applications normally end up in / but user files (like the virtualbox hard drives) will normally go into your home folder.

---

### Post by Dreakon on 2010-03-31
> **halitech said:**
> Applications normally end up in / but user files (like the virtualbox hard drives) will normally go into your home folder.
Any way to redirect where applications and other things that end up in / go?

---

### Post by QIII on 2010-03-31
If you add the VirtualBox PUEL source to your sources list (I'm  not at my Ubuntu machine), then save a list of your installed applications, your sources list and some odd things like your hosts file to your /home you should be OK there.  The virtual drives for your VirtualBox guests are saved in /home (as above).

With the right files saved, you can easily reinstall and reconstruct your system.

Skype is another matter and I suspect that would have to be reinstalled.

---

### Post by halitech on 2010-03-31
> **Dreakon said:**
> Any way to redirect where applications and other things that end up in / go?

only way I know of would be to compile from source and use the proper switches to install in a different location but I don't know if that will work with all apps or not. (not to mention it would be a pain to keep updated)

---

### Post by QIII on 2010-03-31
Let me add that if you install from Synaptic, the update process for each application will likely expect to find the application where it is installed by Synaptic by default.  Forcing them to be installed elsewhere may not only make updating them difficult.  It may make updating them impossible, or cause some other unknown catastrophic behavior.

---

