---
title: "Ubuntu 10.10 boot hangs. pls help"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by gerti13 on 2011-01-25
Hi.

I am running Ubuntu 10.10 kernel version 2.6.35-24. 
I have cleared the splash (from quiet splash) in the GRUB_CMDLINE_LINUX_DEFAULT = "" at /boot/grub/grub.cfg

The problem I'm having is that I cannot get the GUI to come up anymore. I can log into comand line (Alt+F1) but when trying to go into GUI (ALT+F7) it hangs into:

fsck from util-linux-ng 2.17.2
/dev/sda1: clean xxx/xxx files xxx/xxx blocks

*Starting AppArmor profiles   Skipping profile in /etc/apparmor.....

and it hangs at 

*Setting sensor limits

at that point I have a blinking cursor.

I tried 'sudo gdm start' and I receive : (gdm-binary:2170): WARNING "Failed to acquire org.gnome.DisplayManager"

I've re-installed GNOME and nothing.

I have looked everywhere on the internet with some people saying that they have had this problem but no help.

Any help would be more than appreciated

---

### Post by khelben1979 on 2011-01-26
Have you tried to reconfigure the X server? ```
sudo dpkg-reconfigure xserver-xorg
```

---

