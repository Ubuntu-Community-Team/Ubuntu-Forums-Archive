---
title: "Put on High Performance"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by Hagumi on 2009-12-20
Hello, I'm a windows vista user who recently switch to ubuntu 9.10

In windows there are three power options; high performance, balanced, and power saver.  I'm wondering is there anything equivalent to that in ubuntu?  I'm really just interested in runing ubuntu in high performance mode.  If there is such a way, how can I automatically do that in login?

I've tried google and searching the forum, but I didn't find anything useful.

-Thanks

---

### Post by Temposs on 2009-12-20
Do you know the specifics of what kinds of differences there are in the Windows Vista performance steps?

If they're changing the power settings, you can change that stuff in System->Preferences->Power Management. You can change things like spinning down the hard disk and changing the brightness settings, which will certainly affect the performance vs. power savings.

---

### Post by Hagumi on 2009-12-20
Well, the higher your performance, the lower it is for your energy saving.

high Performance: low energy saving, high performance
balanced: 50/50
power saver: high energy saving, low performance

I don't care about saving battery time or anything like that, I just want ubuntu in a "high performance mode", if there is such a thing.  The power management does changes the power settings, but it does not change the performance setting.

---

### Post by scorp123 on 2009-12-20
> **Hagumi said:**
>  I'm really just interested in runing ubuntu in high performance mode.  On Ubuntu the default is "On Demand", e.g. it will run with max. CPU speed if thinks it has to. That should be OK for most people.

You can of course manually put it to max. performance ... but I honestly fail to see the point? You only shorten the lifetime of your system that way.

I assume you use GNOME? There is a CPU applet that you can drag & drop to your top panel: Right click > Add to panel ... then check if it's there in the available applets.

If you click on that CPU applet it will allow you to manually select the current mode it works under. Default will be "On Demand". BTW, manually selecting a different mode does not always work on all systems.

---

### Post by Temposs on 2009-12-20
Ah yes, that "CPU Frequency Scaling Monitor" applet does look like exactly what Hagumi wants.

---

### Post by gradinaruvasile on 2009-12-20
> **Hagumi said:**
> Hello, I'm a windows vista user who recently switch to ubuntu 9.10

In windows there are three power options; high performance, balanced, and power saver.  I'm wondering is there anything equivalent to that in ubuntu?  I'm really just interested in runing ubuntu in high performance mode.  If there is such a way, how can I automatically do that in login?

I've tried google and searching the forum, but I didn't find anything useful.

-Thanks

Ubuntu has integrated CPU frequency scaling monitor/governor - the CPU will run on lowest speed(step) when idle or not loaded, (cooling better and consuming less power) but when needed it will throttle up to full speed. Not noticeable in my opinion. You can set it to full speed all the time, but no visible difference in my experience.

Also, the video cards (usually laptops) that support speed stepping will be kept on lowest speed to cool better. If you have laptop with a card that has the option to change this setting, do not do it - you *might* burn your card if you are using it for gaming for long periods and dont let it cool when idle. Maybe i am a bit paranoid about this as i had a Nvidia NVS 135M card on a Dell D630 that burned out, but i havent played any games on it neither did graphics intensive operations - turned out it was design flaw that caused it.
For desktops, you can set it to max speed, as usually there are no problems with cooling.
This setting is noticeable if you are using compiz screen compositing with advanced effects like wobbly windows, fishes in the cube etc - it takes a while to speed up the card resulting in occasional "hiccups".

---

### Post by Hagumi on 2009-12-20
Thank you all. The CPU Frequency Scalling Monitor was exactly what I'm looking for

---

### Post by twright on 2009-12-20
> **Hagumi said:**
> Thank you all. The CPU Frequency Scalling Monitor was exactly what I'm looking for
Though actually *real *performance should probably be better in On demand mode because of the issue of cooling - there is absolutely no point in the cpu running the max no. of instructions per second when there are actually much fewer to do most of the time (benchmarks should tell you the same).

---

### Post by gradinaruvasile on 2009-12-20
> **Hagumi said:**
> Thank you all. The CPU Frequency Scalling Monitor was exactly what I'm looking for

You can install an applet and add it in your taskbar to see the CPU frequencies/change the governors in real time. Open a terminal (applications > accessories > terminal) and type:

```
sudo apt-get install gnome-cpufreq-applet
```

press enter, type in your password, enter again.
Then right-click on your taskbar, click "add to panel", select "CPU frequency scaling monitor", click add. If you have multi core system, add a monitor for each core, then right click on the applet select preferences and select there your CPU core (0,1,etc) - for typical 2 core system in one applet set cpu0 in the other cpu1. The scaling is applied for each core separately, you can have one core at say 800 MHz and the other at 2.0 GHz - this is an example, it varies depending on the CPUs scaling capabilities.

---

