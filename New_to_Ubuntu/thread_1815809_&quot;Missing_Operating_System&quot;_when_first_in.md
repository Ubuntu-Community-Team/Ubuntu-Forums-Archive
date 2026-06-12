---
title: "&quot;Missing Operating System&quot; when first installing"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by Alexanderbot on 2011-07-31
Hello,

I am new to Ubuntu and wanted to try it out so I followed this link to install it:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I have a 2011 Macbook Pro and after following the instructions it installs it just fine(w/ rEF It), but when I leave it and restart my computer and try to enter back into it it gives me the message "Missing Operating System" and then just blinks.  I have searched for some information on this problem and see that it might be a problem with my grub (boot loader)? My setup is
/dev/sda1 fat32               EFI
/dev/sda2 hfi+                Macintosh HD
/dev/sda3 hfi+                Recovery HD
/dev/sda4 linux-swap
/dev/sda5 ext4

Thank you.  I appreciate your help.

---

### Post by powerpleb on 2011-08-01
Sorry, I'm not very savvy with Macs. But the first thing I would do, if I were you, would be to boot up with the live CD, run the partition editor and make sure that the correct hard drive (the one with the GRUB bootloader installed - probably your Ubuntu root partition) is flagged as bootable.

---

