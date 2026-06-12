---
title: "need to resize the screen"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by swish_sam on 2008-12-16
ive had Ubuntu on my laptop for a couple of months and i like it very much, so i decided to install it on my home PC.

my PC is not connected to a conventional monitor, its connected to my 32" HD TV via DVI to HDMI cable.

the problem is that about 1/4 of an inch off each side is off screen. i had the same issue with vista but used the nVidia drivers to shrink the desplay down a bit.

my graphics card is an XFX 8800GT

in Ubuntu i have the resolution set to 1280 X 720 and the display is detected as UNKNOWN

any help would be fantastic but do bare in mind that i am a bit of a Linux noob

thanks

---

### Post by Shhnap on 2008-12-17
Well, i don't know how to solve your problem but if you want to edit nvidia settings then a good place to start would be to:

Applications -> Accessories -> Terminal

In the terminal:

sudo apt-get install nvidia-settings

Close the terminal once that is done.

Then: System -> Administration -> nVidia X Server Settings

Hope that gets you on the right path...

---

