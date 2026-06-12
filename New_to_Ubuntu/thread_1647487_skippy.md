---
title: "skippy"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by dzon65 on 2010-12-17
Does anyone know how to install skippy in openbox?

---

### Post by dzon65 on 2010-12-17
Just found out how.
Regards,J.

---

### Post by matt_symes on 2010-12-17
Hi

Fancy posting how you did it for others?

Kind regards

---

### Post by Rubi1200 on 2010-12-17
> **matt_symes said:**
> Hi

Fancy posting how you did it for others?

Kind regards
I'll second that motion!

Sharing your solutions with other users is what makes this operating system and this forum special.

So, as they say, spill the beans ;)

---

### Post by dzon65 on 2010-12-17
Gimme a sec. Actually found it on the forum. Right back.

---

### Post by dzon65 on 2010-12-17
Okay, here's the link.[http://ubuntuforums.org/showthread.php?t=30510](http://ubuntuforums.org/showthread.php?t=30510)
It comes down to installing those dependencies ( mind you, 23Mb), editing the makefile and cpying the skippyrc-default to your home folder and rename it.
Btw, posted this another thread already. Since skippy needs something to begin with, you can't add it as such to your ~/config/opnbox/autostart.sh, you'll need to add some sleepie to it like so: sleep 5 && skippy &
You could choose to add a shortkey to it but if you install xautolock, you could bind it to a screen launcher.
Sorry for the crappy english. Check out Urukrama's blogs.[http://urukrama.wordpress.com/category/openbox/](http://urukrama.wordpress.com/category/openbox/)

---

### Post by Rubi1200 on 2010-12-17
Very nice dzon65 :)

Thanks, it is definitely appreciated.

---

### Post by dzon65 on 2010-12-17
You're welcome. If only I could  get rid of that damn focus color. Oh well, I'll figure it out.

---

