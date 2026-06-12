---
title: "Startup Script, CRT Brightness"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by t4ggs on 2008-12-30
Hi, I have an old CRT monitor and its very dark, what I did was xgamma -gamma 2.0 and its much better now... but each time i restart the pc i have to do the same again...

how do i write a script to make it happen at startup?? just create a new file and paste there xgamma -gamma 2.0?? and make it run at startup???

---

### Post by TomasJancik on 2008-12-30
write a file that inclues these two lines:
#! /bin/bash
xgamma -gamma 2.0

and let it run on startup using the session manager

---

