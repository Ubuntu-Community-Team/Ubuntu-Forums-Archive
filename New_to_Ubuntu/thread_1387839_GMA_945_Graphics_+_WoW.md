---
title: "GMA 945 Graphics + WoW"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by JiuJitsu500 on 2010-01-22
Hey! Here's one I'm sure has been discussed...

Roommate is a huge WoW fan and plays ALL the time and finally got ubuntu 9.10 installed on his external in a 60GB partition he made for it... after he gave me the disc back he's been trying to get WoW to work... which it does to a point, but Graphics are no bueno, and he can't even enable desktop 3D effects, and needless to say, no compiz either.

It's an old Dell Inspiron E1405, with a GMA 945 or 950 graphics card...

So I told him to re-install the driver (sudo apt-get install --reinstall xserver-xorg-driver-intel or something like that, read on another thread) after we tried a normal install and saying it has the latest driver... and the re-install failed at enabling 3D stuff and WoW obviously still looked like a Nintendo trying to run Halo 3... No proprietary drivers either except for wireless...

Anyone got any tips on perhaps a different driver? Even a roll-back maybe?

---

### Post by cascade9 on 2010-01-22
Inspiron E1405- intel 945 chipset, GMA 950 video. 

[http://en.wikipedia.org/wiki/Dell_Inspiron_E1405](http://en.wikipedia.org/wiki/Dell_Inspiron_E1405)

As far as I know, the GMA950 doesnt support hardware t&l (transform and lighting). You really want that for WoW-

> The following Intel® integrated graphics controllers support hardware Transform and Lighting (T&L):
 
[LIST]
[*]The integrated graphics controller of the Intel® G35, G41, G43, G45, G965, GL40, GL960, GM45, GM965, and GS45 Express Chipsets
[*]Intel® HD Graphics
[/LIST]
  All other Intel® graphics products do not have hardware support for T&L. In most games, transform and lighting calculations can be performed on the processor with acceptable performance. A small number of games that specifically check for hardware T&L support may fail to run.


[http://www.intel.com/support/graphics/sb/CS-011910.htm](http://www.intel.com/support/graphics/sb/CS-011910.htm)

> **Video:** [INDENT] **Minimum: **                 3D graphics processor with Hardware Transform and Lighting with 32 MB VRAM                Such as an ATI Radeon 7200 or NVIDIA GeForce 2 class card or better
**Recommended: **        3D graphics processor with Vertex and Pixel Shader capability with 128 MB VRAM        Such as an ATI Radeon X1600 or NVIDIA GeForce 7600 GT class card or better [/INDENT]

[http://www.worldofwarcraft.com/info/faq/technology.html](http://www.worldofwarcraft.com/info/faq/technology.html)

---

### Post by JiuJitsu500 on 2010-01-22
Well if that doesn't throw a few wrenches in the gears I don't know what would.... damn...

Thanks for the reply :) On the same computer though, using Windows Vista, the game works wonderfully..... That's what confused me (still got learning to do in linux/ubuntu ad plent of it), he's doing all kinds of crazy stuff right now and I'm googling and typing over here to try and give a simpler answer. He's downloading a "linux driver for intel 9xx series cards" or something right now...

EDIT* Oh, and his quote is funny - "This is the dealbreaker, I will not put this on my computer if the game doesn't work in Ubun-whatever" :) Says he wants to suprise his wife when he gets home (in Iraq) with this.

---

### Post by cascade9 on 2010-01-23
Its probable that the intel drivers for windows are better than the linux drivers. Or because he is using an external hdd enclosure, its using more CPU (USB uses a lot more CPU power for HDD access than the normal IDE/SATA internal connections). Its also accessing the files slower (USB 2.0 will run at about 1/2 the speed of what I expect a SATA laptop hdd). 

That could be enough to make the game stutter. 

Hopefully, the intel 9xx drivers for linux worked though ;)

---

