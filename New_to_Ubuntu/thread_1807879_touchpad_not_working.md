---
title: "touchpad not working"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by pranayama on 2011-07-19
I have an HP Pavilion laptop with a Synaptics PS/2 Port Touchpad.

It worked OK with 10.04 for the last year until a few hours ago. I don't know what happened, I was playing an avi file with VLC which I played yesterday without any problem.

xinput list and cat /proc/bus/input/devices show no touchpad, there is only "Macintosh mouse emulation".

I tried the gconftool-2 command in the Ubuntu community documentation but that doesn't work, I tried rebooting in an older kernel but the problem is the same.

Please help or I'll have to reinstall.

---

### Post by jtarin on 2011-07-19
In a terminal issue the command ```
lsmod
``` and then look to see if you have a module ```
psmouse
``` loaded.

---

### Post by pranayama on 2011-07-19
psmouse is listed.

I pressed the touchpad enable/disable button _while_ booting, and now everything works again.

I don't know how I caused the problem and I don't know how I fixed it, so I will not mark the thread as solved.

---

### Post by jtarin on 2011-07-19
> **pranayama said:**
> psmouse is listed.

I pressed the touchpad enable/disable button _while_ booting, and now everything works again.

I don't know how I caused the problem and I don't know how I fixed it, so I will not mark the thread as solved.You fixed it by pressing the enable/disable button _while_ booting, which enabled it. You must have accidentally disabled it.Mark it as solved.

---

