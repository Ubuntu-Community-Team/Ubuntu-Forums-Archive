---
title: "how do i adjust screen brightness w/ 9.10 ubuntu?"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-04-05
how can i adjust the screen brightness?  I've tried using the settings by the battery icon and through preferences>> power management.  neither works!!  It used to be on the32 bit feisty that you could change screen brightness from the function keys but maybe that's because my old lappy was a Toshiba?  Any feedback?

---

### Post by niteshifter on 2010-04-05
Hi,

If you're using GNOME (stock Ubuntu) try adding the the Panel Brightness applet to a panel.

---

### Post by duanedesign on 2010-04-05
You might take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1173732"). it might provide some insight into your issue.

best of luck

---

### Post by nauziem on 2010-04-05
Guided by this site: [http://martinml.com/en/linux-on-asus-eeepc-1005p/](http://martinml.com/en/linux-on-asus-eeepc-1005p/)

I fixed the issue with the screen brightness controls on my asus in what appears to be the same way. As described therein, the brightness controls used to be erratic... jumping to apparently random brightness at the press of the + or - function keys. Following the edit in code, apparently perfect function was restored.

---

### Post by bradmayne04 on 2010-04-05
yeah I don't think that's for 9.10 cuz there was no file in the menu.lst

> **duanedesign said:**
> You might take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1173732"). it might provide some insight into your issue.

best of luck

ok so you DON'T do the changes from the /boot/grub/menu.lst !!
you do it from:     	 	 	 	 	 	  sudo gedit /etc/default/grub
Add acpi_osi=Linux on the end of the line GRUB_CMDLINE_LINUX_DEFAULT=&#8220;quiet splash&#8221; GRUB_CMDLINE_LINUX_DEFAULT=&#8220;quiet splash acpi_osi=Linux&#8221;
sudo update-grub
now i don't have a quiet splash so i didn't have to pay attention to that but make sure you keep the whole line in parenthis as I have shown thanks for tryin to help though guys and gals!!

---

