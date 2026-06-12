---
title: "problem installing an application"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by nadav reichler on 2010-10-15
i tried to install [http://apt.ubuntu.com/p/anjuta-dev](http://apt.ubuntu.com/p/anjuta-dev). 
i typed **sudo apt-get [http://apt.ubuntu.com/p/anjuta-dev](http://apt.ubuntu.com/p/anjuta-dev)**
and got this error:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[SIZE=1]**E: Couldn't find package http:**[/SIZE]

what might have caused this?

---

### Post by Toz on 2010-10-15
The package name is only 'anjuta-dev'. To install it, simply type:

sudo apt-get install anjuta-dev.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto) for more info.

---

