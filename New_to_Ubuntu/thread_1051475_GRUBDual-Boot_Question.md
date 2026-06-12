---
title: "GRUB/Dual-Boot Question"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by semi_fiction on 2009-01-26
Hey all, just wondering:
I am dual-booting Vista and Ubuntu on a seperate desktop. I installed Vista first, so now I'm using GRUB to boot. Can I safely use the "fixmbr" from the Vista recovery console to reinstall the Windows boot loader then create an Ubuntu entry using EasyBCD and still be able to boot to Ubuntu? I would use GRUB but I like the convenience of being able to remove various linux partitions without getting the inevitable "GRUB Error *insert number*" messages.

---

### Post by caljohnsmith on 2009-01-26
Sure, you can use EasyBCD to set up Vista's boot loader to boot Ubuntu if you want to. If you haven't all ready seen this tutorials, you might find them helpful:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5)
[http://neosmart.net/wiki/display/EBCD/NeoGrub](http://neosmart.net/wiki/display/EBCD/NeoGrub)

I would recommend using EasyBCD to first set up Ubuntu in your Vista boot loader, and then once you've confirmed you can boot Ubuntu from Vista's boot menu, then you could run "fixmbr" to get rid of Grub (or if you have a Vista CD, it would actually be "bootrec /fixmbr"). Good luck and let me know how it goes.

---

### Post by semi_fiction on 2009-01-26
Ok, well i downloaded the latest version of EasyBCD and installed it, and when I run it I get this error message:
```
EasyBCD has detected that your BCD Boot data and MBR are either not from the latest version of Windows Vista, or don't yet exist.
```
And it asks me to press OK to correct these issues. When I do, it then tells me it could not detect the drive letter of my boot device. When i select "C:\" and press ok, i have to select "C:\" again as the drive letter of the Vista install. When i hit OK from there, I get this error:
```
The store import operation has failed. 
A device attached to the system is not functioning.
```
Now, I am running 64 bit Vista, but I read EasyBCD 1.7.2 works on 64 bit machines.

---

