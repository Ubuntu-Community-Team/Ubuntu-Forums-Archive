---
title: "Touch Screen in Ubuntu 9.04"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by pulsar2121 on 2009-10-01
I have a Fujitsu LifeBook running Ubuntu 9.04 and the touch screen doesn't work. I tried searching for a driver for it, but I couldn't find one. Any ideas?

---

### Post by bernardfrancois on 2009-10-14
You could try installing the 'xserver-xorg-input-evtouch' package in synaptic. After it is installed, you can reboot to see if it works. Alternatively, you can hit Ctrl+Alt+Backspace (make sure you first save all your open files, as it will quit all your programs).

I found some info about touch screens and ubuntu here:
[https://wiki.ubuntu.com/JauntyTouchscreenHandling](https://wiki.ubuntu.com/JauntyTouchscreenHandling)

There I read that the evtouch would be the only touchscreen driver, and that most touch screens are still unsupported. You'll have to be lucky I guess.

If it doesn't work, you could also try downloading Ubuntu 9.10 from ubuntu.com (it's still in beta, but it will be released within a few days).

---

### Post by matthewbpt on 2009-11-25
If you post the output of ```
lspci
``` and ```
lsusb
``` we can see what touchscreen you have and maybe offer some more help. I have mine working after setting up a driver for it, but it's specific to my touchscreen, eGalax.

---

