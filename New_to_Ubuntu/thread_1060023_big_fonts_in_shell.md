---
title: "big fonts in shell"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by broj9999 on 2009-02-04
whenever I open shell using ctrl alt f2 - f6 the text is huge
I tried adding a subsection to xorg.conf but does not effect shells?

---

### Post by cerealtx on 2009-02-04
Edit->Profile Prefrences

---

### Post by mcduck on 2009-02-04
It's not a question of big fonts, but low resolution. ;)

To fit more stuff on the screen you need to enable frame buffer to get higher resolution in TTYs.

[https://wiki.ubuntu.com/FrameBuffer]("https://wiki.ubuntu.com/FrameBuffer")

Xorg.conf doesn't affect this, as it's configuration file for X, and TTYs don't run inside X. Frame buffer resolution is configured as kernel parameter in Grub's configuration file, /boot/grub/menu.lst. The most common setting would be adding "vga=791" to the end of kernel options, this would give you 1024x768 resolution with 16-bit colors (during boot and in VTTs, X still uses it's own resolution settings).

---

### Post by broj9999 on 2009-02-04
tried to add 

defoptions=vga=791 resume=/dev/hda5
but says I dont have permissions
I am logged in as the user I created when I loaded it?

---

### Post by mcduck on 2009-02-04
you need to use sudo to access system files, you are not their owner.

In this case open a terminal and run "gksudo gedit /boot/grub/menu.lst" to open the file for editing with root privileges.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by broj9999 on 2009-02-04
ok... I got to change the frame buffer...but I cant find a setting it likes.. I went all the way down to 480x640 and boot loader does not like many of may options and the resolution is set to 1024x768 in the gui?

---

### Post by Tomatz on 2009-02-04
Do you not have an "auto adjust" button on your monitor?

---

### Post by broj9999 on 2009-02-04
No its an older monitor no a flat screen or lcd

---

### Post by mcduck on 2009-02-04
> **broj9999 said:**
> ok... I got to change the frame buffer...but I cant find a setting it likes.. I went all the way down to 480x640 and boot loader does not like many of may options and the resolution is set to 1024x768 in the gui?

Set it to "vga=ask" and you should get a list of available modes on next boot. Try one and if it works then change the menu.lst to use that mode.

---

### Post by broj9999 on 2009-02-04
that happened once when I entered an invalid frame buffer code
"791" so I selected one of the vga modes, but they are not completely spelled out they all look to be 800x600 but colors amounts are not shown in the list? anyway to find out so I can set the fb?

---

### Post by mcduck on 2009-02-05
> **broj9999 said:**
> that happened once when I entered an invalid frame buffer code
"791" so I selected one of the vga modes, but they are not completely spelled out they all look to be 800x600 but colors amounts are not shown in the list? anyway to find out so I can set the fb?

Just use one of the modes it gives for you. They should all work on your system (that's why it lists them for you!).

I suppose the text-only VGA modes use 256 colors (8 bits) as defined by VGA standard. I've never tried those as there are plenty of better modes listed on all my systems. Anyway, if you want to know for sure just try one.

---

