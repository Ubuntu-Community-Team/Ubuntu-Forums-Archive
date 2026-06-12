---
title: "basic mount confusion"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by MichaelBurns on 2010-02-26
Why is it that I must manually create a mount point in my directory tree when I explicitly mount a device, even using /etc/fstab, but when I plug in a usb stick, a previously nonexistent mount point (e.g. /media/disk or /media/[label] if it has a label) is automatically created for it?  Is there an option in the /etc/fstab file that I can set for this?

---

### Post by n0dix on 2010-02-26
if you have specified the device in fstab you are manually mount. If you don't hal do for you.

---

### Post by MichaelBurns on 2010-02-26
Thanks, n0dix.  I'm still confused, though.  How does hal know what to do?  I mean, is there an equivalent of /etc/fstab that hal uses, and how can I access it?

---

### Post by n0dix on 2010-02-26
It's better to read the doc by the people of Arch Linux ;): [http://wiki.archlinux.org/index.php/HAL](http://wiki.archlinux.org/index.php/HAL)

Hal is going to obsolete, replace by Udev.

---

### Post by MichaelBurns on 2010-03-03
> **n0dix said:**
> Hal is going to obsolete, replace by Udev.It seems that hal was obsolete before it even existed, but not because of udev, rather because of sysfs and dbus.

Anyway, thanks for your help.  I marked the thread as solved.

---

