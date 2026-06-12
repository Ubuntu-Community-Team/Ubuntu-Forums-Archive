---
title: "My planned dual-boot setup: will this work?"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by rimshot4 on 2010-01-13
Hey All,

I've got two hard drives, both IDE, but only one IDE slot (true story, it's a small box). I've ordered a kit to convert one IDE drive to a USB 2 external drive. The other HD will remain internal and holds the juggernaut Windows XP.

I've read that data transfer on IDE is much faster than on USB 2.0. My plan, then, is to swap out my IDE drives, convert the Windows XP drive to an external USB drive, and install Ubuntu on my (newly) internal drive.  

My plan, then, is install and boot normally into Ubuntu, and to set my BIOS to boot off of USB when present. That way (theoretically) I won't have to mess with the normal "dual boot" setup on either of my HDs, and I will simply plug in the Windows XP USB hard drive when I need to run XP. So, theoretically, UBUNTU will be blissfully unaware of XP, and XP will be largely unaware of Ubuntu (except for files on the internal hard drive, of course).

Will this work, and if not, what's a better solution?

---

### Post by fancypiper on 2010-01-13
IDE slots usually handle two drives, master and slave. Are you using both?  You may just need a new cable with the two drive plugs.

I tried using an external USB drive once and it was slow and unreliable, so I took the drive out and put it inside the computer and no problems.

---

### Post by Cheesemill on 2010-01-13
According to Microsoft it's impossible to run XP from an external drive.

Actually it will, but you need to spend about an hour hacking and rebuilding the XP install disc before performing a clean install with it. Even then performance is very slow and it doesn't work perfectly, you still get occasional errors. I've tried it once and it's simply not worth the effort.

A better idea might be to install a dual-boot on your internal drive and use the external for media/document storage.

---

### Post by deadalus.globalnode on 2010-01-13
I agree with cheesmill. It is a lot easier to get windows and Linux to get along on one Ide hard drive. plus that way you don't have to switch out hard drives all the time. also in my experience you don't loose that much speed by using usb. unless of course it is 1.0.

---

### Post by tom.swartz07 on 2010-01-13
> **deadalus.globalnode said:**
> I agree with cheesmill. It is a lot easier to get windows and Linux to get along on one Ide hard drive. plus that way you don't have to switch out hard drives all the time. also in my experience you don't loose that much speed by using usb. unless of course it is 1.0.

again, i concur.

even if the drive is so small that you could only install the OS's themselves on the internal drive, you could still configure them to store all of your data on an external USB hard drive.

My big desktop is configured so that my /home folder for Ubuntu is stored on an external drive. 



Additionally, if you try to boot with the swapout hard drives, you might run into Grub errors and such that cause even more grief. 



Long story short, just install em on the internal, and plug an external in for more room.

---

### Post by rimshot4 on 2010-01-14
Thank you all for responding. 

So obviously XP on USB is a nix. 

Tom, how do you configure Ubuntu so your /home/ folder is on another drive? Is this an option available during installation?

---

### Post by warfacegod on 2010-01-14
If your "small box" has a Floppy drive, you could probably take it out and replace it with your other hard drive. They are basically the same size.

---

### Post by rimshot4 on 2010-01-15
> **warfacegod said:**
> If your "small box" has a Floppy drive, you could probably take it out and replace it with your other hard drive. They are basically the same size.

Nope, nothing but a hard drive slot and a DVD drive slot. It's a used office machine, IBM. It actually kind of "folds in" on itself when you close the case. The PCI slots are actually on a special card that plugs into another slot. If you need to get to some hardware, you actually have to remove the card that has the PCI slots on it. Very unusual design. Tiny for a desktop.

---

### Post by warfacegod on 2010-01-15
> **rimshot4 said:**
> Nope, nothing but a hard drive slot and a DVD drive slot. It's a used office machine, IBM. It actually kind of "folds in" on itself when you close the case. The PCI slots are actually on a special card that plugs into another slot. If you need to get to some hardware, you actually have to remove the card that has the PCI slots on it. Very unusual design. Tiny for a desktop.

Sounds like allot like a Dell mini. They open like a book. Lots ofplaces for heat to get trapped. Very stupid design.

---

