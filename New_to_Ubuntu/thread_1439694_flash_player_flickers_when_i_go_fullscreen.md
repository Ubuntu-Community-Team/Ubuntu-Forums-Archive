---
title: "flash player flickers when i go fullscreen"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by tybaldwin on 2010-03-26
I know this is not an issue with my graphics card or at least i do not think it is because i can watch videos that ive downloaded fine you know. but when i try to watch youtube videos or videos from other streaming sites when i go into full screen the parts you know like thwe controls flciker in and out like usdually they would u know appear for a few seconds so like if u wanted to pause or rewind but then when you do not move your mouse they go away you know what i mean well the controls keep flicker andf stuff across the screen even thought i am not moving my mouse or anything they just flicker and it gets annoying this does not happen on my windows partition in windows vista paertition it works just fine just not in ubuntu 9.10 32 bit.

---

### Post by terdon on 2010-03-26
Hi tybaldwin, 

          this may be aknown issue relating to compiz (fancy desktop effects). If you are running compiz, try disabling it (Preferences=>Appearance=>Visual Effects) and then viewing the flash again, if that works you know compiz is to blame. 

So, if it is compiz you have to open compiz config and  uncheck "Unredirect fullscreen windows" in "General Options" and "Support legacy fullscreen" in the plugin "Workaround".

See [[COLOR="DarkRed"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?p=3961779") thread for more info.

---

