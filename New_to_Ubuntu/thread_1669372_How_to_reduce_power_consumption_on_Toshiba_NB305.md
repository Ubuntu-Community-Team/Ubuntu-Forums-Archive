---
title: "How to reduce power consumption on Toshiba NB305"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by vfrank on 2011-01-17
Greetings--

I've been using Maverick on my Toshiba NB 305 since early December 2010, and overall I'm really really pleased with it. I installed it from USB, I dual-boot from grub, and the current kernel is 2.6.35-24-generic. 2 GB RAM. 

I want to reduce power consumption/enhance battery life, so I installed powertop. Unfortunately many of powertop's suggestions can't be carried out by pressing the indicated key. And I have no idea how to enable the kernel configuration options suggested on the powertop site (e.g., CONFIG_NO_HZ). 

I've searched the threads quite a bit but still can't get a handle on things. Can anyone point me in the right direction?

Thanks!
Vic


[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]file:///tmp/moz-screenshot-2.png[/IMG]

---

### Post by vfrank on 2011-02-05
Bump

---

### Post by davidmohammed on 2011-02-05
there are various suggestions including how to use powertop on [this website]("http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption").

---

### Post by vfrank on 2011-02-11
Sorry for a possibly stupid question, but can I make these changes in a .config file, or do I need to compile a new kernel?

For example, from PowerTOP's FAQ:
CONFIG_NO_HZ
CONFIG_HIGH_RES_TIMERS
CONFIG_HPET
CONFIG_HPET_TIMER
CONFIG_CPU_FREQ_GOV_ONDEMAND
CONFIG_USB_SUSPEND
CONFIG_SND_AC97_POWER_SAVE
CONFIG_SND_HDA_POWER_SAVE
CONFIG_SND_HDA_POWER_SAVE_DEFAULT=3
CONFIG_TIMER_STATS
CONFIG_ACPI_BATTERY
CONFIG_CPU_FREQ_STAT
CONFIG_INOTIFY

---

