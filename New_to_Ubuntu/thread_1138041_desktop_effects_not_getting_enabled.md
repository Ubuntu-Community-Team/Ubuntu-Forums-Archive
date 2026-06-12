---
title: "desktop effects not getting enabled"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-04-26
hi,

i just installed ubuntu jaunty in my system.. when i try to enable the desktop effects in my system.. it says "Desktop effects could not be enabled" ...


ubuntu 8.10 gave me all the desktop effects... why is jaunty not enabling me any desktop effects in the same system....

---

### Post by Spiritous on 2009-04-26
> **luckydeveloper said:**
> hi,

i just installed ubuntu jaunty in my system.. when i try to enable the desktop effects in my system.. it says "Desktop effects could not be enabled" ...


ubuntu 8.10 gave me all the desktop effects... why is jaunty not enabling me any desktop effects in the same system....

I have this too... Any answers?

---

### Post by organicanagram on 2009-04-26
Do you know what kind of graphics cards your computers are using? The X3100 cards, as well as some other intel variants, were blacklisted, which could be causing your problem.

---

### Post by luckydeveloper on 2009-04-26
hey.. intrepid was giving me all those.. why not jaunty.. thats the point..

---

### Post by organicanagram on 2009-04-26
yes, the ubuntu dev team did so with the recent release of jaunty.

Anyway, here's the workaround:
```

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

```

Type that into a terminal, then logout and login. It should work.

---

### Post by luckydeveloper on 2009-04-26
what should i do to enable the desktop effects... in my system

---

### Post by calrogman on 2009-04-26
Going out on a branch I'm guessing you are using an integrated Intel graphics chip, such as the  "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)".

If you are, you should know that integrated Intel chips have been blacklisted until a bug in compiz is ironed out.  If you really want to enable desktop effects (or disagree with how the whole thing is handled) then open "~/.config/compiz/compiz-manager" in your favorite editor and change the line "SKIP_CHECKS=no" to "SKIP_CHECKS=yes".  You can then enable compositing, but don't count on it working.

---

### Post by luckydeveloper on 2009-04-26
when will the blacklisted chips be given access to desktop effects... or when will the bug in compiz be handled..

---

### Post by organicanagram on 2009-04-26
Here's the bug they're working on.
 [https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392]("https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392")

Here's a less technical explanation of the problem. basically the cards just caused random crash/freezes:
[http://www.realistanew.com/2007/09/23/compiz-in-ubuntu-update/]("http://www.realistanew.com/2007/09/23/compiz-in-ubuntu-update/")

Honestly though I've changed SKIP_CHECKS to yes and haven't encountered any problems. So far, at least.

---

### Post by luvinit on 2009-04-26
I also find that I can't enable them with a Nvidia 8800GT.

---

### Post by calrogman on 2009-04-26
Those guys are presumably who I'd file a bug report to about how the blacklist is handled as well?

Really I think that if your chip/card is blacklisted you should still be able to enable compositing, just go through a warning pop up first.  Not just get given cryptic messages.

---

### Post by blackened on 2009-04-26
> **luckydeveloper said:**
> when will the blacklisted chips be given access to desktop effects... or when will the bug in compiz be handled..

This is a user forum, we have no way of knowing the answer to either of those questions. The only information I've seen on the subject says that they will be fixed in a post-Jaunty-release update. That means any time between now and October.

---

### Post by luckydeveloper on 2009-04-26
> **organicanagram said:**
> yes, the ubuntu dev team did so with the recent release of jaunty.

Anyway, here's the workaround:
```

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

```

Type that into a terminal, then logout and login. It should work.


I did that.. after logout and login,

when i try to check the option button visual effects tab, after i do that, the screen goes white and after about 10 seconds, the desktop comes back and nothing happens. the visual effects is once again "none". I tried this several times, the same thing happens.. 

please help

---

