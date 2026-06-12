---
title: "power saving options in ubuntu 9.04"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by licketty_split on 2009-08-12
hey i just download ubuntu 9.04 for my laptop, and i'm wondering if there are any good applications or functions to control power consumption. It's a HP laptop, so the battery life's pretty crap already, so any advice would be much appreciated. 

thanks

---

### Post by mbsullivan on 2009-08-12
You should install powertop:

```
sudo aptitude install powertop
```

It is an application to monitor what applications are consuming the most power on your laptop, and it also allows you to sometimes shutdown unneeded services which consume power.

After installing it, run it as root from a terminal, and then sit and watch :)

Mike

---

### Post by LunaticHiatus on 2009-08-12
sudo aptitude install powertop

fixed that for you

---

### Post by licketty_split on 2009-08-12
thanks guys, very helpful. is there anyway to limit the CPU and graphics card power consumption? i need the laptop to last for a couple of hours, basically using the word processor (note taking for university).

---

### Post by mbsullivan on 2009-08-17
> thanks guys, very helpful. is there anyway to limit the CPU and graphics card power consumption? i need the laptop to last for a couple of hours, basically using the word processor (note taking for university).

The biggest way to limit the CPU power consumption is to make sure that you are using CPU frequency scaling. The easiest way to monitor this, probably, if you're running Gnome is with the applet:

```
(Add to Panel -> CPU Frequency Scaling Monitor)
```

The "ondemand" CPU governor is what you're looking for to save battery life.

There's no real way to save graphics card power consumption that I know of. Make sure that your screen brightness is turned down, that will save some battery life. 

Also, integrated wifi cards are a huge battery drain, which might come as a surprise. If you're not using a wireless network, turn off your wireless network card. It will greatly extend your battery life.

Cheers!
Mike

---

