---
title: "playing movies&amp; playinggames(winxp ones using Wine)"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by thelegionsplayer on 2009-05-08
the movies i play(avi)are very choppy cant c anyting properly.and also wen i open games using wine the screen is a whole lot choppier than running videos..my resolution:-1440*900(16:10) winxp best resolution was 1024*768 ..so will the movies and games speed up if i reduce the resolution?(i hav set low  resolution for games(i tried running proj igi wich dsnt need much ram and aint so cpu intensive)my rams only-512mb so is that the problem?(procesor :-dual core 1.6 ghz,video adapte memory:-64)

---

### Post by thelegionsplayer on 2009-05-08
bump

---

### Post by achase79 on 2009-05-08
What graphics chipset do you have? Nvidia, ATI, Intel?

Sometimes this is just a video card driver issue.

---

### Post by alexandari on 2009-05-08
I dunno if I understood that...so you say that the videos you`r playing look bad and the games under wine are slow?
1. what movie player are you using? try mplayer or vlc
2. are you using compiz or any desktop effects while playing games?
3. some games may run slowly under wine...because maybe there`s a workaround which fixes that or something + you need to be using the latest version of wine to be sure it`s not something because of the earlyer wine version.

---

### Post by thelegionsplayer on 2009-05-08
Graphic card-VIA chrome 9hc igp 64 mb
Im using the default thing movie player (wich says totem wen i open it)under applications >sound and video
i dunno wat compiz is and visual effects:-none
PS; i   hadnt  installd the game in wine(not that installing wud make a change)

---

### Post by jacksinn on 2009-05-08
It's possible that you don't' have effective 3D drivers installed for your sound card. If you don't mind using restricted/proprietary drivers you can go to System-->Administration-->Hardware Drivers and if any proprietary drivers are available within the scope of your repositories, you should be able to install them. 
If not, I recommend visiting your graphics card manufacturer's website for drivers or checking the known good/bad hardware forums for Ubuntu.

---

### Post by thelegionsplayer on 2009-05-08
My graphics card is VIA Chrome9 hC IGP 

well i downloaded the driver but it says its for 8.04.is it ok if i install it in 9.04?
here are the deails


Integrated VIA Chrome9™ HC IGP
                              DirectX® 9.0 engine
                                Pixel Shader 2.0
                                Dual pixel pipeline
                                128-bit 2D/3D engine
                               250MHz engine clock speed Optional external PCI Express x16 interface

---

### Post by coskierken on 2009-05-08
The VIA Chrome does not have good 3d support.  Try checking to see if you have any desktop effects turned on.  To do this, right click anywhere on your screen and change desktop appearance.  Go do special effects and make sure you have NONE!  On older video chips and even on good chips under 8.10, this can cause the video to be choppy.  Download VLC and use it instead of mplayer or totem.  This should help.

---

