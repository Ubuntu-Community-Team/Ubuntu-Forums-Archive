---
title: "Red triangle warning appears when there are no uipdates to install"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by robfuller on 2010-10-12
Hello,

I think this is just a minor cosmetic issue, but I'm curious... The red triangle icon appears very often (at least once every 2-3 days) on my desktop, even when there are no updates to install. Earlier today I updated my system (and have rebooted since), but the red triangle has appeared again. When I run the update manager, there is nothing to install.

Is the red triangle trying to notify me of something else? Or should I just ignore it?

Thanks in advance,
Rob

---

### Post by spillage2 on 2010-10-12
im a complete novice but have you have got a broken package?

might be worth running the package manager to check and run fix broken packages.

---

### Post by robfuller on 2010-10-12
I've opened the package manager. How do I know if something is broken?

---

### Post by emoguitarist06 on 2010-10-12
Have you ran
```
sudo apt-get update && sudo apt-get upgrade
```
in the terminal?
If not please do so
It sounds like some of the repositories you are not being updated for some reason
Please post the output of that command here

---

### Post by robfuller on 2010-10-12
Ah, so that's it. One of my repositories was not valid. I've worked it out now. Thanks for your help!
Rob

---

