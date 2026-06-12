---
title: "Suspend mode won't work"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by kiniyaloca1 on 2010-12-09
Whenever I click the suspend button, my laptop enters  suspend mode, but once I resume the computer restarts at the grub 2 menu. I am pretty new to linux so please be descriptive in reply please.

-Running Ubuntu 10.10 amd 64 on a partition alongside windows 7 on sony vaio-vgn fw390

---

### Post by think13 on 2010-12-09
It looks like your laptop is shutting off instead of suspending. Are you sure that it's set up that way for Ubuntu? Those settings can be different between Windows and Ubuntu. You can check this by going into System->Preferences->Power Management and selecting the General tab.

---

### Post by NikoC on 2010-12-09
This did the trick for me on an Sony Vaio VGN-NS21Z running 10.04
open /etc/default/grub with a text editor
e.g. sudo gedit /etc/default/grub

Change GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX="acpi_sleep=nonvs" 

Save the file and update grub with sudo update-grub.

Reboot.

I got the info from [this]("http://ubuntuforums.org/showthread.php?t=1596545&page=4") thread.

---

### Post by kiniyaloca1 on 2010-12-09
Thanks think13 and NikoC.
-Niko this worked perfectly, not being able to enter sleep mode was the only thing keeping me from completely switching to Ubuntu. Thank you guys for responding so quickly, with great instructions. You rule.

Thanks,

Kiniyaloca1

---

