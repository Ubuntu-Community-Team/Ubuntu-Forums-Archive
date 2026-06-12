---
title: "blackbox window manager -  how to change screen resolution?"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by ltk5 on 2010-09-21
Hello!
I have Ubuntu 8.10 installed and I wanted to try blackbox, because it should be lightweight. The problem I'm having is the screen resolution. 
It is at max (1280 x ...) and I would like to make it lower.

I've been searching around but couldn't find any useful tips. How to do this?

---

### Post by Seq on 2010-09-21
> **ltk5 said:**
> Hello!
I have Ubuntu 8.10 installed and I wanted to try blackbox, because it should be lightweight. The problem I'm having is the screen resolution. 
It is at max (1280 x ...) and I would like to make it lower.

I've been searching around but couldn't find any useful tips. How to do this?

You should be able to do this with xrandr. `xrandr` alone gives you available resolutions, `xrandr -s 1024x768` sets one. `man xrandr` for more info.

---

### Post by ltk5 on 2010-09-21
thank you very much. That helped! :)

---

