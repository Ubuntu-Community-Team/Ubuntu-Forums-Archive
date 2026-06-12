---
title: "Video card driver and root error"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Manipular on 2009-01-12
I'm sure that this is a simple fix for any experienced user, which I am not.

My main problem being that I do not know how to run as root in order to get my video driver installed. I run the code of "cd Desktop" as that is where the files have been downloaded to, when I run the command of "sh NVIDIA-Linux-86_64-180.22-pkg2.run" - as stated to be used by Nvidia - it goes through some processes but in the end says "ERROR: nvidia-installer must be run as root"

This has been a nuisance as the resolution of 800x600 on a 15.6 inch screen is quite horrible. This problem is the last major one as far as I'm concerned, as I have wireless and sound working just fine.

Thanks in advanced for all the help.

---

### Post by Michael.Godawski on 2009-01-12
hey,

slip a sudo in front of the command:
```

sudo sh NVIDIA-Linux-86_64-180.22-pkg2.run
```


[LIST]
[*][http://godawski.oxyhost.com/rootsudo.html](http://godawski.oxyhost.com/rootsudo.html)
[/LIST]

---

### Post by Manipular on 2009-01-12
Thanks Michael, that did the trick, only now it's saying that that I'm running an X server and that it needs to be exited. I know I came accross how to do this somewhere...

Update/Edit

After successfully installing the video driver, upon X server reboot a warning comes up saying "Low-graphical something or other" - in which the screen (on a laptop) and video card were still not detected, I believe that all of the /etc/X11/xorg/conf stuff is correct in that "vesa" is no longer selected but "nvidia" has manually replaced it. Also the monitor and/or screen sections have multiple resolutions (this is done with X-server stopped). But still no more resolutions and still the Low-graphics thing... Taking a break from this for a bit. This is being done on a HP G60 with AMD Athalon X2 64 processor(s).

---

