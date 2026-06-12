---
title: "HP pavilion DV6000 - UNR"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by Smeltn on 2010-02-23
Hello all,

I am looking to get into Ubuntu on my laptop, but it is mainly being used by my wife and 11 yr old daughter. I want something that would be easy for them to just pick up and use, which Ubuntu Netbook Remix looks perfect to start off with. The problem is when I try to install it, (I have tried installing from CD and from creating a bootable USB drive) and both give me the same error: 

```
Can not mount /dev/loop1 on /cow
```

Now I have an AMD processor in my HP Pavillion DV6408nr so I assume thats why since UNR is made for Intel Atom processors. Is there another release that will work with AMD processors? I really want the UNR to start with.

Thanks

---

### Post by 416inversed on 2010-02-23
If you install the AMD Ubuntu Desktop iso, you should be able to then put UNR on top of it.

In terminal:
```
sudo apt-get install ubuntu-netbook-remix
```Should install all of the UNR packages.

---

### Post by Smeltn on 2010-02-23
Ok so install normal desktop version of ubuntu then install the UNR on top of that. Gotcha

Thanks

---

