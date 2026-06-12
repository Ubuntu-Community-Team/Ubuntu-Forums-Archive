---
title: "problem with sound"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by soundpath on 2008-12-19
I can't get sound to work on my computer. I installed Ubuntu 8.10 yesterday. I tried to change some of the volume/ sound preferences but so far nothing has worked. I also disabled my onboard sound, which helped a little. I can hear some faint music, but there is a lot of hiss in the way. 
I tried plugging headphones directly into my sound card because I thought it might just be the speakers, but I encountered the same problem.

My soundcard is a soundblaster audigy 2 platinum (emu10k1 chipset) 

and my speakers are Logitech z-540 5.1 surround-sound. 

I'm new to Linux, so I'm at a loss as to what could be causing this problem.

---

### Post by linux_tech on 2008-12-19
Try installing gnome-alsamixer, then run it and try adjusting settings 
In terminal (Applications>Accessories>Terminal) type:

```
 sudo apt-get install gnome-alsamixer
```

---

### Post by soundpath on 2008-12-19
it worked. 

I just unchecked the option for Audigy Analog/ digital output jack and the sound is nice and clear. 

Thanks for the help, really appreciate it.

---

### Post by linux_tech on 2008-12-19
glad to hear you have sound!

---

### Post by Swerve1000 on 2008-12-19
This worked for me to!

Days I've been trying to fix this!!


):P

---

### Post by cigtoxdoc on 2008-12-20
The fix of "no sound" by installing the gnome-alsamixer worked for me too.

However, why did sound work at times w/o the gnome-alsamixer?

OS = 8.10

John

---

