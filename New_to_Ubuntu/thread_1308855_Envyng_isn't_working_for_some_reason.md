---
title: "Envyng isn't working for some reason"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by 133794m3r on 2009-10-31
EnvyNG was just installed on my pc. I got the envyng-gtk one. And then i saw it under my apps->System Tools->EnvyNG and for some reason when i click it does nothing... Does this mean it didn't install correctly? Or is there some other issue.

I also even tried running it from the alt+f2 interface and no such luck.

I'm trying to get it b/c ubuntu's "restricted drivers" for nvidia are only up to 185 and i'd like to get the 190 release.

---

### Post by imjafo on 2009-11-01
Did you install envy core and envyqt as well? When I installed envy I made the mistake of not installing all 3 of the envy packages, and it didn't work until I installed all of them.
Hope this helps

---

### Post by 133794m3r on 2009-11-01
... i have to install Envy-qt? well then i'm not using envy then. I don't see a reason to install the entire KDE system to just use envy.

---

### Post by gigglestick90 on 2009-11-01
hey. I had the same problem as you. I went to here for help: [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A). What I did was install it from the ubuntu software center and i tried to open it but nothing happened. so i went to that website and typed this in the terminal console:      sudo apt-get install envyng-qt      and it seemed to work.

---

### Post by volneilo on 2009-11-01
Hi guys!

I've just walked through this same path you did and discovered that *envy-gtk* is currently not working. So, you can use *envy-qt* GUI (and have all that KDE stuff) or use text mode (run envyng via terminal) instead.

Cheers! ;)

---

