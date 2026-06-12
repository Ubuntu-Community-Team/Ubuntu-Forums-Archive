---
title: "Loading or Bootup Screen"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by hifly1231 on 2010-11-21
Why does the loading screen in Ubuntu 10.10 look so cheap?  It looks like nobody put any thought into it whatsoever, unlike previous versions.  Is there any way to change this back to the one in Ubuntu 10.04?

---

### Post by ajgreeny on 2010-11-21
I presume you mean he purple screen with "ubuntu" and five coloured dots beneath?

That is plymouth and it is still in its infancy and causing a few problems with some graphic cards.  As to your preference about the artistic impression it gives, I think that is very personal;  it's only there for a few seconds, so does it really matter that much?

Not to me, it doesn't.

---

### Post by sikander3786 on 2010-11-21
Yep there are a few problems with plymouth that still need to be addressed.

For a workaround, see here.

[http://linuxhub.net/2010/09/fix-ugly-plymouth-screen-on-ubuntu-10-10-using-a-simple-script/](http://linuxhub.net/2010/09/fix-ugly-plymouth-screen-on-ubuntu-10-10-using-a-simple-script/)

---

### Post by Quackers on 2010-11-21
Or this :-)

[http://ubuntuforums.org/showthread.php?t=1469475&highlight=problems+lucid+lynx](http://ubuntuforums.org/showthread.php?t=1469475&highlight=problems+lucid+lynx)

Scroll down to the heading that says [COLOR="DarkRed"]Bootup/Plymouth. [/COLOR]
This works for me.

---

### Post by hifly1231 on 2011-01-17
I've found the solution.  You have to go into Startup Manager, and make sure that the Display Resolution and the Bootloader Menu Resolution (Advanced Tab) are set to 640X480, and change the Color Depth to 24 bits.

---

