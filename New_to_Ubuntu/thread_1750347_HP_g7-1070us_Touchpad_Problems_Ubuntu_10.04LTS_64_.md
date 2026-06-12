---
title: "HP g7-1070us Touchpad Problems Ubuntu 10.04LTS 64 bit"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by wildwackyactionbike on 2011-05-05
:-k
For the life of me I can't seem to find a fix for this. I'm running 10.04LTS 64 bit on an HP Pavillion g7 laptop. The problem is that when I type, I will occasionally hit the tremendously large touchpad, it does tap-to-click and sometimes it really messes things up for me. I just want the touchpad DISABLED. Hopefully I can find a solution which will have it disabled at startup? I use a logitech wireless mouse, so I don't need the touchpad.


Things I've tried: 
-Tried disabling via touchpad on/off button.

-Downloaded GSynaptics from the Ubuntu Software Center.

-Tried running GSynaptics(among many other touchpad config tools) and get an error, "GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics" 

-Created xorg.conf(as it wasn't present before), added the default information per some other forums, adjusted the config file accordingly. Tried running GSynaptics again, nothing still.

-Tried running ```
sudo synclient TouchpadOff=1
```
, got "Couldn't find synaptics properties. No synaptics driver loaded?"

-Proceeded to try to hunt down driver on the internet, no luck. Tried Hardware Drivers, no luck.


So, at this point, I'm stuck. ANY help? Anyone else have this model and a similar problem?

---

### Post by wildwackyactionbike on 2011-05-05
Still looking scrupulously for a solution to this.

One thing seems consistent: Solutions seems to vary from brand-to-brand and model-to-model, not to mention the 32 bit vs 64 bit consideration. Yet, in the end, I'm finding more often than not  the vast majority of threads have come to dead ends with the same or very similar issues regarding the touchpad.

Btw, didn't mention before, but I have tried touchfreeze and it did not work either. 

Just tried to change settings in gconf-editor(desktop>gnome>peripherals>touchpad). Set tap_to_click to "False" and disable_while_typing to "True".

Still no dice. 

](*,)

---

### Post by wicasa71 on 2011-06-19
I have the same machine with the same problem.. I did however find you can disable and re-enable via the command line. 

First find out if you're touchpad is recognized by typing in the command line:


xinput list

See if  PS/2 Synaptics TouchPad is listed and what id has been assigned. 

Once you have the id number you can type in 


xinput set-prop 13 "Device Enabled" 0
 To disable it or 

xinput set-prop 13 "Device Enabled" 1
To enable.

It's quick and dirty but it works!! I haven't written a script or anything for it, possibly a script for a shortcut key would be good. As soon as I have one written I will post it for you.

---

### Post by jbrucek on 2012-02-22
Thank you wicasa71.
Just what I was looking for!

---

### Post by WA4MOE on 2012-04-17
I have my HP Probook 4530s 64 bit with Ubuntu 0.04LTS installed , and also need to disable touchpad. I applied both the disable and enable commands and there is no response to either one. I have problems while typing that teh cursor moves all over randomly as soon as any minor touch on the touchpad.
 
Please help ......
Thanks
Moe

_________________________________________________________


> **wicasa71 said:**
> I have the same machine with the same problem.. I did however find you can disable and re-enable via the command line. 

First find out if you're touchpad is recognized by typing in the command line:

xinput list
have the id number you can type in 


xinput set-prop 13 "Device Enabled" 0
 To disable it or 

xinput set-prop 13 "Device Enabled" 1
To enable.

It's quick and dirty but it works!! I haven't written a script or anything for it, possibly a script for a shortcut key would be good. As soon as I have one written I will post it for you.

---

