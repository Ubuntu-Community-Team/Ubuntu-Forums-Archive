---
title: "black screen after update"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by apox77 on 2010-06-16
So yesterday I performed an update on Lucid and I noticed it updated something with xorg.  This morning, upon boot...I get the black screen.  I've had this in the past and I know its from the ATI driver.  I always do the "aticonfig --acpi-services=off" thing and it always works.  I did not do it yesterday since it was only updating xorg an other things.  

My propblem is that I cannot enter failsafe or recovery mode or get to any terminal windows (ctrl-alt-F1 etc.).  As the boot process begins, holding down the shift key does nothing.  pressing esc during boot does nothing  I keep having to do a hard reset and I am frustrated at this point.

Any help would be greatly appreciated.

Ed

---

### Post by apox77 on 2010-06-16
Well I booted with a live CD, opened up /etc/X11 as root and deleted the xorg.conf files except the original and failsafe.  rebooted and everything was ok.  Reinstalled fglrx, ran aticonfig --initial -f and aticonfig --acpi-services=off.  rebooted and all is well again.

---

