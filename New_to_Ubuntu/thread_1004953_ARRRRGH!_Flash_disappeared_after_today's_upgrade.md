---
title: "ARRRRGH! Flash disappeared after today's upgrade"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by ah pook on 2008-12-07
What happened? and where do I look??? No more Youtube, etc...
Where do I start?

Ok, now that I calmed down a little, the problem is Firefox quit loading Flash video. For some reason I don't understand. Firefox 3.0.4, And running Ibex.. Please,  some ideas?

---

### Post by drs305 on 2008-12-07
Start by telling us what version of ubuntu you are using, whether it is 32 or 64 bit, and what browser you use. If you know, which version of flash were you running and how did you originally install it?

Have you tried simply removing (if installed) and reinstalling 'flashplugin-nonfree'?

---

### Post by residualbit on 2008-12-07
I had a similar issue a few days ago. flashplugin-nonfree just stopped working on me. I removed it an downloaded the one directly from Adobe (they even have a .deb download)

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

That worked flawlessly for me.

---

### Post by ah pook on 2008-12-07
gosh, that was quick. how do I remove flashplugin-nonfree? I'm running 64 bit Ibex, and it's been weorking flawlessly...

---

### Post by residualbit on 2008-12-07
ah 64bit flash...that is something I have no idea about

i would check here...[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by evilkastel on 2008-12-07
It's ok...there is no 64 flash, but 32 flash is ported. Just g to system>administration>Synaptic Package Manager, search "flashplugin-nonfree" and check reinstall. It happens rarely, but it does. Reinstalling should do the trick. OK good luck.

---

### Post by ah pook on 2008-12-07
you guys (girls?) are the best! removed, reinstalled, all better now!

Doon't know what happened, but it's working..

thanks very much...

---

### Post by kansasnoob on 2008-12-07
This works:

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

```
$ wget http://queleimporta.com/downloads/flash10_en.sh
$ sudo bash ./flash10_en.sh
```

---

### Post by Fass on 2008-12-07
> **evilkastel said:**
> It's ok...there is no 64 flash,

[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
[http://blogs.computerworld.com/64_bit_linux_adobe_flash_player_surprisingly_good](http://blogs.computerworld.com/64_bit_linux_adobe_flash_player_surprisingly_good)

Not quite true any more.

---

### Post by drs305 on 2008-12-07
ah pook,

Glad you got your flash restored. Would you please mark this thread Solved via the Thread Tools link at the top right of the first post? Marking it so helps others find solutions and assists helpers concentrate on unresolved issues.

I don't normally make posts about marking threads solved but since we were talking about 64-bit flash I just wanted to mention that the Flash 10 alpha of 64-bit flash has been working flawlessly for me for about a week. I can recommend it without reservation. It's available at the Adobe site:
[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

It is a .tar.gz file but you merely have to uninstall your current flash, extract one file and copy it to one or two locations. There are numerous posts in the forums about installing it.

---

