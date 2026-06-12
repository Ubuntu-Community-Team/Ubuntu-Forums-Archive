---
title: "Strange Gnome behavior"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by kane77 on 2009-02-15
Hi, I'm using ubuntu 8.10 and I noticed strange behavior lately, sometimes randomly all of sudden my gnome theme is replaced by different one (this happened 3 times). After restarting X my usual theme is there.

Other, more annoying thing that is happening is that randomly X is restarted.

Can anyone help me to diagnose and solve the problem? What output should I give that could help find out what is happening and why?

---

### Post by RomeReactor on 2009-02-15
Hi. I'm not sure why get changing Gnome themes, but for the X problem, you could check your logs to see if there are any errors or warnings:
```
cat /var/log/Xorg.0.log | grep "(EE)"
```
```
cat /var/log/Xorg.0.log | grep "(WW)"
```

---

### Post by kane77 on 2009-02-16
I only found this:
```
(EE) Unable to open evdev device "/dev/input/event2".
(EE) PreInit returned NULL for "USB-compliant keyboard"
(EE) config/hal: NewInputDeviceRequest failed
(EE) USB-compliant keyboard: Read error: No such device
(EE) USB-compliant keyboard: Read error: No such device
(EE) USB-compliant keyboard: Read error: No such device
(EE) USB-compliant keyboard: Read error: No such device
(EE) USB-compliant keyboard: Read error: No such device
(EE) USB-compliant keyboard: Read error: No such device
(EE) USB-compliant keyboard: Read error: No such device
(EE) USB-compliant keyboard: Read error: No such device
(EE) USB-compliant keyboard: Read error: No such device
(EE) USB-compliant keyboard: Read error: No such device
(EE) USB-compliant keyboard: Read error: No such device

```

and

```
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
```

---

### Post by RomeReactor on 2009-02-16
Try booting into recovery mode from grub and select XFIX; then select 'Resume' and see if there's any difference. If you get to reach your graphical desktop, try changing the theme back to Human.

---

