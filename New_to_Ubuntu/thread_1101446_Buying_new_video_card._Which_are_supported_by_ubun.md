---
title: "Buying new video card. Which are supported by ubuntu?"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by shawndh on 2009-03-20
Not looKing for gaming card, just a graphics card that can do 3d. I can only get 800x600 resolution right now with the integrated card. Suggestions?

---

### Post by hardyn on 2009-03-20
what is the integrated card?

then with current state of development nvidia, then ATI; although there is some open source ATI development that is pretty exciting.

if you are not looking for gaming, intel chips are the best supported but would require changing a motherboard as intel does not have a graphics card yet.  in may cases a new motherboard could be cheaper than a videocard anyway.

---

### Post by porchrat on 2009-03-20
> **hardyn said:**
> what is the integrated card?

then with current state of development nvidia, then ATI; although there is some open source ATI development that is pretty exciting.

if you are not looking for gaming, intel chips are the best supported but would require changing a motherboard as intel does not have a graphics card yet.  in may cases a new motherboard could be cheaper than a videocard anyway.

Intel chips are the best supported? When did that happen?

Right now ATI and Nvidia are both fine support wise, I find the ATI catalyst particularly easy to install, download it and set its permissions followed by running it with sudo and you're good to go.

---

### Post by hardyn on 2009-03-20
try running a terminal session with nvidia.

i have never had a issue with Intel, they have always just worked.

---

### Post by izizzle on 2009-03-20
Get an Nvidia GeForce 8600GT. I have it- it's am amazing card. Amazing support and great 3D in games and Compiz :popcorn:

Here is a review: [http://www.legitreviews.com/article/486/3/](http://www.legitreviews.com/article/486/3/)

---

### Post by shawndh on 2009-03-20
> **hardyn said:**
> what is the integrated card?

then with current state of development nvidia, then ATI; although there is some open source ATI development that is pretty exciting.

if you are not looking for gaming, intel chips are the best supported but would require changing a motherboard as intel does not have a graphics card yet.  in may cases a new motherboard could be cheaper than a videocard anyway.

Actually, its not integrated but it did come with the computer. It's nvidia Legacy Vanta series card.  Tried installing drivers from their site last night but they didn't do anything.

---

### Post by hardyn on 2009-03-24
you should have better luck with any of the gforce 5000+ series cards.

---

### Post by Synthros on 2009-03-24
> **izizzle said:**
> Get an Nvidia GeForce 8600GT. I have it- it's am amazing card. Amazing support and great 3D in games and Compiz :popcorn:

Here is a review: [http://www.legitreviews.com/article/486/3/](http://www.legitreviews.com/article/486/3/)

+1.  I'm running Intrepid Ibex on an nVidia 8600GT, and it works flawlessly.

---

### Post by mysticaltopher on 2009-03-24
I've been having problems of the same type....i installed ubuntu 8.10 on a friends comp with a nvidia TNT2 Vanta series graphics card, unfortunately, Nvidia does not have drivers for this card to work with linux 64 or 32 bit systems....I've been trying to find a way to change the default settings to 1024x768 instead of 800x600.  If anyone has any ideas for me to try please help (I've been trying to fix this problem for 3 weeks now) Thanks!


things I've tried that didn't work:

installing the nvidia-gtx-7? drivers

editing xorg.conf in gedit by putting in the new resolutions under "Screen" and "Monitor"

removing the nvidia-gtx-7? drivers and installing nvidia-xconfig

now nvidia-xconfig won't open because their is no driver listed in xorg.conf

Don't mean to hijack your thread just letting you know what didn't work for me and trying to get some fresh ideas....

Thanks!

---

