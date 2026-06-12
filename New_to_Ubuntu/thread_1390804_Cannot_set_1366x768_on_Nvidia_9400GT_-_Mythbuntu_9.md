---
title: "Cannot set 1366x768 on Nvidia 9400GT - Mythbuntu 9.10"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by jquintana on 2010-01-26
[FONT=Arial][SIZE=2]Hello, all.

I have a fresh install of Mythbuntu 9.10 that cannot display correctly on my tv. My tv is a Philips 50PF9956-37 with a native resolution of 1366x768. My video card is an Nvidia 9400GT and I have successfully loaded the Nvidia 185 drivers. [/SIZE][/FONT][FONT=Arial][SIZE=2]

If I go to Applications > System > Nvidia X Server Settings I have several resolutions available but not 1366x768.

I have read several guides about setting the resolutions in xorg.conf but following [this]("http://www.gacosta.net/Linux-Apache-MySQL-PHP/making-ubuntunvidia-recognize-your-widescreen-1366x768-resolution.html") guide caused me to have to reinstall Mythbuntu 9.10 on my system because I would only get a black screen. I even tried booting into "Safe Mode" and restoring my original xorg.conf but that didn't help either.

Any help is greatly appreciated!
[/SIZE][/FONT]

---

### Post by inobe on 2010-01-26
are you using an s-video cable.

---

### Post by jquintana on 2010-01-26
> **inobe said:**
> are you using an s-video cable.dvi -> hdmi

---

### Post by inobe on 2010-01-26
this method has always failed miserably, s-video failed too, the adapter works well hdmi to dvi, it doesn't work well the other way.

my monitors were automatically detected when using either vga or dvi.

in fact' i had terrible difficulty with that method on multiple platforms.

so i believe the connection is the culprit, the guide should have worked.

i wish i could offer more.

---

### Post by inobe on 2010-01-26
give this a go, of course you want to replace there modelines with your actual modes

[http://www.ypass.net/blog/2009/07/dvi-to-hdmi-overscan-screen-edge-cutoff-on-an-hdtv/](http://www.ypass.net/blog/2009/07/dvi-to-hdmi-overscan-screen-edge-cutoff-on-an-hdtv/)

---

### Post by jquintana on 2010-02-01
I bought an ASUS board with a dual-core atom and ion chip and am having the same problem. The new board has HDMI out so no need for DVI converters.

I just found this information for my TV:

[FONT=Verdana,Tahoma,Times New Roman][SIZE=2][LEFT][FONT=Verdana][SIZE=2]Philips 50PF9956/37  50"  Pixel Plus Flat TV, [COLOR=Red]**1366 x 768 pixels Resolution**[/COLOR], Aspect Ratio 16:9,**[COLOR=Red] [/COLOR]**[/SIZE][/FONT] [FONT=Verdana][SIZE=2]**[COLOR=Red]Computer formats : 640 x 480, 60Hz, 800 x 600, 60Hz, 1024 x 768, 60Hz[/COLOR]**, Picture in Picture:Full dual screen (2 tuners), Mozaic, Weight incl. Packaging:70 kg, [/SIZE][/FONT] [FONT=Verdana][SIZE=2][COLOR=#546451]Built-in speakers:4,  [/COLOR][/SIZE][/FONT] [FONT=Verdana][SIZE=2]RC 4306 Universal RC for VCR/DVD/DVD-R/SAT/ CABLE/AMP,  6 Widescreen Modes, Set Dimension (WxHxD) : 50.2"W x 34.7"H x 3.9"D[/SIZE][/FONT]


[FONT=Verdana][SIZE=2]Does that mean I will never be able to get the full 1366x768 or does it not matter since I am coming in to the tv using HDMI?
[/SIZE][/FONT][/LEFT]
[/SIZE][/FONT]

---

### Post by jquintana on 2010-02-02
:confused:

---

### Post by realzippy on 2010-02-02
..did you try to set desired resolution with nvidia-settings?
Sometimes it works to use the gnome display setting tool from the menue.When asked to use your graphic drivers vendor tool (nvidia-settings) click "no" and see if the resolution is there.
BTW,why doubleposting?
[http://ubuntuforums.org/showthread.php?p=8764453](http://ubuntuforums.org/showthread.php?p=8764453)

---

### Post by jquintana on 2010-02-02
> **realzippy said:**
> ..did you try to set desired resolution with nvidia-settings?
Sometimes it works to use the gnome display setting tool from the menue.When asked to use your graphic drivers vendor tool (nvidia-settings) click "no" and see if the resolution is there.
BTW,why doubleposting?
[http://ubuntuforums.org/showthread.php?p=8764453](http://ubuntuforums.org/showthread.php?p=8764453) 1366x768 is not an option in the Gnome display setting tool, either.
 
The double post is because one is an Nvidia 9400GT and the other ans an Nvidia ION.

---

