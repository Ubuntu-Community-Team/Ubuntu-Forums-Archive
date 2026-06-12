---
title: "Very annoying GRUB issues"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Vonnick on 2009-04-27
OK, Ubuntu is amazing when it works. Sound, Compiz, etc. Except for one thing... It takes 15 minutes to boot up. First, GRUB hangs for about 10 on "GRUB loading stage1.5", then another 5-7 minutes on "GRUB loading, please wait..."

Why is it doing this? I installed Ubuntu on a fresh hard drive, by the way. I'm not dual booting with anything.

---

### Post by philinux on 2009-04-27
Install startupmanager from synaptic. The menu item appears in system>admin.

Tick the box to "show text at boot".

When it hangs make a note of what its hanging on. Not sure about the stage 1.5 hang though. Also try unplugging any usb hubs or devices.

[edit] It could be signs of hard drive failing or a bios problem.

---

### Post by Cypher on 2009-04-27
The only delay in GRUB before hitting the Kernel boot, should be the 10 second timer allowing you to choose which option you want. From the power-up to the GRUB menu should be nore more than 10-15 seconds.

It looks like there is something screwy about your setup if it takes that long to get int the GRUB menu. Check your BIOS about the boot order and make sure it's something like CD-ROM and HD, as opposed other things before this. It's possible it's off seraching on non-existing drives before it really gets your HD and loads up..

---

