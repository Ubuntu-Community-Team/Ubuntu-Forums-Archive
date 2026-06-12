---
title: "Pandora Radio not showing"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by mjnuss on 2009-11-08
I can't seem to use Pandora Radio.  The website will load but the interface won't come up at all, it remains a big white block.  I'm a little stumped, I don't have any problems with youtube and I've already tried reinstalling the Flash plugins.  Any ideas?

Mike

---

### Post by think13 on 2009-11-08
Pandora seems to work for me. What flash plugin are you using? You can check by typing about:plugins in the Firefox address bar.

Mine says 
Shockwave Flash
File name: libflashplayer.so
Shockwave Flash 10.0 r32

If you don't have that, try using the Adobe Flash plugin in the Software Center.
Also, make sure you aren't blocking it with something like AdBlock.

---

### Post by mjnuss on 2009-11-08
Looks like I have the same plugin version, but if I scroll down I see a second listing for flash

libswfdecmozilla.so
Shockwave Flash 9.0 r999

Could this be the underlying problem?

---

### Post by tom.swartz07 on 2009-11-08
> **mjnuss said:**
> Looks like I have the same plugin version, but if I scroll down I see a second listing for flash

libswfdecmozilla.so
Shockwave Flash 9.0 r999

Could this be the underlying problem?

thats it!

install the flash plugin from the software center, and you should be good

---

### Post by mjnuss on 2009-11-08
> **tom.swartz07 said:**
> thats it!

install the flash plugin from the software center, and you should be good

It is/was installed. :/

---

### Post by tom.swartz07 on 2009-11-08
> **mjnuss said:**
> It is/was installed. :/

okey dokie- just remove the swfdec module.
sudo apt-get remove --purge swfdec*

im not exactly sure about the proper title, so you might have to play around with different variations of that- swfdecmozilla, swfdec, swfdecplugin, etc.

once you have it removed, firefox should use the official flash plugin.

---

### Post by mjnuss on 2009-11-08
> **tom.swartz07 said:**
> okey dokie- just remove the swfdec module.
sudo apt-get remove --purge swfdec*

im not exactly sure about the proper title, so you might have to play around with different variations of that- swfdecmozilla, swfdec, swfdecplugin, etc.

once you have it removed, firefox should use the official flash plugin.

I was able to successfully remove it (swfdec-mozilla  FYI) and it doesn't appear on my about:plugins page anymore.  BUT, pandora still won't load.  When right-clicking the white space where it should be, I see "Movie not loaded..." grayed out.  Also,the progress bar on the bottom of the screen says its "Done" though.

---

### Post by beastrace91 on 2009-11-08
Have you installed Adobe's flash plugin? ```
sudo apt-get install flashplugin-nonfree
```

~Jeff

---

### Post by mjnuss on 2009-11-08
> **beastrace91 said:**
> Have you installed Adobe's flash plugin? ```
sudo apt-get install flashplugin-nonfree
```

~Jeff

yessir

---

### Post by mjnuss on 2009-11-10
Still no luck, any advice?

---

### Post by twisted_steel on 2009-11-10
I have both libflashplayer.so and  libswfdecmozilla.so in about:plugins on my laptop.  Pandora works fine for me.  Have you tried a new Firefox profile to see if there is a problem with yours?

This (from a terminal) will display the profile selection window.
```
firefox -no-remote -P
```

---

