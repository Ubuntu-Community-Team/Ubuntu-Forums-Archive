---
title: "Problems."
date: 2009-01-25
forum: New to Ubuntu
---

### Post by ChristopherO on 2009-01-25
I'm Trying to get my Geforce 8500 GT to see my two computer screens. Problem is when i edit confg it says I'm not the owner. which i created this account. Its my only one, Every time i get some thing to start working, when i restart it all goes back :(! I been trying to stroll a little bit to find my answers but after a few hours running into to many dead ends.

---

### Post by halitech on 2009-01-25
most config files are owned by root so you will need to open them as root

in a terminal do this
```
gksu gedit /name/of/file
```

---

### Post by shifty_powers on 2009-01-25
> **ChristopherO said:**
> I'm Trying to get my Geforce 8500 GT to see my two computer screens. Problem is when i edit confg it says I'm not the owner. which i created this account. Its my only one, Every time i get some thing to start working, when i restart it all goes back :(! I been trying to stroll a little bit to find my answers but after a few hours running into to many dead ends.

what are you using to edit the config?

---

### Post by Topsider on 2009-01-25
here check this site out: [http://www.yolinux.com/TUTORIALS/LinuxAndDualMonitors.html](http://www.yolinux.com/TUTORIALS/LinuxAndDualMonitors.html)

I haven't tried to run dual-displays, but I have seen that the proprietary NVidia driver comes with a graphical utility that manages such things...

let me know if this helps!

---

### Post by ChristopherO on 2009-01-25
problem is it says i do not have permission to edit this.

---

### Post by halitech on 2009-01-26
if the file is outside your home directory (and it probably is) you need to open it as root (in this case sudo or gksu)

what file are you trying to edit?

---

