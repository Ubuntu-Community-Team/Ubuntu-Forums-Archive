---
title: "It says: Battery Has 5 Minutes Remaining. But Battery is full"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by SPazzo on 2010-06-23
So, I have a MSI Wind U123 netbook.  I just installed Ubuntu 10.04 and I love it!  There is just one tiny problem I'm having.  Whenever I unplug my laptop from AC power, I get a window popping up that says *"Laptop battery critically low.  Computer will hibernate very soon unless it is plugged in."*  And a little notification pops up that says that the laptop has 5 minutes until the power drains.

But when I click on the battery icon, it says that I have 4 hours of battery time remaining.  My battery is a six cell battery with 97.1% charge capacity.  I have no idea why it's saying that it's almost out of power.  That doesn't come up if I turn on my laptop after I unplug it.

Does anyone know why it's coming up or how I can disable it?

Cheers!

---

### Post by Windows Nerd on 2010-06-24
Does it actually go hibernate 4 minutes (or however many minutes it says it will in) after you unplug it, or does it just give you that phantom warning when you uplug it. If it does not actually hibernate, does GNOME squack at you when it **actually** has critical battery?

It might be a bug, once you tell me the behaiviour I will know for sure or not.

Scott

---

### Post by SPazzo on 2010-06-24
Nope, the battery has lasted longer than 4 minutes.  I haven't tried it for the full 4 hours yet to see if draining it might do something.  I'll try draining it and post the results back here...

Cheers!

---

### Post by Windows Nerd on 2010-06-24
If it actually does give you the "Critical Battery blah blah blah x minutes until hibernate blah blah..." warning, then it is likely a bug.

---

### Post by xtremesupremacy3 on 2010-06-24
I can confirm this is a bug, since I have it too, and funny enough, I have an MSI CR700.
I just ignore it lol

---

### Post by Windows Nerd on 2010-06-24
> **xtremesupremacy3 said:**
> I can confirm this is a bug, since I have it too, and funny enough, I have an MSI CR700.
I just ignore it lol
Sweet, did you report the bug in Launchpad?

---

### Post by MatthewPlanchard on 2010-07-01
There is a workaround for this issue.

If you open up a terminal and run gconf-editor, go to apps, navigate to gnome-power-manager, click on general, and then uncheck "use_time_for_policy", it will fix the warning messages.  Some people (myself included) were also having trouble with it automatically hibernating/suspending when unplugged, and this fixes that issue also.

Filling a bug is still a good idea, though.

---

### Post by SaintDanBert on 2010-12-20
> **MatthewPlanchard said:**
> 
... If you open up a terminal and run gconf-editor ...

There is another section, "thresholds" where you find the percentages and time intervals for "low power" and "critical low power" notification
and the corresponding actions.

Cheers,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2011-01-08
Folks who read this thread might benefit by looking at the package **battery-stats**. This simple daemon gathers data about your battery state into a text log file. A companion utility **battery-graph** included in the package will prep the log file and present a graph using gnuplot.

[indent]**Clarification:** The package is "battery-stats." It includes  both the data gathering and the graph creation utilities.
[/indent]
Enjoy,
~~~ 0;-Dan

---

