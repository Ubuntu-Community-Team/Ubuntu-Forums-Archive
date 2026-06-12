---
title: "Vista Dual Boot GRUB missing menu.lst"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by dslocum on 2010-03-12
Hi All,
 
Yeah, I know. This has been asked 1000000 times before, but I can't seem to find the exact answer - probably just can't figure out the right question! :-)
 
I installed the most recent Ubuntu on my Vista machine by following this:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
 
Works great, but it always boots into Ubuntu. It suggests a complicated method of modifying the menu.lst file, but there is no menu.lst file. Then I found a thread that suggested using EasyBCD, so installed and configured that.
 
However, it still boots into GUB first, and then into EasyBCD. 
 
What's the best course of action to allow me to boot to Vista by default, allowing me to select Ubuntu before a timeout?
 
Thanks in advance and sorry for asking dumb questions.
 
Doug

---

### Post by howefield on 2010-03-12
Try startupmanager.

It is in the repository, so you'll can install with Synaptic Package Manager.

---

### Post by Mark Phelps on 2010-03-12
> **dslocum said:**
> ... but there is no menu.lst file. 

That's because GRUB2 (the default with new Ubuntu 9.10 installs) does not use menu.lst anymore.

To get access to your Windows install, boot into Ubuntu, open a terminal, and run "sudo update-grub".  It will display each kernel and OS that it finds.  You should see a line something like "Vista/Windows loader on xxxx".

Reboot.

Next time, you will have a GRUB menu and an entry for Windows.

---

### Post by Method X on 2010-03-12
And no more menu.lst.
Its grub.cfg from now.
;)

---

### Post by dslocum on 2010-03-12
[Solved].
 
Boy was that easy and staring me right in the face.
 
I just needed to go into EasyBCD, click "Manage Bootloader", select "Reinstall the Vista Bootloader" and click "Write MBR".  Then restarted the machine.
 
Now EasyBCD asks which partition to select (instead of GRUB) and defaults to Vista.
 
Thanks anyway folks.  I hope my experience is helpful to others.
 
Cheers!
 
Doug

---

