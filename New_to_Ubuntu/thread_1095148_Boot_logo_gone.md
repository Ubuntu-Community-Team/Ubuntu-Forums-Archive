---
title: "Boot logo gone"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by Snv on 2009-03-13
Hi all!

After I installed nVidia Driver v177, the Ubuntu boot logo is no longer showing during boot. What is shown is the long lines of text... 

How can I get the logo back?

This is the menu.lst file:

> title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		05f1a7b0-1262-4c85-adb3-217b81534fc6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=05f1a7b0-1262-4c85-adb3-217b81534fc6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		05f1a7b0-1262-4c85-adb3-217b81534fc6
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=05f1a7b0-1262-4c85-adb3-217b81534fc6 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		05f1a7b0-1262-4c85-adb3-217b81534fc6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1



Thanks in advance :)

---

### Post by wDok on 2009-03-13
> **Snv said:**
> Hi all!

After I installed nVidia Driver v177, the Ubuntu boot logo is no longer showing during boot. What is shown is the long lines of text... 

How can I get the logo back?

This is the menu.lst file:




Thanks in advance :)

install startup manager from add remove applications or synaptic.
Then in the settings put the ubuntu (default)theme, or download and install one of your choice.

Post back for any trouble.

---

### Post by Snv on 2009-03-13
Thanks a lot! :D:D

Installed it ^, did some changes 

[ Boot options> Display Res : 1024x768, Colour Depth : 24bits. Previously was 640x480, 8bit ]

[ Appearence > Usplash Theme : usplash-theme-ubuntu. Previously was edubuntu-splash (How?? :-s ) ]

And rebooted. Problem Solved :D

Thanks a lot again :D :D

---

### Post by LowSky on 2009-03-13
> **Snv said:**
> Previously was edubuntu-splash (How?? :-s ) ]


You probably installed the edubuntu theme or at least part of it at some time... happens, mine is the ubuntu-studio one right now, as I added the theme and forgot to re-choose my splash screen

---

### Post by Snv on 2009-03-14
No actually I didn't! I mean don't even have any downloaded / other themes.. That's why I wondered how it happened.. Anyways.. 

I have installed some education programs though..

---

