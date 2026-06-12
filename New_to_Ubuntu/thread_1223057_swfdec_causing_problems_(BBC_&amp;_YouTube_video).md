---
title: "swfdec causing problems? (BBC &amp; YouTube video)"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by qwerty_uk on 2009-07-25
Have been running ubuntu happily on my desktop for a while. Decided to install on my laptop using wubi. On the whole, this has gone well.

However, I'm having some big problems playing video from BBC and YouTube. BBC videos don't even load (the player freezes, but Firefox keeps working), while YouTube starts playing but after a while causes the whole PC to freeze!

I suspect that the problem is coming from swfdec. If I right click on the video on the laptop, I get options including "info", which tells me that swfdec is being used. If I do the same on my desktop, it gives me "about Adobe flash player 10".

I've installed flash player on the laptop, but I don't know how to get Firefox to use this rather than swfdec. So I can't test my theory.

Any help would be much appreciated.

Cheers

---

### Post by llamabr on 2009-07-25
```
swfdec-mozilla - Mozilla plugin for SWF files (Macromedia Flash)
flashplugin-nonfree - Adobe Flash Player plugin installer
```


you installed the first one, but you want the second one.

btw, I havn't used it, but totem now comes with the bbc plugin built in.  neat.

---

### Post by QIII on 2009-07-25
If you are sure you have Flash installed, then REMOVE swfdec and gnash, as they will likely cause conflicts.

---

### Post by qwerty_uk on 2009-07-25
That's done the trick - thanks!

I had tried "remove swfdec" (didn't know that the full name included "-mozilla")

I always try to be a good forum user, by doing a search first. But I wish I had just asked sooner on this occasion, rather than stressing about it for most of the day!

Thanks again.

---

### Post by lovinglinux on 2009-07-25
For future reference...

See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

