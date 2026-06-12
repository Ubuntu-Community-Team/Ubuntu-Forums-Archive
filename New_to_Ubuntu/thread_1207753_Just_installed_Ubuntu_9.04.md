---
title: "Just installed Ubuntu 9.04"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Coh3n on 2009-07-08
Hello all,

So I just installed Ubu 9,04 on my laptop and went to enter this command into the command prompt:

```
sudo apt-get install ubuntu-restricted-extras
```I was told a while ago on this site that it would get me all the necessary plugins/codecs (codecs, java, flash, mp4, avi, mp3 etc), however I get this message:

```
cohen@cohen-laptop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
cohen@cohen-laptop:~$
```I used this command a while back on my desktop, and it worked like a charm, it got my Java working and all my music, so I was just wondering if it has changed or if there's another way of doing it.

Thanks,

Coh3n

---

### Post by wojox on 2009-07-08
Go to Applications > Add/Remove
Set show to All available applications
Search for
ubuntu-restricted-extras 
and install it. 
See if that helps.

---

### Post by credobyte on 2009-07-08
Enable [COLOR=Blue]multiverse[/COLOR] reposiroties ( software sources in [COLOR=Blue]System/Administration[/COLOR] ).
Also, 32bit ubuntu-restricted-extras does not include Java - you need to install it separately !

---

### Post by ivanvajar on 2009-07-08
Now you can install complete multimedia support on Ubuntu's web site by just clicking one link. Just look for it.

---

### Post by Coh3n on 2009-07-08
> **credobyte said:**
> Enable [COLOR=Blue]multiverse[/COLOR] reposiroties ( software sources in [COLOR=Blue]System/Administration[/COLOR] ).
Also, 32bit ubuntu-restricted-extras does not include Java - you need to install it separately !

I don't have that option, I have:

Canonical-supported open source software(main)
Community-maintained open source software(universe)
Proprietary drivers for devices (restricted)
Software restricted by copyright or legal issues (multiverse)

And they are all checked off.

---

### Post by oldos2er on 2009-07-08
Try this:
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Coh3n on 2009-07-08
> **oldos2er said:**
> Try this:
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

Yay, that worked, thanks a lot :D

---

### Post by nothingspecial on 2009-07-08
I usually follow [[COLOR="DeepSkyBlue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by nothingspecial on 2009-07-08
> **Coh3n said:**
> Yay, that worked, thanks a lot :D

Guess you don`t need to although it is worth a look.

---

### Post by Coh3n on 2009-07-08
> **nothingspecial said:**
> I usually follow [[COLOR=DeepSkyBlue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

That looks like it could be very helpful, thanks. :)

---

### Post by credobyte on 2009-07-08
> **Coh3n said:**
> I don't have that option, I have:

Canonical-supported open source software(main)
Community-maintained open source software(universe)
Proprietary drivers for devices (restricted)
**[COLOR=Red]Software restricted by copyright or legal issues (multiverse)[/COLOR]**

And they are all checked off.

I hope it was a joke ?

---

### Post by Coh3n on 2009-07-08
> **credobyte said:**
> I hope it was a joke ?

:p

---

