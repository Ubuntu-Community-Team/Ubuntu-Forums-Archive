---
title: "second monitor using nvidia config"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by DarinB on 2011-07-05
I got an external monitor to work with 10.04 nvidia config an hp compaq v6000 laptop. 
it is set to separate x screen when I click the external monitor in the config 
i see it has the option right of left of above below and absolute. 
All I want is a mirror of my laptop desktop not a separate screen. 
that way all my icons appear on the external monitor...
I have tried using the twin monitor but that seems to make both the laptop screen and the external monitor connect together any Ideas how I can mirror this using the nvidia config....And what does the choice absolute mean?

---

### Post by seawolf167 on 2011-07-06
Can you select to "mirror" or "clone" the displays from System -> Preferences -> Monitors? There should be a checkbox somewhere near the mid-left edge if I'm not mistaken.

---

### Post by DarinB on 2011-07-07
I am using the proprietary drivers for nvidia and the monitors tool does not work. It asks to use the nvidia config application. And there is no option for mirror or clone. only seperate x or twin any ideas???

---

### Post by BicyclerBoy on 2011-07-07
If the option does not exist in the nvidia-settings then this may work..

In your /etc/X11/xorg.conf file , device section..
Option "TwinView"
Option "TwinViewOrientation" "Clone"


or from terminal
nvidia-xconfig --twinview
nvidia-xconfig --twinview-orientation="Clone"

It may be a "clone" requirement that both screens have the same resolution (real or virtual).

---

### Post by Grenage on 2011-07-07
> **DarinB said:**
> I am using the proprietary drivers for nvidia and the monitors tool does not work. It asks to use the nvidia config application. And there is no option for mirror or clone. only seperate x or twin any ideas???

Select the *X server Display configuration* tab.
Click on the monitor.
Click on *position*.
Select *clone*.

Job done. ;)

---

