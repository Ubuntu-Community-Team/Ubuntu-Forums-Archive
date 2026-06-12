---
title: "Some sounds play but not others"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by Andavane on 2009-05-23
Hello.
Youtube files are playing and sounding fine.
*.asx files are "playing" i.e. the bar is moving along and things are jiggling about on the screen suggesting that it is is playing fine, but no sound is coming.

In preferences/sound none of the test sounds is making any noise.

I have been fiddling around with the settings for some time and feel stumped.

Some ideas of what to try are welcome.

Regards

John

---

### Post by Screwdriver0815 on 2009-05-23
have you also checked the alsamixer?

for that, you open a Terminal and type in 

```
alsamixer
```

then in the terminal some slider-bars appear. There you should make sure that the Master and the PCM are not muted.

Moving in the menu is by the arrow keys on your keyboard, saving and exiting the settings is by pressing the ESC-button

hope this helps

---

### Post by Andavane on 2009-05-23
> **Screwdriver0815 said:**
> have you also checked the alsamixer?

for that, you open a Terminal and type in 

```
alsamixer
```

then in the terminal some slider-bars appear. There you should make sure that the Master and the PCM are not muted.

Moving in the menu is by the arrow keys on your keyboard, saving and exiting the settings is by pressing the ESC-button

hope this helps
Well I did that, and nothing was muted; but I slid a few things up-and-down and blow me! I have sound!

As I didn't appear actively to 'do' anything, I must assume the result is due to some magic emanating from your end... :D

Whatever the problem was, thanks for fixing it!

best wishes

John

---

