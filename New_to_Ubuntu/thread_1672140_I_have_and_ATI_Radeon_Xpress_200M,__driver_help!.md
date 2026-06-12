---
title: "I have and ATI Radeon Xpress 200M,  driver help!?"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by shatanas on 2011-01-20
**Problem:** 3D games, be it chess or tuxracer do not work. They keep flashing rapidly between black covering the [game] window and the game.

**Goal:** I want to be able to run Ubuntu games and possibly World of Warcraft

ok, so first of all, I had the catalyst control centre on Windows XP.

I had installed World of Warcraft under wine and it churned out ridiculously low frame rates (~3fps) although it worked smoothly under windows.

I have looked at the first search results google gives me, but it is all very very technical and I am afraid to mess things up.

This site: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) totally confuses me- what does better dual-head support mean!? Should I install the free driver or closed source? More importantly, how!?

+do any of those provide a GUI? Like the Catalyst Control Centre?

I apologise for a hefty load of questions, but this has annoyed me to the bones!

---

### Post by khelben1979 on 2011-01-21
[On this webpage]("http://www.ensode.net/ati_radeon_xpress_200m_linux.html") you have 2 links down the page where you can download the correct driver for your graphic card/chipset. It's important to choose the correct one, either 32bit or 64bit version of the driver.

You also have the possibility to configure your [X server]("http://en.wikipedia.org/wiki/X_server") to use the open source Radeon driver.

What version of Ubuntu are you using?

---

### Post by cascade9 on 2011-01-21
ATI proprietary drivers wont work with the x200 with any new version of ubuntu (IIRC 8.10 or 9.04 was the last to have ATI drivers for the x200). 

If you try to install ATI drivers on a version later than that, all you will do is break x. Then you'd need to remove the drivers to even get your desktop back. The only drivers that will work with that card on current ubuntu versions are the open soruce drivers.

---

### Post by khelben1979 on 2011-01-22
> **cascade9 said:**
> The only drivers that will work with that card on current ubuntu versions are the open soruce drivers.

Thanks for clarifying. Then it's open source drivers only for that chipset.

---

### Post by shatanas on 2011-01-22
I am using Ubuntu 10.10

---

### Post by shatanas on 2011-01-22
ohhh right....damn it

---

### Post by cascade9 on 2011-01-22
You migth want to look into gallium3D. It wont be quite as fast as the catalyst drivers were in older ubuntu versions though- 

[http://www.phoronix.com/scan.php?page=article&item=amd_r500_expanded&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r500_expanded&num=1)

---

