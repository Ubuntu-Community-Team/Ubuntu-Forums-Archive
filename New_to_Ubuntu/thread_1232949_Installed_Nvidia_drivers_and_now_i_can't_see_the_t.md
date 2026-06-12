---
title: "Installed Nvidia drivers and now i can't see the top or the bottom of the desktop"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by SmeagolL on 2009-08-06
Hello

I got a nVidia GeForce 9300 gfx card on a Panasonic TX-P42X10B tv, connected through HDMI. At first it was pretty alright except for the screen not being 100% and then i installed the nvidia server x drivers through the hardware drivers interface and then i got the resolution/features i was afterbut i don't get the full desktop. Any ideas what i can do?

---

### Post by sasho_zl on 2009-08-06
I had the same problem with the nvidia-settings manager. When it edited the xorg.conf file and after reboot all the panels and window borders were gone. I think it is some kind of a bug in the manager. You can fix it by going in single user mode (sudo init 1) and then repairing your xorg with default settings.

---

### Post by SmeagolL on 2009-08-06
They're not gone just off screen, but ill check that xorg you're mentioning. Thanks!

---

### Post by SmeagolL on 2009-08-06
Checked out the xorg file but i wouldn't know what to look for... I know that when i try to save the conf in the manager i get an error that it can't save over the original file, so im stuck in a lower resolution but i got the same problem in all resolutions so

---

### Post by sasho_zl on 2009-08-06
To bypass the error  issue with the saving of the configuration you can start a root nvidia manager by typing **sudo nvidia-settings** in the terminal. You can turn xorg.conf to its default settings by selecting the xorg menu in single user mode as I wrote before.

---

### Post by SmeagolL on 2009-08-06
"by selecting the xorg menu in single user mode"

I don't understand what that means, but i clicked Reset in the nvidia settings, saved and rebooted and it didn't work.

---

### Post by SmeagolL on 2009-08-06
If you mean there should be a xorg option in the menu that comes up, i don't have that option...

---

### Post by SmeagolL on 2009-08-06
it was overscan that was the problem. Problem solved once i figured out that word :) Just a setting on the tv (deep into the menu system)

---

