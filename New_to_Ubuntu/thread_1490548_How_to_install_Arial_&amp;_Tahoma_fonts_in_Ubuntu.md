---
title: "How to install Arial &amp; Tahoma fonts in Ubuntu"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by webwiller on 2010-05-22
In order to run Pokerstars software at its best with Wine I read that Id need to install Arial&Tahoma fonts, which are Ms fonts.
Here enclosed I found a file to install these fonts but I dont know how to use it.
Can anybody help me please?
Thx in advance!
Chri

---

### Post by sandyd on 2010-05-22
```

wget -c [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo apt-get install cabextract
chmod 667 winetricks
sh ./winetricks allfonts fontfix fontsmooth-rgb droid

```

---

### Post by webwiller on 2010-05-22
ty very much!

---

