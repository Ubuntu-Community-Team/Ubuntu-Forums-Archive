---
title: "Force Safe Graphics Mode"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Newbie503 on 2010-05-05
I have a new notebook with a Intel graphics card. I can boot a live CD into Safe Graphics Mode and it works fine. I installed off the alternate CD and it just boots to a black screen. I have tried dropping to a terminal via ctrl+alt+F1 but it just stayed at a black screen. I think I just need to enable proprietary drivers to get it working permanently but I need a way to enable safe graphics mode in the actual installation like on the live CD. Thanks!

---

### Post by -humanaut- on 2010-05-05
> **Newbie503 said:**
> I have a new notebook with a Intel graphics card. I can boot a live CD into Safe Graphics Mode and it works fine. I installed off the alternate CD and it just boots to a black screen. I have tried dropping to a terminal via ctrl+alt+F1 but it just stayed at a black screen. I think I just need to enable proprietary drivers to get it working permanently but I need a way to enable safe graphics mode in the actual installation like on the live CD. Thanks!

when your booting into ubuntu hit ctrl+alt+f1 and see if you can get a tty console then set NOMODESET and than reboot with sudo shutdown -r now and that should boot it without probing for a video card.

---

### Post by Newbie503 on 2010-05-05
Ctrl+Alt+F1 just keeps the screen blank. I think I am looking for a GRUB boot option that will force safe graphics mode like on the live CD.

---

### Post by Newbie503 on 2010-05-06
So I added nomodeset to the kernel parameters in GRUB and it at least shows me the splash screen. Then boom, back to black. I tried to see the kernel parameters that the live CD uses when you select safe graphics mode, but it just says boot=casper. Can someone please tell me the parameters that actually make "safe graphics mode" Thanks!

---

### Post by markofealing on 2010-05-07
Boot off an Ubuntu live CD.

Navigate to your hard disk's /etc/X11/ directory

In terminal enter sudo nano xorg.conf to edit the config file and change your Device section to look like:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"

Save the file, reboot without the live CD.

Ubuntu will complain and allow you to reconfigure your graphics card settings.

Alternatively copy xorg.conf-failsafe and make it xorg.conf and reboot.

---

