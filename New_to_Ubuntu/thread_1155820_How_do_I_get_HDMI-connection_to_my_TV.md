---
title: "How do I get HDMI-connection to my TV?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by Lhademmor on 2009-05-11
Hi all. I've installed jaunty onto my PC as dual-boot with XP. However, I really want to get rid of XP, but there are two things holding me back. One of them is this:

On XP I have configured my graphics card (a nVidia 9600 GT) to 'clone' the image to my 40" TV screen using a HDMI cable connected between the graphics card and the TV. That means that if I e.g. have a movie on XP I can open it and then watch it on my TV in full screen.

However, I have absolutely no idea how to achieve this in jaunty. Can anyone help?

Thanks.

---

### Post by adam_kimber on 2009-05-12
Unfortunately this sort of thing is not yet "really easy" in Linux but Ubuntu is making strides. Depending on how confident you are feeling try the following:

1) Goto Restricted Drivers and enable the nvidia corporation driver. 180 seems to work fine for most so try that one. 

2) Go to nvidia settings, I think you can get that in the system menu. If it is not installed, we can solve that. 

3) Connect TV.

4) Click detect displays. 

5) Setup TV as-you-like.

6) Click save to xorg.conf (might not be present in Jaunty as there is a newer version of X in use.

Any problems just shout. :)

---

### Post by LowSky on 2009-05-12
I use a VGA connection but HDMI should work as well.

open a terminal

type ```
gksu nvidia-settings
``` 
go to the second option on the left, it will allow you to configure the screens.

---

### Post by Lhademmor on 2009-05-30
Thank you both, it seems to actually work (something which it doesn't do in Windows 7!)

---

