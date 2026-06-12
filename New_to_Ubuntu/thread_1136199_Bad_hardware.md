---
title: "Bad hardware?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Arias on 2009-04-24
I had some spare desktops laying around the house. They're pretty old (one is running pentium 4) but I wanted a desktop setup.

Well I installed ubuntu 8.10, it boots up perfectly and once you log in the screen goes black. Could this be bad hardware?

I ran the memory check and the cd check and both came out clean.


Thanks.

---

### Post by jrlii on 2009-04-24
I can't say for sure, but if you have an LCD monitor, it could be defaulting to a refresh rate faster than the monitor supports.

Practically all LCDs only support a refresh rate of 60Hz.

On my laptop, the boot starts out normal, then goes black and finally comes up normally when X-11/Gnome starts, and the settings X-11 uses takes over.

---

### Post by Arias on 2009-04-24
> **Ellen2 said:**
> It could be your video driver not properly installed yet. Or it could be resolution not set properly. Why dont you follow this thread and apply it to your system: [http://ubuntuforums.org/showthread.php?t=965478&highlight=freeze&page=4](http://ubuntuforums.org/showthread.php?t=965478&highlight=freeze&page=4)

That fixed the problem perfectly, thank you.

---

