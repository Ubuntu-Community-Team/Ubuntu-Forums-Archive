---
title: "weird colours"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by AAH-motorfreak04 on 2011-03-08
so ive got myself an Asus P5PE-VM
just installed 10.10, and im getting all sorts of weird colors in totem
but most of the time, i wont get any video playing, just a blank screen
and ive been having other problems with my aero setup
ill attach some screenshots

any input would be greatly appreciated, as im still getting to grips with linux

i think it might have something to do with the driver...

---

### Post by Paddy Landau on 2011-03-09
I can't comment on the aero setup, because I use the default.

However, regarding Totem, you may want to install VLC Media Player (use Ubuntu Software Centre). VLC is usually reliable.

You might also need extra codecs. In Ubuntu Software Centre, go to Edit > Software Sources > Other Software > Add. Enter:
```
deb http://packages.medibuntu.org/ maverick free non-free
```(You'll be prompted for your password.)
Then search for *non-free-codecs* and install.

---

