---
title: "[SOLVED] VirtualBox is being mean!"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Cadeyrn on 2008-12-20
So, I have a problem that's obvious and has been fixed by other people tons of times, but I can't find help on the internet ANYWHERE that's understandable to Linux newbs like me. So I need a step-by-step guide for fixing this:

I create a machine and set everything to reasonable settings, but when I try to launch, it says "FATAL: No bootable medium found! System halted."

Now, I know that means the virtual machine can't find its operation system, and I know it has something to do with the fact that my virtual CD Drive is mounted to the default (/dev/scd0) instead of what it should be, /dev/cdrom. I just don't know how to change the mounting or do whatever I'm supposed to do next.

---

### Post by Zeedok on 2008-12-20
Try these steps (and check out my screenshot - a picture tells a thousand words):

1. Select the virtual machine you've just created in the right hand panel of Virtualbox.  
2. Right click and choose settings, select the DVD/CD option on the right panel of the window that pops up (third icon from the top)
3. Check the box "Mount CD/DVD Drive", then check "ISO Image File", use the folder icon next to it to find your live cd image file (.ISO)
4. Reboot your virtual machine.

Good luck, hope that helps for you

---

### Post by Cadeyrn on 2008-12-20
Well, yeah that's another problem I came accross before making this topic--my /dev/cdrom is not a mountable ISO file. I'm pretty sure it doesnt even have a file type. Should I rename it to cdrom.iso?

Screw it, I'll try renaming it. I'll mark this solved if it worked.

EDIT: Oh, I feel like such a newbie :P

Your picture just showed me what I needed to know. Screw renaming the file XD

Man, one upside that I was once retarded enough to get a Mac, then even more retarded to install Windows on it: I HAVE LEGAL COPIES OF ALL THREE POPULAR OPERATING SYSTEMS :D!!!!!!! Making an iso of WinXP now.

---

