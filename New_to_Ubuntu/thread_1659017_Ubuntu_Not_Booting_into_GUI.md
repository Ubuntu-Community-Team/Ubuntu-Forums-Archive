---
title: "Ubuntu Not Booting into GUI?"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by pr3smac on 2011-01-03
I just got a Dell Inspiron N4010 the other day and loaded Ubuntu 10.10 desktop edition onto it. But for some reason or another it will not boot into the GUI, I have installed and reinstalled Ubuntu and Ubuntu Netbook times over, but still with no luck. The LiveCD is perfectly fine, but once I reboot its all in text-mode. I tried doing 'startx' but it just made the screen go blank. I don't know how, but at one point i was holding down the power button to turn it off after doing 'startx' and a graphic warning popped up saying that it was running in Low Graphics Mode. But then it just shutdown cause i was holding down the power button. Does anybody know how i could get the GUI to load on boot? Thanks for all your help!

---

### Post by sparker1 on 2011-01-04
Try add "nomodeset" in /boot/grub/grub.conf
 
[http://ubuntuforums.org/showthread.php?t=1305010](http://ubuntuforums.org/showthread.php?t=1305010)

---

### Post by cheapie on 2011-01-04
Instead of typing startx, type "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup". Then run startx. It should show the low graphics mode prompt, and let you reconfigure the graphics.

---

### Post by pr3smac on 2011-01-04
I did some more searching on it, and it looks like this pecticular computer uses an i915 chipset, and apprently the linux kernel was built wrong for it, so it looks like i gotta get a different computer. Thanks for all your help! Love the forum!

---

### Post by Rubi1200 on 2011-01-04
If you mean you have an Intel chipset, then what you say is not necessarily true.

I have tested with an Intel chipset on both 10.04 and 10.10 and I can tell you there are workarounds.

See here for more:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

Let us know which particular card you have so we can try and help you resolve this.

---

### Post by HermanAB on 2011-01-04
Howdy,

The problem is the video driver.

The installation system uses the generic VESA driver that works on anything.  Therefore, when all else fails, change the file xorg.conf to use the vesa driver, then at least you will have basic video capability.

I've been running my Toshiba laptop for over a year on the Vesa driver since the Nvidia drivers are total cruft and causes the machine to lock up.  The only practical downside is that you cannot do fancy graphics or play games on Vesa, but it is good enough for business use.

---

