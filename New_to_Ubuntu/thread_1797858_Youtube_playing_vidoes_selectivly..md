---
title: "Youtube playing vidoes selectivly."
date: 2011-07-05
forum: New to Ubuntu
---

### Post by Newuser901 on 2011-07-05
^ It appears to play selectively. It refuses to play a lot of videos. I can play singing in the rain but not a lot of other stuff. and it appears to grow daily. Any idea why? I"m trying to update adobe but I'm having a hard time getting it. Not even sure if what i'm using is newer. But has anyone been seeing this issue. It might help.

Ubuntu 11.04 64bit!

---

### Post by wojox on 2011-07-05
Have you tried the [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") add-on written by an Ubuntu member, to see if it resolves anything? It will remove any conflicts and install the correct player for your system.

---

### Post by EVILCOOKIE on 2011-07-05
What error message do you get (if any)? Do you get an empty black rectangle when you click a video? If so, have you tried adding https instead of http at the beggining of the address bar?

You can get flashplayer for 64 bits from [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html) and put libflashplayer.so into ~/.mozilla/plugins, then activate it from the addons menu.

---

### Post by whatthefunk on 2011-07-05
What browser do you use?  Ive always used Firefox, but the last few days Ive been having the same problem.  Youtube videos play fine on Chromium though.

---

### Post by hakcayurek on 2011-07-05
> **whatthefunk said:**
> What browser do you use?  Ive always used Firefox, but the last few days Ive been having the same problem.  Youtube videos play fine on Chromium though.

yeah same here. I use kubuntu, and youtube was ok until a few days ago. Now it is just a black box. Other flash sides seems to be ok for me. Does anybody know  a  solution?

well looks like this is a common problem:

[http://ubuntuforums.org/showthread.php?t=1797402](http://ubuntuforums.org/showthread.php?t=1797402)

---

### Post by whatthefunk on 2011-07-06
[http://ubuntuforums.org/showthread.php?t=1280836&page=2](http://ubuntuforums.org/showthread.php?t=1280836&page=2)

This worked for me.  Delete the cookies from youtube and disable cookies for youtube.

---

