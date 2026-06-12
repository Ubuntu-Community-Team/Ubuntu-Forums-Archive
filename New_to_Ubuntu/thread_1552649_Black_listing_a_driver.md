---
title: "Black listing a driver"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by audit on 2010-08-13
I have been having alot of problems with the wireless card that came with this laptop.

I have a usb wireless card that seems to work well. 

Reading an old post suggested that the one way to disable a wireless card is to "backlist" it. And since I have a wireless card that is nothing but headaches I thought maybe I should backlist it.


from what I can tell all you do is create a file at this named this:
> /etc/modprobe.d/blacklist

and add this line:
```
blacklist ath5k
```

is that really all there is to it? the only reason I am asking is because right now this file does not exist.

---

### Post by marshmallow1304 on 2010-08-13
I believe it's /etc/modprobe.d/blacklist.conf

---

