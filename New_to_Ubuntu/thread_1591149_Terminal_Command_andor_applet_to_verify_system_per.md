---
title: "Terminal Command and/or applet to verify system performances."
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Mobidoy on 2010-10-08
I like to know how my system runs.

Temperatures, Cpu speed scheme, fan speed etc etc.

Is there a list of commands that I can use to micro manage all that and/or apps/applets to monitor/modify it.

---

### Post by sandyd on 2010-10-08
> **Mobidoy said:**
> I like to know how my system runs.

Temperatures, Cpu speed scheme, fan speed etc etc.

Is there a list of commands that I can use to micro manage all that and/or apps/applets to monitor/modify it.
temperature.... 
```
acpi -t
```

cpu speed...
```
cat /proc/cpuinfo | grep "cpu MHz"

```
Theirs three main schemes - powersaving, ondemand, and performance.

---

### Post by psusi on 2010-10-08
The Gnome Sensors panel applet will show your temperature and fan speed if you install and configure the lm-sensors package.  And the cpu frequency scaling monitor applet will show and let you control your cpu frequency.

---

### Post by Mobidoy on 2010-10-08
> **psusi said:**
> The Gnome Sensors panel applet will show your temperature and fan speed if you install and configure the lm-sensors package.  And the cpu frequency scaling monitor applet will show and let you control your cpu frequency.

I have confirm that Lm-sensors is installed but, I cant find the Gnome Sencor Panel... Where should I look ?

---

### Post by psusi on 2010-10-08
> **Mobidoy said:**
> I have confirm that Lm-sensors is installed but, I cant find the Gnome Sencor Panel... Where should I look ?

Right click on the panel and choose add to panel.  Scroll down to "Hardware sensors monitor".

---

### Post by Mobidoy on 2010-10-08
lm-sensors is there has I have said, I removed it, re-installed it (from command line) but still, I cant find it when I try to add it ti the top bar (pannel). if I try sensors in command line, it works, if I try to set it up sudo sensors-detect it runs too, but, it is no where to be found in the top (or bottom) bar lol

---

### Post by psusi on 2010-10-08
Oh yea, you have to install the sensors-applet package.

---

### Post by SuaSwe on 2010-10-08
Conky is a lovely tool for system monitoring; don't think it can be used for modifying anything though, mind!

---

### Post by Mobidoy on 2010-10-08
> **psusi said:**
> Oh yea, you have to install the sensors-applet package.


Awesome, now I got it :) Only dont have the fan speed :)

Will look at Conky soon :)

---

### Post by Trandok on 2010-10-09
I would strongly suggest Conky. It's highly customizable and it can tell you basically anything about your computer, from system stats to the weather outside and so on.

---

