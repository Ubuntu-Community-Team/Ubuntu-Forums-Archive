---
title: "Help my graphics are worse after i install the right drivers what am i doing wrong?"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by rulitawyn on 2010-04-22
Ok I am really new to linux. I have been reading this forum for days now trying to find a soloution to my problem. I have found many topics similar to this one but they are all just different enough that i can't seem to get any effective resolutions to my problem.

heres the issue.

I have a nvidia Geforce 5200 installed (at least according to dxdiag when it was in a windows computer i got the card from a friend so i can be sure) when i first installed ubuntu the highest resolution i could get was 800x600 i wasn't surprised that i needed new drivers so i downloaded the nvidia drivers from the website and attempted to install. after struggling with that for several hours finally i heard about envyNG tried that and it installed a nvidia driver for me. ok great i think so i restart the computer and my resolution is 640x480 and thats the only mode i can get out of it. if i uninstall the driver it goes back to 800x600 but i know this card and monitor can do much higher than that. not to mention 800x600 is small enough to make using some windows difficult when the buttons to apply or accept are off the bottom of the screen.

i don't know much about using the terminal i have followed some instructions on how to fix similar issues with no success please anyone how can help i would greatly appreciate it

---

### Post by iver2435 on 2010-04-22
Have you tried going to "System" --> "Administration" --> "Hardware Drivers"?  There might be a driver there that you can use.

---

### Post by cgroza on 2010-04-22
You can install the drivers from System >> Administration >> Hardware Drivers. But make sure you unistal the drivers from the nvidia website.

---

### Post by realzippy on 2010-04-22
..with that old card I would suggest to install 10.04,since the nouveau driver (free driver for nvidia cards) is implemented in Lucid.Nouveau works fine even with those old nvidia gpus.Similar resolution problem was solved in this thread (anything else -*xrandr,adding xorg.conf modelines,deleting monitors.xml,vga cable* - did not work to increase resolution):

[http://ubuntuforums.org/showthread.php?t=1448196&page=10](http://ubuntuforums.org/showthread.php?t=1448196&page=10)

See post #94

---

### Post by _0R10N on 2010-04-22
I'm editing this. so I can remove the link I posted earlier. My bad! I'm sorry!

Kind regards!

_0R10N >>

---

### Post by _0R10N on 2010-04-22
To allow further help, tell us what you had tried so far.

_0R10N >>

---

### Post by realzippy on 2010-04-22
obsolete as prior post being deleted

---

### Post by RedRat on 2010-04-22
Can you run nvidia-settings with the EnvyNG driver installed? Perhaps the limitation might also be the monitor you have selected. Is the system correctly identifying your monitor and its capabilities. I run 8.04 and when I did this install via envyNG I had to manually select my monitor, a Samsung SyncMaster 191T. My system could not identify that monitor so I had to do that manually. You can do it via nvidia-settings.

Keep in mind that you need to run nvidia-settings using sudo:
```
sudo nvidia-settings
```

Check you synaptic to see if nvidia-settings is installed.

---

### Post by rulitawyn on 2010-05-11
sorry its taken so long to reply i have been away from the fourms trying other things and working on finals for school but now i have some extra time...

I just upgraded from karmic koala to lucid and my display (without driver) went from a max of 800x600 to 1024x786 with driver is it still 640x480 i have tried using the restricted drivers manager to install the nvidia 96 driver i have used the termanial to install the driver downloaded directly from nvidia and i have also tried using envyng to install the driver agter installing the driver and rebooting the computer I nolonger get the "your computer is running in low graphics mode" message but when it boots up it is in 640x480 rez. 

once the driver is insatlled using the nvidia driver display tool i have to click advanced and allow desktop panning just to be able to see the entire window because otherwise it wont draw the bottom of the pane. the monitor is reported as a standard crt monitor it is actually a nec accusync 90 but i have never known the type of monitor i was using to cause display issues before so i never would have thought that was the problem. 

in the nvidia driver tool the highest resolution i can set is 640x480 

on of the other forums i have read simmilar to this the user solved his problem by manually editing the xorg.conf and just adding the correct modes i tried duplicating his method and it had no effect. currently I am back to using no driver at all because having a resolution above 640x480 is significantly more important than having hardware 3d acceleration

---

