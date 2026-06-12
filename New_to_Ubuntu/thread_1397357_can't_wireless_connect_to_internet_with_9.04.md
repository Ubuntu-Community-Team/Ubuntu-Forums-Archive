---
title: "can't wireless connect to internet with 9.04"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by mellors.john on 2010-02-03
:Pbeginner here, sort of... I have a laptop with windows xp and wireless connection to a cable modem.. works fine.. I installed ubuntu 9.04 and it works fine.. when I boot up I have a choice of which os to use... ok.. the problem is I cannot connect to the internet with ubuntu... network manager does not show any wireless devices to choose.. I've read all the posts and it is a bit too complex... is there a simple way to get it to work..yeah, I did the lshw -C network command and saw this: *network disabled.. ok, now what do I do???
 
going nuts in new jersey

---

### Post by norbert26 on 2010-02-03
first connect with the cat 5 cable direct . go into adminstration and locate hardware drivers on the drop menu. have ubuntu look for your wireless card driver(s) . if it has them they will be presented to you . install them and your wireless card should work.

---

### Post by mellors.john on 2010-02-03
I like that!.. I'll give it a try..

---

### Post by thatguruguy on 2010-02-03
What wireless card do you have?

EDIT: If it's a broadcom (which I suspect) you may want to check out [this thread]("http://ubuntuforums.org/showthread.php?t=1368699").

---

### Post by mellors.john on 2010-02-03
this is the wireless modem I use.. works fine with windows xp
 
SMC 8014wg-s1....  got it from Time Warner Cable
 
[http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=2&scid=19&pid=1584](http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=2&scid=19&pid=1584)

---

### Post by anaconda on 2010-02-03
> **mellors.john said:**
> this is the wireless modem I use.. works fine with windows xp
 
SMC 8014wg-s1....  got it from Time Warner Cable
 
[http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=2&scid=19&pid=1584](http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=2&scid=19&pid=1584)

he meant what wireless card (chip) do you have on your computer?

if you type (in terminal)
lsusb
or
lspci

one of them should show (among other things) information of your wlan card..

---

### Post by mellors.john on 2010-02-03
on my laptop i have an Atheros AR500 7eg wireless adapter... is that what you mean?

---

### Post by Sealbhach on 2010-02-03
Hi.

Try looking under System > Administration > Hardware Drivers. See if the  Atheros driver is listed under there. If so enable it and let us know what happens.

.

---

### Post by mellors.john on 2010-02-03
that worked like a charm!! unbelievable...simple...

it's amazing how much surfing and sifting I had to do to find this easy solution...

I am now on the internet, using ubuntu, freed from the tyranny of the windows operating system..

so let me thank all who responded to my post.. You're the greatest!..

and, to show my appreciation, here's a good stock tip (caveat: I own it so I am not unbiased):

  ARM Holdings .. the chip inside the Apple iPad is rumored to be based on an Arm design... Arm designed chips power the vast majority of smart phones as well... ARMH is the David to Intel's goliath....

I love linux!

---

### Post by mellors.john on 2010-02-03
thanks man.. that did it!

---

### Post by Sealbhach on 2010-02-03
Well done on getting connected. That's why there's such a buzz about Ubuntu - it makes things simple which were once difficult.

.

---

