---
title: "Nvidia ION has correct resolution on 1 TV but not the other"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by jquintana on 2010-02-01
I have 2 TVs that I am testing with. One is a 19" Dynex LCD and the other is a 50" Philips Plasma. I am connecting both via HDMI to my ASUS motherboard with has an Atom 330 and Nvidia ION.

Both TVs have a native resolution of 1366x768. On the 19" I am able to get 1360x768 which I am thrilled with. On the 50" I am not. I know the card is cable of it now but am not sure how to configure the card to use the correct resolution on the 50" TV.

Any help is GREEEEEATLY appreciated!!!

---

### Post by LowSky on 2010-02-01
open terminal, type

gksu nvidia-settings

go to X server display config

---

### Post by jquintana on 2010-02-01
> **LowSky said:**
> open terminal, type

gksu nvidia-settings

go to X server display configIs that any different from sudo nvidia-settings ?

I have run sudo nvidia-settings but the problem is that when connected to the 50" TV I do not see 1366x768.

Thanks!

---

### Post by jquintana on 2010-02-01
I just double-checked my nvidia-settings while connected to my 50" TV and saw that the 195 driver is showing that the TV has a native resolution of 1024x768.

I just found this information for my TV:

[FONT=Verdana,Tahoma,Times New Roman][SIZE=2][LEFT][FONT=Verdana][SIZE=2]Philips 50PF9956/37  50"  Pixel Plus Flat TV, [COLOR=Red]**1366 x 768 pixels Resolution**[/COLOR], Aspect Ratio 16:9,[/SIZE][/FONT] [FONT=Verdana][SIZE=2]**[COLOR=Red]Computer formats : 640 x 480, 60Hz, 800 x 600, 60Hz, 1024 x 768, 60Hz[/COLOR]**, Picture in Picture:Full dual screen (2 tuners), Mozaic, Weight incl. Packaging:70 kg, [/SIZE][/FONT] [FONT=Verdana][SIZE=2][COLOR=#546451]Built-in speakers:4,  [/COLOR][/SIZE][/FONT] [FONT=Verdana][SIZE=2]RC 4306 Universal RC for VCR/DVD/DVD-R/SAT/ CABLE/AMP,  6 Widescreen Modes, Set Dimension (WxHxD) : 50.2"W x 34.7"H x 3.9"D[/SIZE][/FONT]


[FONT=Verdana][SIZE=2]Does that mean I will never be able to get the full 1366x768 or does it not matter since I am coming in to the tv using HDMI?[/SIZE][/FONT][/LEFT]
[/SIZE][/FONT]

---

### Post by jquintana on 2010-02-02
:confused:

---

