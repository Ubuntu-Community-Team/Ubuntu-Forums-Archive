---
title: "working with a stylus"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by ave2 on 2009-03-11
I have a genius g-pen 560, plugged in, if I place my pen on any point on the tablet, the mouse cursor jumps to the corresponding position on the screen as it should, but pen movements seem to be too sensitive, so if I move the pen 1cm, the cursor shoots to the other end of the screen.
I didnt install any drivers, because the pen only comes with mac and pc drivers, I just plugged it in and it worked, but now I dont know how to modify the options, or even how to view the drivers

---

### Post by Favux on 2009-03-11
Hi ave2,

Maybe this link will help you.

[https://help.ubuntu.com/community/TabletSetupWizardpen]("https://help.ubuntu.com/community/TabletSetupWizardpen")

---

### Post by ave2 on 2009-03-11
Iv been messing with that tutorial, but I dont actually have a clue what is going on-so I get errors on every step

there must be some sort of driver already installed, as most of the functionality is working- is there anyway to open up a dialogue box or something and calibrate the existing driver

---

### Post by Favux on 2009-03-11
Hi ave2,

What version of Ubuntu are you using?  Is the tablet usb?  In other words you plug it into a usb port?

Assuming it is usb to figure out what driver is running the tablet we can try a couple commands.  Both will give long outputs that you'll have to go through to find the driver name.

In a terminal type:
```
lsusb -v
```
or from:  [https://help.ubuntu.com/community/TabletSetup]("https://help.ubuntu.com/community/TabletSetup")  This link will also tell you what names to look for.
```
cat /sys/bus/usb/devices/*/product
```
And here is another Genius tablet setup link:  [http://ubuntuforums.org/showthread.php?t=228991&highlight=Genius+pen]("http://ubuntuforums.org/showthread.php?t=228991&highlight=Genius+pen")

---

