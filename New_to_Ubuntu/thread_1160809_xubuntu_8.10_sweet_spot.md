---
title: "xubuntu 8.10 sweet spot"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by mesmith on 2009-05-16
Dell Dimension 3000, dual P4, 1 gb memory.

I have been happily using xubuntu 8.10 for 6 months.  There were a couple of niggles.  Every 10 cold boots, or so, I would get a boot hang with "checking battery status."  I would also get an occasional grub error, usually 16, but this would disappear on reboot.  No real problems.  While poking around the bios on a boot, I looked at the legacy device settings.  In there, I found a setting for on-board memory buffer, which was set to 1mb.  The other option was 8mb.  I made the change to see what would happen.  Firstly, xubuntu splash progress screens showed up on boot and shutdown (never seen them before) and boot hangs disappeared.

Then came the upgrade to the 2.6.27-14-generic kernel.  Grub errors disappeared.

I have no idea as to why any of this should have happened.  As a nooby, I don't have the skills to find out.  But, maybe my experiences will help someone else.

Xubuntu 8.10 was great, but now it's extraordinary.

If they'd just backport Abiword 2.6.6 to 8.10 that fixes the partially broken help system, well, it would be perfect.  I'd move to 9.04 the day before they released 9.10.

---

### Post by MontelEdwards on 2009-05-21
It probably was the new Kernel.
Have you looked at upgrading to Jaunty?

---

### Post by mesmith on 2009-05-22
I'm kind of appalled at the level of problems with 9.04.  Especially the video problems.  The release should have been delayed in my opinion.  Of course, zillions of users think I'm wrong.

---

### Post by QIII on 2009-05-22
I haven't found any level of problems with Jaunty . . .

That said, those who have legacy ATI graphics whose drivers are no longer supported by ATI (and are now "legacy" in Ubuntu) have certainly had problems.

The only issue I have had thus far is actually an Xorg regression which causes Xorg to fail to release memory after certain types of graphical objects are created and then destroyed.

That's an Xorg issue, not an Ubuntu issue.

---

