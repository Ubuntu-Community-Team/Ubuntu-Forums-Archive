---
title: "hard drive keeps going mental and slowing ubuntu?"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by kapi on 2009-04-06
hi, wondered if anyone else has had this. Recently I've had the hard drive light go mental on my laptop because something is accessing it like theres no tomorrow. Its so bad that I have to force a shut down by holding in the start key on the laptop.

I did wonder if it could be linked to wine and IES4Linux as I switch between ff and ie constanly - 

any ideas would be welcome

thanks

---

### Post by CLomax on 2009-04-06
Memory leak?

I got that a lot when running things on WINE.

---

### Post by taurus on 2009-04-06
Next time when that happens, open a terminal and look at top too see which process (or processes) is hogging the CPU.

```
top
```

---

### Post by kapi on 2009-04-06
yeah it appears to be wine  - how do I force a quit again

---

### Post by halitech on 2009-04-06
open a terminal and type in
```
killall -9 wine
```should do it

might also need to do it with sudo

---

### Post by kapi on 2009-04-06
thanks very much for your help

kapi

---

### Post by LowSky on 2009-04-06
> **kapi said:**
> 
I did wonder if it could be linked to wine and IES4Linux as I switch between ff and ie constanly - 

any ideas would be welcome

thanks

Stop using Internet Explorer...lol

I know some ste require IE but there are work arounds, like agent switcher for Firefox. and using Windows FireFox in Wine.

In all seriousness you could run Wine and IE form a terminal, might give you an idea of what is going wrong.

---

