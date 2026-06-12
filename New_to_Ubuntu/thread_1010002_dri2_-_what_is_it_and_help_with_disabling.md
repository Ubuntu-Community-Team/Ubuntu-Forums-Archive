---
title: "dri2 - what is it and help with disabling"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by shmish on 2008-12-13
Hi,

Since when I first install Ubuntu I had problems with using aticonfig.  I would always get an error that said
"Parse error on line 32 of section Module in file xorg.conf
	"Disable" is not a valid keyword in this section."

The section in xorg.conf that it is referring to is
```
Section "Module"
	Load  "glx"
        Disable "dri2"
EndSection
```

I just comment out this line and all seems to work okay.  I'd like to know what dri2 is though, and why xorg.conf seems to default to disabling it (and therefore defaults to the error above).
I'm using Ubuntu 8.10

thanks

---

### Post by gettinoriginal on 2008-12-13
dri2 has to do with direct rendering, and from their website:
The only X.Org video driver using DRI2 right now is the Intel batchbuffer branch for xf86-video-intel.
Which may explain why it is disabled.  But since you have found the solution to making your system work, that is great.  If you want to know more about it, go here:
[http://www.x.org/wiki/DRI2](http://www.x.org/wiki/DRI2)

:p

---

