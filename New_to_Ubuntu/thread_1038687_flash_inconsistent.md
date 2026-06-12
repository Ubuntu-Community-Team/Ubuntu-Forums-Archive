---
title: "flash inconsistent"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by rwltrz4 on 2009-01-13
sometimes it works and sometimes it wont ,any ideas?

---

### Post by whoop on 2009-01-13
Happens to a lot of people (me too). Especially the 64bit version. Flash is not working optimal.

---

### Post by kansasnoob on 2009-01-13
I assume you have Firefox 3.0.5, you can find out by clicking on Help > About Firefox at the top of Firefox.

If not say so and also tell me what version of Ubuntu you're running.

If you are then begin by going to Terminal and running:

```
sudo apt-get install ubuntu-restricted-extras
```

Of course change that to xubuntu or kubuntu if that's correct.

Then go to Tools > Add-ons > Get Add-ons and search for and install Flashblock. You'll be prompted to restart Firefox, so do.

Give that a whirl!

Note: an older version of Flashblock is available in the repos but it doesn't work as well.

---

