---
title: "no USB detected"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by langyaw on 2009-07-27
my Ubuntu 9.04 (dual booting with Windows Vista Home Premium on an HP Pavilion dv6000 laptop) cannot recognize my USB when I put it in the port. how do I get it working?

---

### Post by Cheesemill on 2009-07-27
What sort of USB device are you trying to use?

---

### Post by hyperAura on 2009-07-27
can u not see the usb device at all?? if u can see it but not open it, i think that u have to mount it (load)..

---

### Post by LookTJ on 2009-07-27
Could you tell us what device it is?

Plug in your usb device

and please give us the follwing output
```
lsusb
```

:KS

---

### Post by langyaw on 2009-07-28
> **LookTJ said:**
> Could you tell us what device it is?

Plug in your usb device

and please give us the follwing output
```
lsusb
```

:KS

[FONT="Arial"][COLOR="Navy"]thanks, Guys. I guess the problem solved itself. 
I was really waiting for that sound when you plug in the USB flash stick in the USB port. because I didn't hear it, I thought my USB drive was out, too.
but this time, after inserting the memory stick, a window came up that showed me my USB stick's content. cool. :)
so to "safely remove" it, the command is "unmount". 
thanks again![/COLOR][/FONT]

---

### Post by halitech on 2009-07-28
yes, you would use
```
umount /dev/sdX
```to unmount, or simply right click and eject.

---

