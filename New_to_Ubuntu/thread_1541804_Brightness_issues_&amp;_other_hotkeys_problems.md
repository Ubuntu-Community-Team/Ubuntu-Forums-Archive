---
title: "Brightness issues &amp; other hotkeys problems"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by bripa on 2010-07-29
Hi,

New to Linux, I need support. I have the hotkeys and above all brightness issue aftre first installation.

the ubuntu support website say: 
"Brightness control doesn't work properly. Pressing Fn-F5 or Fn-F6 changes the brightness randomly.
To get best support for hotkeys, update your BIOS to the latest version then add some kernel parameters to the grub config. Run sudo gedit /etc/default/grub
Edit the line with GRUB_CMDLINE_LINUX_DEFAULT and add " acpi_osi=Linux acpi_backlight=vendor". The line should then look like -> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
Save and then run sudo update-grub
Reboot
xbacklight, and xgamma work too.."

I did all the procedure without success. My bios is versio 0901. As the ASUS website discourage to update the bios, do I really need to update it to solve brightness control?

Additional question: when doing grub update, I get the message that GRUB_CMDLINE_LINUX was not found. What should be the correct value? 

Thanx for your reply
Paolo

---

