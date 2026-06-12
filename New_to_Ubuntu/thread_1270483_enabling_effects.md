---
title: "enabling effects?"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-09-19
i am able to get to the effects to give me wobbling windows ect, i check it... apply it.. but nothing. sorry brand new to kde i have the proper driver for my card  is there something else i need to do to get my wobbly windows and desk cube working other than system settings->desktop->desktop effects->all effects (tab)-. wobbly windows '"check" ->apply... what am i missing here? 

i do have kde installed along side of gnome on the same partition i switch between the 2  at my log in, however i do not have this problem with compiz in gnome. any ideas?

---

### Post by ankspo71 on 2009-09-19
Hi,

I upgraded to a new Ubuntu version last night (from 9.04 to 9.10 alpha6), so I had to reconfigure my 3D effects settings. I discovered that wobbly windows does not work if "GLib" is not enabled in "CompizConfig Settings Manager".

You do have CompizConfig Settings Manager installed, don't you? I am assuming you do because you know about the desktop cube.

Hope this helps.
James

---

### Post by ankspo71 on 2009-09-19
Hmm, that's odd, now I can disable GLib and the wobbly windows still works. I did have to enable GLib to get the wobbly windows to work the first time though.

James

---

### Post by tarantula78 on 2009-09-19
if you go to the appearance setting ( i dont know what its called in KDE sorry) does it give you the option to set "Custom" Effects?

---

### Post by R3fr4cti0n on 2009-09-19
how do i enable these effects i just did a fresh install of kde 4, i know how to get to the effects(system settings->desktop->desk effects->All effects"tab") so i UNCHECKED everything and pressed the apply button and nothing the desktop still works the same as it did. i also CHECKED a bunch (wobbly windows, fall apart ect) and none of it is working on my windows so how do i enable this what am i doing wrong?

---

### Post by Cresho on 2009-09-19
you need a video hardware accelerated.  go into .......hmmmmmm  look for hardware drivers in your kde menu.  install that and reboot and you should now see your hardware accelerated desktop.

---

### Post by Soley on 2009-09-19
An easy way to manage your compiz effects is to use ccsm. In a terminal type ```
sudo apt-get install compizconfig-settings-manager
```

Once it install, hit Alt+F2 and type "ccsm" (without the quotes) & you'll have full access to your effects for compiz. Also be sure you have accelerated graphics (video drivers) installed.

---

### Post by mohi on 2009-09-20
I also had this issue and I found that the nVidia driver is deactivated, I just "Activate" it from hardware drivers and everything is fine now. so you might also check this. :)

---

### Post by overdrank on 2009-09-20
Please do not create multiple threads on the same issue. Threads merged.

---

### Post by R3fr4cti0n on 2009-09-20
my vid drivers are all on and i dont want to use Compiz i would like to just enable kde.... so is there a step that i am missing?

---

### Post by Cresho on 2009-09-20
i think you are confused.

if you have video hardware accelerator, then your done.

kwin is for kde

compiz fusion is for gnome.

What i mean is kde has it's own effects engine and no need to use compiz.  Even if you enable the full effect of kde kwin, you will never see it as awesome as compiz.  Compiz is far more mature.

---

