---
title: "Meter for temps, processor, etc."
date: 2009-05-05
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2009-05-05
Hi. I use a dual boot and on my Windows side I have an program called Mobmeter. It gives me a little box with the CPU temp, CPU speed, HD temp, and battery charge/discharge in real time.

I was wondering if there is an app I could use here in Ubuntu that does the same thing.

---

### Post by llamabr on 2009-05-06
```
brock@hops:~$ apt-cache search temp speed battery
collectd - statistics collection and monitoring daemon
cpudyn - CPU dynamic frequency control for processors with scaling
powersaved - power management daemon
brock@hops:~$ 
```

---

### Post by nhasian on 2009-05-06
try:

```
sudo apt-get install sensors-applet
```

Then right click on your taskbar and say add to panel. Then select the Hardware Sensors Monitor.

---

### Post by emeraldgirl08 on 2009-05-06
> **nhasian said:**
> try:

```
sudo apt-get install sensors-applet
```

Then right click on your taskbar and say add to panel. Then select the Hardware Sensors Monitor.

It's nice but I have a need for only one taskbar. When I enable it it takes up a lot of space.

I'd like to try llamabr's suggestion. I was hoping it could be something that could be displayed like a screenlet app.

---

### Post by emeraldgirl08 on 2009-06-11
```
brock@hops:~$ apt-cache search temp speed battery
collectd - statistics collection and monitoring daemon
cpudyn - CPU dynamic frequency control for processors with scaling
powersaved - power management daemon
brock@hops:~$
```

What does this do? I'm dragging this thread back out b/c I have Jaunty running now and didn't want that long line of temps on my taskbar.

---

### Post by gradinaruvasile on 2009-06-11
Right click on the indicators, you must have a preferences option. Go to the sensors tab, untick that you dont need.

---

### Post by louieb on 2009-06-11
Conky looks neat. But I'm to lazy to set it up. If you want to try it there are some threads in the how to section. Also have seen conky setups posted in the cafe.

Because its easy to setup I use gkrellm. The repositories have gkrellm and about half dozen plug-ins for it. 

:D lol just knew you would not stay windows only for long.

---

### Post by emeraldgirl08 on 2009-06-11
lol Conky? Right click on indicators???

Guys I think I unknowingly walked into a new dimension here :D

What are these things??? What indicators are you talking about?

---

### Post by Johan-Steyn on 2009-06-11
Hi,

Have you checked out the screenlets (widgets)?

You can achieve the same thing as Mobmeter.

Please see Attached.

Regards,

JS
[IMG]file:///tmp/moz-screenshot-1.jpg[/IMG][IMG]file:///tmp/moz-screenshot-2.jpg[/IMG]
[IMG]file:///tmp/moz-screenshot.jpg[/IMG]

---

### Post by capnthommo on 2009-06-11
hi there
if you go to community cafe you will find recurring threads about conky.  people have posted their conky setups so you can choose one you like.
i think it's a good way to get system data, for example i have a continuous readout on my desktop like this (see attached)


it's worth taking a little time to explore this cos it can be really customisable.  and there are how tos as said in earlier posts
just a little recommendation - nothing more.  hope it helps
cheers
nigel

---

### Post by emeraldgirl08 on 2009-06-11
I like that Conky set up. I've seen the thread on it but was busy with other things.

I'll take a read sometimes. Anyone have an answer for that code I copied from llamabr?

---

### Post by louieb on 2009-06-11
gkrellm on my T30
[IMG]http://louboldt.com/p-gkrellm.png[/IMG]

---

### Post by emeraldgirl08 on 2009-06-11
```
apt-cache search temp speed battery
collectd - statistics collection and monitoring daemon
cpudyn - CPU dynamic frequency control for processors with scaling
powersaved - power management daemon

```

Okay guys. I'll ask again. What does this code do and how do I uninstall this if I entered this blindly into my Linux HD?

---

### Post by www.rzr.online.fr on 2012-07-08
did you figure out how to setup collectd sensor :


cat /etc/collectd/thermal.conf

<Plugin "thermal">
#Device "temp1"
Device "thermal_zone0"
IgnoreSelected false
</Plugin>


but kcollectd dont see it , how comes ?

-- 
[http://rzr.online.fr/q/sensors](http://rzr.online.fr/q/sensors)

---

### Post by wildmanne39 on 2012-07-08
Old thread closed.

---

