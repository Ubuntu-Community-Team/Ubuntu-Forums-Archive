---
title: "sd card does not mount"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by supermooshman on 2010-04-15
hey all,

A few days ago I tried accessing an sdcard (fat32) with the internal cardreader from my eee 901. When inserted, the card did not become visible in nautilus, nor did parted find it.
When I tried it with my imac and pc it worked like a charm.

is there any way I can solve this?

ps: before that time the card always mounted correctly

---

### Post by undecim on 2010-04-15
Do any other SD cards work?

When you put it in, do any new sd* or mmc* devices show up in /dev/?

open a terminal and run```
ls -1 /dev/ > ls.nosd.out
```
while you have no SD card inserted, and
```
ls -1 /dev/ > ls.sd.out
```
with it inserted, and then
```
diff ls.{,no}sd.out
```
after you've done both

Did the last command show anything?

---

