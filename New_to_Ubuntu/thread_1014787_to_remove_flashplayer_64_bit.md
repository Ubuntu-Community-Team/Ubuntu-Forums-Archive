---
title: "to remove flashplayer 64 bit"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by theemperor on 2008-12-18
Hi,

I had installed Flash player 64 bit alpha edition recently(ubuntu 7.10 system). Post that, firefox/epiphany hangs very frequently. How do i remove flash player 64 bit plugin from Firefox and epiphany browsers

Thanks

Bijoy

---

### Post by any.linux12 on 2008-12-18
sudo apt-get remove flashplugin-nonfree

---

### Post by any.linux12 on 2008-12-18
sudo apt-get remove epiphany-browser

sorry that I posted twice but i did see it before

hope it works

---

### Post by Sef on 2008-12-18
Moved to absolute beginners.

---

### Post by bwang on 2008-12-18
You can do this:

```

cd ~/.mozilla/plugins
rm libflashplayer.so

```

---

