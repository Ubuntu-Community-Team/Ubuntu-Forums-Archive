---
title: "Ubuntu 10.04 Compiz problem"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by myolbug on 2010-06-11
Hey,
Okay I have a Gateway NV52 laptop with Ubuntu 10.04 and I enabled the extra effects and selected Desktop cube in COmpiz and it resized my desktop and now all buttons are unresponsive, i.e I cannot undo my actions.  How do I use a terminal to turn off Compiz?

---

### Post by llawwehttam on 2010-06-11
Did a blog on this a while ago: [http://llawwehttam.blogspot.com/2010/01/reset-bad-compizconfig-settings-in.html](http://llawwehttam.blogspot.com/2010/01/reset-bad-compizconfig-settings-in.html)

---

### Post by myolbug on 2010-06-11
> **llawwehttam said:**
> Did a blog on this a while ago: [http://llawwehttam.blogspot.com/2010/01/reset-bad-compizconfig-settings-in.html](http://llawwehttam.blogspot.com/2010/01/reset-bad-compizconfig-settings-in.html)

I'll check it out later, thanks!

---

### Post by llawwehttam on 2010-06-11
If the blog I did does not work for you, get a terminal up and type:

```
rm -rf .gconf
```
 
that command will wipe your configuration settings, ie wallpaper etc... as well but its the easiest way to fix this problem. You will not lose any data, just your theme, wallpaper and icon settings.

---

### Post by myolbug on 2010-06-11
A big thanks to you!!!  I did the first portion of your instructions and it worked great, thanks!!!!

---

### Post by llawwehttam on 2010-06-11
Glad that worked for you. Could you mark the thread as solved ie Thread Tools ( near the top) and pressing mark as solved.

It just lets others see that your problem's been fixed.

---

