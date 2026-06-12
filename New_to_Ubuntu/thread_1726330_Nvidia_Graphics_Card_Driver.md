---
title: "Nvidia Graphics Card Driver"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by dmullick95 on 2011-04-11
Hey,

i am facing a bit of a problem with my Nvidia graphics card driver for ubuntu 10.10.. 
Whenever i enable it from System/Administration/Additional Drivers , my default ubuntu splash screen changes to something extremely pathetic with a res of mayb 640x480 instead of the original 1366x768
Now, i require this driver for my Compiz settings and Cairo GLX-Dock

Is there some way to restore my original splash screen as well as keep my driver enabled..

---

### Post by dmullick95 on 2011-04-11
oh sorry forgot to mention iv got a 
Geforce GT 220

---

### Post by 3rdalbum on 2011-04-11
No, it's a limitation in NVIDIA's driver. Sorry!

---

### Post by wolfen69 on 2011-04-11
That happens because the splash screen is made to work with the default nouveau drivers, and not nvidia's. I've never heard of a fix for it, but who knows. Linux distros historically have never put a lot of effort into splash screens.

---

### Post by gandaran on 2011-04-11
> **dmullick95 said:**
> Hey,

i am facing a bit of a problem with my Nvidia graphics card driver for ubuntu 10.10.. 
Whenever i enable it from System/Administration/Additional Drivers , my default ubuntu splash screen changes to something extremely pathetic with a res of mayb 640x480 instead of the original 1366x768
Now, i require this driver for my Compiz settings and Cairo GLX-Dock

Is there some way to restore my original splash screen as well as keep my driver enabled..
install startupmanager from software center or [Grub Customizer]("http://ubuntu-tweak.com/source/danielrichter2007-grub-customizer/") , I believe you can change the resolution to what it was before.

---

### Post by mikewhatever on 2011-04-11
I've used [this method]("http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html"). Worked quite well.

---

