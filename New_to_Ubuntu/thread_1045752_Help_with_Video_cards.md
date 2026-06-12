---
title: "Help with Video cards?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by tyeo098 on 2009-01-20
I have a Dell e310 with the standard 64mb graphics card hooked up to my LCD monitor, due to the lack of desktop realestate space, I (under windows) installed two (ANCIENT) PCI graphics cards a:
ATI 3D Rage II+ PCI
Matrox Millenium PCI

They both worked great in Windows, installed and everything.
Then I chucked windows because of a virus (and I couldnt compile natively) for Ubuntu.
Now the only monitor that shows any screen is the Middle LCD running on the integrated graphics.

I know I ahve to mess with my xorg.conf, but everytime i do I have to go into recovery mode...

Can anyone help me get my 3 monitor system working again?

---

### Post by blueridgedog on 2009-01-20
Others may have newer information, but a google search revealed this:

[http://www.linuxquestions.org/questions/ubuntu-63/new-to-ubuntu-multiple-monitors-628111/](http://www.linuxquestions.org/questions/ubuntu-63/new-to-ubuntu-multiple-monitors-628111/)

It may get you searching on better key words or give you a hint.

---

### Post by jimmy the saint on 2009-01-20
I can't help with the setup, but I can save you the recovery mode headache (which is a terrible idea anyway)
rather than just open the file, open a terminal and type in
[code]gksudo gedit /etc/X11/xorg.conf[/conf]

This will enable you edit it with root privalges.  Using sudo (or gksudo for gui apps) will grant you temporary root privliges.

MAKE SURE YOU BACKUP YOUR .conf FILE FIRST!!

---

### Post by tyeo098 on 2009-01-20
Argh
I think the problem is that in 8.10 there is no ServerLayout Section in xorg.conf
so im pretty screwed there.
I really dont want to switch distros, I love ubuntu!
All I need to do is install drivers, but I cant get that working argh!

---

### Post by blueridgedog on 2009-01-20
You can add a ServerLayout section, I did on my eee pc.

---

### Post by sowelie on 2009-01-20
If you're going to do multiple monitors, I'd recommend getting graphics cards of the same brand.  I'd recommend NVIDIA, their multiple monitor support is excellent, very simple.

If you'd prefer to keep what you have, you can definitely add everything to xorg.conf you need.  If you google ubuntu multiple monitors, there's a ton of stuff out there, definitely back up your xorg.conf.  The easiest way I find to tweak is to log into ubuntu, hit ctrl + alt + f1 make changes to xorg.conf, then run sudo /etc/init.d/gdm restart.

---

### Post by tyeo098 on 2009-01-21
Every time I add a ServerLayout section X wont start.
So I decided to just shrink the partition and install Win7 on the rest.

Oh look at that Win7 doesnt support my card either!
 ARGHHHHHHHHHHHH

---

### Post by blueridgedog on 2009-01-21
> **tyeo098 said:**
> Every time I add a ServerLayout section X wont start.
So I decided to just shrink the partition and install Win7 on the rest.

Oh look at that Win7 doesnt support my card either!
 ARGHHHHHHHHHHHH

You need an EndSection...if it won't start you can also use the debug option

---

### Post by tyeo098 on 2009-01-21
I did have an EndSection, I made sure that everything was perfect.
Now theres a new hiccup.
My little ATI 3d Rage II+ has died on me, give me an Error 10 in Xp.

My Matrox is still alive, god know for how much longer. But without my 3 mon setup, theres goes all my college nerd cred...
I think Im going to build a new computer specifically for Ubuntu when I go off to college.

But for now Ive given up on ubuntu on my desktop, runs of my lappy perfectly, but with 2 empty black monitors sitting there, I just cant deem it usable for my primary OS.

Thanks to all you guys that helped me, Ill be back when I have problems with my lappy.

Laterz
-Tyeo

---

