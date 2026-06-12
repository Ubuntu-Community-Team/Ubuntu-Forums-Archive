---
title: "USB device recognition"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Skivache on 2008-12-19
I have a USB video capture card im trying to get working in linux. Its a generic Q-see model, which no real information online about what chipset it uses. So far I've tried it with Xawtv, but it can't read anything from /dev/video0. I used to be able to get the chipset/model info of another usb tuner using lsusb, but all I get with this (Q-see) is:
```
Bus 005 Device 004: ID 3100:f200 
```

What other commands can I use to find out chipset information and or what can I do to view video using it.

---

### Post by xjcannonx on 2008-12-19
I unfourtunately do not know of another command but the 3100 in that line is the vendor id(manufacturer) of the chip and you can google that with something like usb vendor id ****, I believe each vendor gets a unique id so you should be able to find it that way.

---

### Post by Skivache on 2008-12-19
Thanks for the suggestion xjcannonx, but i've tried searching for everything possible without any good results.  Just in case, I tried searching for some new terms including the one you mentioned without any luck. Perhaps I should try using another version or distro to try and get a better answer?

---

### Post by xjcannonx on 2008-12-19
Here check this out [http://www.boot-land.net/forums/?showtopic=1659]("http://www.boot-land.net/forums/?showtopic=1659")

---

### Post by Skivache on 2008-12-20
Well, I found out its made by Hang Zhou Silan Microelectronics Co. Ltd, but that doesn't help much.  Those tools on the USB page didn't give specific chipset info either.  Im going to be booting into 8.04 and 7.10 to see what I get.  Thanks again for the links :)

---

