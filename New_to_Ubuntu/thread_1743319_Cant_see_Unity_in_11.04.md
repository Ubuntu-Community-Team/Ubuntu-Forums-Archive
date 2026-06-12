---
title: "Cant see Unity in 11.04"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by ravi_buz on 2011-04-29
I downloaded the latest version of 11.04 and tried it as live user because i want to make sure it works with my Pc. When i booted into it, i could not see ubuntu unity rather only Gnome. Can anyone tell me how to fix this.

---

### Post by jerome1232 on 2011-04-29
What video card do you have? You may need to install drivers for it, which can't be done on a live cd, thus no unity for you on a live cd if that is the case.

---

### Post by ravi_buz on 2011-04-29
I have an old GeForce FX 5200 card (up the problematic series) hope it will work once i install it :o

---

### Post by Frogs Hair on 2011-04-29
I had to install proprietary drivers for my Nvidia card to boot into Unity .

---

### Post by ravi_buz on 2011-04-29
> **Frogs Hair said:**
> I had to install proprietary drivers for my Nvidia card to boot into Unity .
What card are u using?

---

### Post by kaldor on 2011-04-29
Once you install, use the Additional Drivers utility and install the proprietary drivers. 

Quick method is to just run it from terminal with the "jockey-gtk" command.

---

### Post by ravi_buz on 2011-04-30
Just installed 11.04 and installed the additional driver. But when i restarted ubuntu i cant see anything as unity is not supported and so i loggged into Gnome. Can any one tell me how to make unity work on my driver

---

### Post by gstla on 2011-04-30
If unity isn't supported after you installed the proprietary driver then it isn't a driver issue, ravi_buz, it's probably that your hardware can't support it. I don't think anyone can modify the drivers either, since they're closed-source.

---

### Post by ravi_buz on 2011-04-30
Finally have my unity working on my OLD Gefore FX 5200 card :) Really impressed that my card is supported by Unity

Solution: Ubuntu by default installs the 173 driver for the card which works perfectly on Ubuntu Classic mode. So if you want to see unity remove it and restart ubuntu and you will see another experimental driver in the list ( You wont see this if you have 173 installed ) install it reboot and vola, You have UNITY!!!

---

### Post by ZebaSz on 2011-05-01
Um...I tried that and it almost rendered my install useless. I couldn't even reboot after uninstalling the driver, I had to use recovery mode, and ended up reinstalling the proprietary driver. GeForce FX 5200.
Maybe I did something wrong. Do I need both experimental and proprietary? Or maybe I can install experimental via synaptic/apt without removing the other one? I'd really love to use Unity+Compiz, instead of 2D.

---

### Post by ravi_buz on 2011-05-01
> **ZebaSz said:**
> Um...I tried that and it almost rendered my install useless. I couldn't even reboot after uninstalling the driver, I had to use recovery mode, and ended up reinstalling the proprietary driver. GeForce FX 5200.
Maybe I did something wrong. Do I need both experimental and proprietary? Or maybe I can install experimental via synaptic/apt without removing the other one? I'd really love to use Unity+Compiz, instead of 2D.

I used only the experimental drive only. May be remove the 173 driver reboot and choose the recovery option with low graphic (so that you can see your system) install the experimental driver reboot. Thats all

---

### Post by ZebaSz on 2011-05-02
> **ravi_buz said:**
> I used only the experimental drive only. May be remove the 173 driver reboot and choose the recovery option with low graphic (so that you can see your system) install the experimental driver reboot. Thats all
That's what I did, didn't work for me.

---

### Post by prosik on 2011-05-03
I have the experimental drive but now I can't see icons in launcher.

---

### Post by LeoEvs on 2011-05-03
worked perfectly for me. 

the experimental driver (for nvidia-173) is
[B]libgl1-mesa-dri-experimental
A free implementation of the OpenGL API -- Extra DRI modules
[/B]and can be downloaded directly by synaptic.

only the icons do not appear on the side, any idea how to fix this?
thank you.

---

### Post by ZebaSz on 2011-05-04
Ok, I found the answer. Apparently, they blacklisted the video card (GeForce FX 5200). Maybe because of the "no icons in launcher" bug.
To check for Unity support, run in a terminal:
```
/usr/lib/nux/unity_support_test -p
```
If you're using the proprietary drivers, you should see it's blacklisted, and therefore lacks Unity support. To bypass the check, add this:
```
UNITY_FORCE_START=1
```
to your /etc/environment, then reboot and voila: Unity with proprietary drivers. If you re-run the support test, it will output:
```
Warning: UNITY_FORCE_START enabled, no check for unity or compiz support.
```
Just a note: jockey still informs the drivers are "enabled but not in use". So I'm a little confused there.

Still, same as you, no visible icons in launcher.

---

