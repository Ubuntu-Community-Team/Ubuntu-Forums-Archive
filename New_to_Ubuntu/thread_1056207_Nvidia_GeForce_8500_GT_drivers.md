---
title: "Nvidia GeForce 8500 GT drivers?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by yolsl on 2009-01-31
Gah, this is the third time I've installed Ubuntu on a computer using a Geforce 8500 GT card, 512mb VRAM. The first two times the drivers were preinstalled or came up via software update but this time I got nothing and can't enable desktop effects or anything.

I don't know how to get drivers for it because I've never really had to, been searching for it with no result. I remember using a series of command lines for a GeForce 8600 GT which worked on my sister's computer but it was a long time ago.

---

### Post by diablo75 on 2009-01-31
Did you look at System>Administration>Hardware Drivers to see if they're enabled or not?

---

### Post by yolsl on 2009-01-31
Yes. That is what EVERYONE told me to do O_o

I go there and it said there's no drivers at all. I found a thousand internet guides saying installing Nvidia drivers was as simple as going there and checking a box... but instead it says "No proprietary drivers are in use on this system." and the box under that is empty.

---

### Post by sandyd on 2009-01-31
have you tried envyng?

```

sudo apt-get install envyng-core
sudo envyng

```

---

### Post by yolsl on 2009-01-31
sudo envyng -t

...

Thank-you, that worked :O

---

