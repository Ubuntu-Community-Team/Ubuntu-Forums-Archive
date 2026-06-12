---
title: "Firefox Issues"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by MikesGuitar on 2010-03-02
Firefox keeps freezing up on me and I cannot seem to figure out why. I have tried uninstalling and reinstalling a few times with no effect, and I also have all of my add-ons up to date. Any suggestions for a Firefox that keeps turning black and white and not responding?

---

### Post by s.fox on 2010-03-02
Hello,

1)  Does this happen on all sites you visit?  Or is it only on certain ones? 

2)  Do you run compiz fusion?  If so have you tried temporarily turned it off when web browsing ?

-Silver Fox

---

### Post by MikesGuitar on 2010-03-02
Yes I am, and it does seem to only freeze up on certain sites; such as when I click certain links and what not. Is there any way to solve this by NOT having to turn off compiz every time I web browse? This does not happen when I use Epiphany...

---

### Post by s.fox on 2010-03-02
Hello,

Just to clarify,  when you disabled compiz fusion Firefox no longer crashes?

-Silver Fox

---

### Post by Enigmapond on 2010-03-02
> **MikesGuitar said:**
>  This does not happen when I use Epiphany...

Well it shouldn't happen at all and we don't know what happens when YOU use Epiphany. What version of FF are you using? I would suggest purging your current one, deleting everything in home/*username*/.mozilla and doing a fresh install of the 3.6 via the repo.

[http://www.ubuntugeek.com/how-to-install-firefox-3-6-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/how-to-install-firefox-3-6-in-ubuntu-karmicjauntyintrepidhardy.html)

---

### Post by MikesGuitar on 2010-03-02
I am using 3.5.8. How exactly do I purge it? I tried removing from the software center and the package manager with not results...

---

### Post by Enigmapond on 2010-03-02
You may have more than one instance of FF...go to synaptic and completely remove everything firefox then delete everything firefox in you home .mozilla folder then follow the instructions on the link to install the new version.

---

### Post by MikesGuitar on 2010-03-02
Thanks guys, got everything working as of right now. All I did was following the instructions and commands for terminal. SOLVED

---

### Post by lovinglinux on 2010-03-02
For future reference and some tips on how to maintain Firefox performance, see [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

