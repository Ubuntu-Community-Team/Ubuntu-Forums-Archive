---
title: "Is fake RAID safe if the mobo dies?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Sydius on 2008-12-31
I just installed a fake RAID using my nVidia chipset motherboard (MCP51 Serial ATA Controller, I think).  I want to access it from both Windows and Linux.  It works okay, but I was wondering, if the motherboard dies, would there be any way to read the data from it without having the exact same motherboard? Is there a software solution available for Linux to do this?  I wouldn't need to boot from it; just get the data.

---

### Post by Nostalos on 2008-12-31
I can't vouch for any chipset besides Nvidia, but yes it should be safe if moving from one Nvidia Raid chipset to another.   I moved my RAID install from an Nforce3 to an Nforce4 Motherboard with no issues (well other than the typcial Windows Freaking out about drivers of course)

The link below is a how-to on installing pre 8.10 to a fakeraid system.  Its pretty much the same scenario for data recovery as well.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)


Also the 8.10 alternate installer (not sure if live cd does or not)  auto detects Nvidia Raid controllers.   The only issue I had reinstalling to my Nvidia Raid with it was Drive Geometry.  I had to boot to live cd and reinstall grub manually to get it to boot.    How to manually set disk geometry in Grub is listed in the above howto as well.


*Edit*  Just read my own link ;)  Its been updated to refelct changes in 8.10.  and it is only on Alternate Installer.

---

