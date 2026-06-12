---
title: "no visual effects for ati 9550"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by Redmage913 on 2010-01-02
Greetings,

I'm running a Dell 4600 with an ATI Radeon 9550 256MB video card installed in the AGP slot, running a dual-boot with Karmic and XP.  XP works fine, but I'm having video issues with Karmic.  I put in this card after having problems with my Radeon 9600 256MB AGP (couldn't render anything in Ubuntu well; constant graphics corruption. I got this card off a friend and it works for basic tasks.)

I wanted to turn on graphical effects, but it won't let me.  I think I saw the Restricted Drivers program searching for available drivers, but the window disappeared and I got an error message saying "Desktop effects could not be enabled".

Supplemental Information:  I haven't tried any other graphics-intensive tests on Karmic, though I can say that Starcraft, when ran under Wine, works fine.  I dunno if that's even relevant.

Any suggestions?

--Redmage913

---

### Post by Mark Phelps on 2010-01-02
That card is too old for any ATI hardware drivers in Ubuntu's newer than 8.10.  You're stuck using the open source drivers -- which are installed by default.  Don't attempt to download and install the drivers from ATI -- they won't work and will only hose up your display.

---

### Post by 3rdalbum on 2010-01-02
There are more recent ATI cards (Radeon HD 4000 series) available in AGP versions - PowerColor makes them. You might want to get one of these because you can use the proprietary ATI driver with them.

Otherwise, you can live without desktop effects until there is 3D support in the open-source driver.

---

