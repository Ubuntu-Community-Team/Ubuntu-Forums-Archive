---
title: "Change resolution from command line?"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by blackstripes on 2009-03-13
I am running Ubuntu 8.10 from VPC 2007 on my work machine.  Unfortunately I selected a resolution that is not displaying correctly and I cannot see anything to change it back.  Is there a simply command that I can enter into the virtual console that will allow me switch back to my desired 1280x1024 resolution?

---

### Post by taurus on 2009-03-13
You can reconfigure the X server with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by sisco311 on 2009-03-13
or you can try to press Alt+F2, type:
```
xrandr -s 1280x1024
```and hit Enter.

---

### Post by blackstripes on 2009-03-13
> **sisco311 said:**
> or you can try to press Alt+F2, type:
```
xrandr -s 1280x1024
```and hit Enter.

Just to clarify, this does not need to be entered into terminal?

---

### Post by blackstripes on 2009-03-13
> **sisco311 said:**
> or you can try to press Alt+F2, type:
```
xrandr -s 1280x1024
```and hit Enter.


Thanks a lot for this help! It actually didn't work with 
xrandr -s 1280x1024, but xrandr -s vga=794 did the trick.  Not sure why, but I'm fixed. :)

---

