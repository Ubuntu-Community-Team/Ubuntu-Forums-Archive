---
title: "Fancontrol Application?"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by McRat on 2011-02-03
When I went to install the Fancontrol application from the Ubuntu software center, it says it's already installed (apparently a default app).

How do I find it to launch it?

All I'm really looking for is CPU core temps.

---

### Post by matt_symes on 2011-02-03
Hi

Install the (search for) sensors-applet in synaptic or at the terminal type

```
sudo apt-get install sensors-applet
``` 

Then add it to the gnome panel to get CPU temp readings. You might have to install lm-sensors.

Fancontrol is a daemon that runs in the background and has no direct user interface.

Kind regards

---

### Post by matt_symes on 2011-02-03
Hi 

Heres a screenshot attached.

Kind regards

---

### Post by HermanAB on 2011-02-03
Note that on some systems, these utilities don't work - YMMV.

---

### Post by McRat on 2011-02-03
Thanks y'all!  That should get me started!

Related question, is there a good app for CPU clockspeed?

---

### Post by matt_symes on 2011-02-03
Hi

Yes. CPU Frequency Scaling Monitor 2.30.0. 

Right click on panel->Add to panel->CPU Frequency scaling monitor.

You may also need to install this.

```
sudo apt-get install cpufrequtils
```

It assumes your CPU and kernel has that ability as in Hermans caveat.

Kind regards

---

