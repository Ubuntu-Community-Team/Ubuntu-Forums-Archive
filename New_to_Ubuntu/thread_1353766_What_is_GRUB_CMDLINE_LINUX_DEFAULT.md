---
title: "What is GRUB_CMDLINE_LINUX_DEFAULT"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by johnwieja on 2009-12-13
I am trying to get my gma500 video card on my sony vaio p running correctly. Following the instructions here:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

But one last step I don't understand:
"
If you have a Vaio-P or if you are experiencing extremely slow performance (less than 14 fps running “/usr/bin/xscreensaver/glblur -fps -window”) add “mem=2000mb” to /etc/default/grub, at the end of GRUB_CMDLINE_LINUX_DEFAULT"

Can someone help me understand this? Thanks

---

### Post by plucky on 2009-12-13
> **johnwieja said:**
> I am trying to get my gma500 video card on my sony vaio p running correctly. Following the instructions here:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

But one last step I don't understand:
"
If you have a Vaio-P or if you are experiencing extremely slow performance (less than 14 fps running “/usr/bin/xscreensaver/glblur -fps -window”) add “mem=2000mb” to /etc/default/grub, at the end of GRUB_CMDLINE_LINUX_DEFAULT"

Can someone help me understand this? Thanks

Open a terminal and ```
gksudo gedit /etc/default/grub
``` will allow you to edit that file.

This is what the file contains ```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="05"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[color=red]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/color]
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

Make the line in red to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash mem=2000mb"
```

Good Luck

---

### Post by sisco311 on 2009-12-13
After editing the file you have to run:
```
sudo update-grub
```


[uhelp]community/Grub2[/uhelp]
[thread=1302743]Grub 2 - 5 Common Tasks[/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]
[thread=1195275]The Grub 2 Guide[/thread]

---

### Post by johnwieja on 2009-12-13
Thanks a lot to sisco and plucky.... fixed it in 1 minute. frame rate much improved now!! 

This forum is the best!

---

### Post by sisco311 on 2009-12-13
> **johnwieja said:**
> Thanks a lot to sisco and plucky.... fixed it in 1 minute. frame rate much improved now!! 

This forum is the best!

Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

