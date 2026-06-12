---
title: "Fixing font in wine?"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by Sexraider on 2009-11-26
Is there any possible way to fix the font when running applications in wine?

The font looks crunched and choppy.

Any help would be awesome, Thanks!

---

### Post by sandyd on 2009-11-26
```

cd /usr/bin
sudo wget [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo chmod 777 winetricks
winetricks fontfix fontsmooth-rgb corefonts droid allfonts
```

---

### Post by Wharf Rat on 2009-11-26
Thanks
Carlee

---

