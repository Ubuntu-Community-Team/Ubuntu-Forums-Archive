---
title: "Oneric Live USB won't boot."
date: 2011-08-16
forum: New to Ubuntu
---

### Post by kyletstrand on 2011-08-16
I decided to make a LiveUSB for Oneric's version of Ubuntu studio to see how it is coming.

I used 

```
gksudo usb-creator-gtk
```

to use the easy graphical interface.  I created the usb using the  correct .iso file and it said everything was created successfully and I  received a message stating that this drive was now bootable when  inserted or something along those lines.

I then used gparted to create a second partition on the usb drive and that was done successfully as well.

I restarted and no luck with booting. It just booted into my normal OS.

This is my first attempt at creating a LiveUSB environment.

Do I need to change something in my Bios, or am I missing something completely obvious?

Thanks!

---

### Post by kyletstrand on 2011-08-16
Ok, got it.  It was in my Bios.  It wasn't seeing it as a removable device, but a separate drive.

---

