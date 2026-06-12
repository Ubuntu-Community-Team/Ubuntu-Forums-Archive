---
title: "Jaunty fails to play vidoe online"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by south_coaster on 2009-05-06
I just upgraded my laptop to Jaunty a couple of weeks ago. Since that time I have not been able to play video from CNN. I have 2 laptops. Both have Jaunty. One has the Ubuntu Remix and one a standard Dell using Jaunty. Neither will play online videos. Does anyone have any idea how to get it to work?

---

### Post by LowSky on 2009-05-06
CNN is playing fine for me have you tried reinstalling flash?

---

### Post by -kg- on 2009-05-06
Upon installing Jaunty (not an upgrade...I did a fresh install) I did what updates there were and installed restricted extras from Synaptic PM.  After I did that, all online streaming videos worked flawlessly.

I see that you upgraded to Jaunty.  Have you checked Synaptic to make sure that restricted-extras is installed?  That might be the problem.

---

### Post by acimmarusti on 2009-05-06
Open up a terminal and do:

```

sudo apt-get install ubuntu-restricted-extras

```

That should do it

---

### Post by presence1960 on 2009-05-06
> **south_coaster said:**
> I just upgraded my laptop to Jaunty a couple of weeks ago. Since that time I have not been able to play video from CNN. I have 2 laptops. Both have Jaunty. One has the Ubuntu Remix and one a standard Dell using Jaunty. Neither will play online videos. Does anyone have any idea how to get it to work?

are you using 32 bit or 64 bit? If 64 bit uninstall all Flash and follow this : [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

for java plugin for 64 bit follow this : [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

Kudos to zika for sharing this java plug in how to.

---

