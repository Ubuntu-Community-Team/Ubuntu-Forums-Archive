---
title: "Compiz reverts back to xfwm4 after a short time."
date: 2010-05-30
forum: New to Ubuntu
---

### Post by seanelly on 2010-05-30
When I run compiz it starts and operates normally, but soon reverts back to xfwm4. I've ran compiz in this machine before without a problem. I'm using xubuntu 10.04. This is what the terminal says when run from there. 
```
:~$ compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
i915_program_error: Exceeded max nr indirect texture lookups

Launching fallback window manager

```
Any ideas? Thanks.

---

### Post by seanelly on 2010-05-31
Seems the Blur Windows effect wasn't appreciated. Disabled and all is now fine.

---

