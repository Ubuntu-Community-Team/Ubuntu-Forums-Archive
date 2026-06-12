---
title: "new update 10.04 lost nvidia resolution"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by wapfu on 2010-06-29
My latest updates included an nvidia package.
On reboot the resolution has dramatically changed in that all I get is a very very large top left corner.
In failsafe graphics works.
The nvidia set up said it could not be found.
Tried sudo nvidia-config - no response
Tried sudo startx to no avail.
Any help appreciated to restore display configuration.
Kind Regards
bill

---

### Post by -humanaut- on 2010-06-29
Did it change the Kernel version on you (type uname -r) in a terminal last kernel update completely killed X for me so I had to and i'm stick with Kernel 2.6.32-22-generic try adjust grub if it did you can do it from a tty console(ctrl+alt+f1 at startup) just do this from it (((I'm also using a Nvidia card with the 256.35 driver)))
login
sudo nano /etc/default/grub
Grub Default=2
save
sudo update-grub
sudo shutdown -r now 
see if that works for you.

heres a reference for you my grub looks like this

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

**GRUB_DEFAULT=2**
GRUB_HIDDEN_TIMEOUT=1
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

