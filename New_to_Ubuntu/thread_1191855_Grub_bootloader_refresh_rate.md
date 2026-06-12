---
title: "Grub bootloader refresh rate"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-06-19
Hey everyone, I was wondering if there's a way to set the refresh rate on the bootloader screen where you select which OS to boot into. Right now it's set at 85Hz for some reason, and my TV refresh rate shouldn't be set above 60Hz. Everything else runs at 60Hz except when I'm choosing the OS.

I don't think this would change anything, but I could lower the resolution through StartUp-Manager.

edit: I tried ```
sudo gedit /boot/grub/menu.lst
``` to see if I could find the setting, and I didn't see anything containing hertz Hz or 85.

---

### Post by philinux on 2009-06-19
Where/how do you see it set at 85?

---

### Post by Lazy-buntu on 2009-06-19
I'm using my TV as my monitor. At the top of the screen, whenever the resolution changes, it shows the resolution and the refresh rate. It goes from my BIOS (I think is 800x600 60Hz) to grub (1024x768 or 800x600 85Hz) to the ubuntu loading bar screen (800x600 60Hz) to my login screen/desktop (1360x768 60Hz).

---

### Post by philinux on 2009-06-19
What sort of TV is it. LCD Plasma or crt?

---

### Post by Lazy-buntu on 2009-06-19
Sony 32" LCD

---

### Post by philinux on 2009-06-19
Then ignore it.

[http://en.wikipedia.org/wiki/Refresh_rate](http://en.wikipedia.org/wiki/Refresh_rate)

---

### Post by Lazy-buntu on 2009-06-19
So refresh rate doesn't matter in this case? 

I thought I read somewhere else that running a TV at a higher refresh rate than it is suited for will damage the TV.

---

