---
title: "Using photographs as a screensaver"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by groeswenphil on 2009-10-26
Hi,
I'm too mean to go out and buy a digital photoframe.....but I'd like to use my Netbook as one when it isn't being used.
I know how to do this using FSpot but it makes all of the photographs very small.
Is there a way to do a slideshow where your photograpsh are displayed full screen and you can say how long each one should be displayed for?
Phil

---

### Post by my_key on 2009-10-26
I use feh to do that. You'll need to combine fullscreen mode with a slide-change delay. Feh is very lightweigt so it'll run snappy on your netbook.

ciao

---

### Post by nothingspecial on 2009-10-26
```
feh -Fzr -D 5 ~/photos
```

Where F is fullscreen, z is random, r tells feh to go through the directories recursively and D specifies the time each picture is displayed before changing to the next one. The time is in seconds so my example would delay the pictures for 5 seconds.

---

### Post by groeswenphil on 2009-10-26
Does anybody know of anything that is a bit easier to set up....i.e. not using a command line?
Phil

---

### Post by John Bean on 2009-10-26
> **groeswenphil said:**
> Does anybody know of anything that is a bit easier to set up....i.e. not using a command line?
Phil

Have you actually looked under "Preferences->Screensaver"? Is seems to me that "Pictures folder" or "GLSlideshow" already do something close to what you want.

---

### Post by groeswenphil on 2009-10-26
That works. Thanks.

---

