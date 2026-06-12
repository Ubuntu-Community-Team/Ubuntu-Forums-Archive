---
title: "Gnome Vs KDE Power Management - CPU frequency"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Dodge on 2009-11-02
Hi guys,

Newbie here - I'm trying to decide between KDE and Gnome on my Eee PC and one thing I can't seem to find out how to control is the power profile when on mains and battery with regard to CPU frequency using Gnome.

In KDE's power management, I can select which profile I'm using depending on whether it's on mains or on battery, if the battery is low and if it's critically low.  I can select any one of the 'On Demand', 'Performance', 'Power Saving' etc. for each situation and it automatically controls it.

In Gnome however, I can manually select these things with the CPU applet (which works fine), however I'd like it to automatically switch to 'Power Saving' for example when on battery, and 'Performance' when on mains.

Any assistance appreciated.

Dodge

---

### Post by duanedesign on 2009-11-02
Try a script like:

```
#!/bin/bash
if on_ac_power; then
# Reset back to normal settings
echo "**governor**" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo "**governor**" > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
else
# Turn on aggressive power savings
echo "**governor**" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo "**governor**" > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
fi

```
Just change the word **governor** to performance, powersave, ondemand or conservative, depending on which one you want for battery and ac. You can check your particular available settings.

```
cat  /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```

To use this script on Hardy/Jaunty/Karmic, name it 99-savings and use:

```
sudo install 99-savings /etc/pm/sleep.d
sudo install 99-savings /etc/pm/power.d
```


for more detail see sdennie's post:
[http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)

Also you might look at [laptop_mode_tools]("http://manpages.ubuntu.com/manpages/intrepid/man8/laptop-mode.conf.8.html").

---

