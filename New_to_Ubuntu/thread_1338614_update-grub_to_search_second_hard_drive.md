---
title: "update-grub to search second hard drive"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by stans on 2009-11-26
How do I get update-grub to search a second hard drive for a new kernel ? I have Mint on one drive, and Ubuntu on a second one. The most recent Ubuntu update downloaded a new kernel and I'd like to see it on the boot menu. Mint (Gloria) is my primary default boot drive.

---

### Post by Buuntu on 2009-11-26
I'm not sure about this, but I don't think grub can list partitions on different drives.  I think which hard drive you boot off of is handled by your BIOS.  Grub only lets you pick between partitions in one hard drive (I believe).  However, each hard drive can have its own grub menu, it's just a matter of changing which one to boot off of in the BIOS first.

---

### Post by kansasnoob on 2009-11-26
> **stans said:**
> How do I get update-grub to search a second hard drive for a new kernel ? I have Mint on one drive, and Ubuntu on a second one. The most recent Ubuntu update downloaded a new kernel and I'd like to see it on the boot menu. Mint (Gloria) is my primary default boot drive.

What version of Ubuntu? What version of grub?

Should have added, to determine version of Ubuntu run "cat /etc/issue", to determine version of grub run "grub-install -v".

---

### Post by stans on 2009-11-26
Ubuntu is 9.10 - not sure about grub version - can I find out without rebooting ?

I may have solved this myself by editing menu.lst (after making a backup copy of course) and copying the lines for the last kernel and renaming relevant parts to the new version. Did the 'update-grub' command and rebooted... and my new Ubuntu kernel appeared in the selection list. 

Could it be that simple ?

---

### Post by kansasnoob on 2009-11-26
If you still have a menu.lst it's legacy grub.

And legacy grub does NOT detect changes in other OS's.

So yes, it's that simple. Just use a bit of copy-n-paste. Create a new entry in the menu.lst above the old one, then edit the kernel # and save.

I personally wouldn't recommend upgrading to grub2 with multiple drives just yet. It can sometimes be a real pain in the rear!

It is improving however.

---

### Post by Buuntu on 2009-11-26
Sorry :P, yeah I was wrong...

---

### Post by stans on 2009-11-26
Thanks for the responses. Yes, I will hold off on grub2.

---

### Post by kansasnoob on 2009-11-26
> **Buuntu said:**
> Sorry :P, yeah I was wrong...

Not altogether!

As far back as Gutsy (possibly further) the installer (I think it was even then ubiquity) did a good job of finding existing OS's. Not so much after installation!

While it's a major frustration sometimes, grub2 is improving that whole thing. Once they have all the bugs ironed out you should literally be able to run one command and have all OS's detected.

I'm using the latest version from Debian Sid and it's pretty good but still fails randomly with multi-drive machines.

---

