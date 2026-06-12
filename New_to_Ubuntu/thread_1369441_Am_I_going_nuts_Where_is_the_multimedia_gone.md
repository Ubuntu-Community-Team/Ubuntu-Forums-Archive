---
title: "Am I going nuts? Where is the multimedia gone?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by listerdl on 2010-01-01
Hi, I am having problems with my sound in 9.10 and the first thing I ought to do is check for sound being muted.

I checked on another post and the advice was to check this by Applications > Multimedia > Sound...

Ummm, where is my multimedia (?)

When I check in Applicaitons it isnt there?

Any ideas? THANKS!!!!!!!

---

### Post by Atzu on 2010-01-01
Check if enabled :P (right click on ubuntu icon and click edit)

---

### Post by waspbr on 2010-01-01
install a little app called gnome-alsamixer

```
udo apt-get install gnome-alsamixer
```

it will show in your Application > Sound and video section, go there and check if your volume levels are too low.

---

### Post by jpeddicord on 2010-01-01
Try System > Preferences > Sound; that applet tends to move around a lot between Ubuntu releases. :P

---

### Post by Methuselah on 2010-01-01
Also there should be a little speaker on the top panel.
If you right click it you should eb able to seelct sound preferences.

---

### Post by tenach on 2010-01-01
It was not under Applications > Sound & Video - I had to check to see if mine was muted by going to System > Preferences > Sound

I don't know if this will help you but I had to uninstall alsa-utils and install the package from Jaunty to get sound to work on a laptop I've been working on.

---

