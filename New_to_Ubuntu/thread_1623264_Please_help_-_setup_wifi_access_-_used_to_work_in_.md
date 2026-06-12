---
title: "Please help - setup wifi access - used to work in earlier ubuntu, now trying 10.10"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by luckylucky on 2010-11-16
Hi Folks,

A couple years ago I installed a Dlink usb wireless adapter to connect to wifi, and it worked.  Now I'm on ubuntu 10.10... and it doesn't.

Basically I'm following these steps:
[http://swik.net/Ubuntu/OnlyUbuntu+Tutorials/Howto+Setup+a+DLINK+WUA-2340+USB+Wireless+Adapter+in+Ubuntu+Hardy/b8mxw](http://swik.net/Ubuntu/OnlyUbuntu+Tutorials/Howto+Setup+a+DLINK+WUA-2340+USB+Wireless+Adapter+in+Ubuntu+Hardy/b8mxw)

I am not even able to see any wifi (bunch of houses around me are broadcasting).  I'm not even sure what exactly is wrong.  Could someone help me to figure out what might be wrong/different?  Thank you.

---

### Post by Hippytaff on 2010-11-16
There can driver issues with dlink usb dongles. To identify you chipset (probably ralink - something) do
```

lsusb

```
in the terminal...once you know have a look around the forums...there are a good number of threads with stuff on.

if you need morw help post back :-)

---

