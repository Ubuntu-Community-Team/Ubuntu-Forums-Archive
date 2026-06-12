---
title: "refresh rate question"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by interceptorV8 on 2008-12-05
since i've gotten my monitor's resolution to 1920x1200, it looks great, but i noticed a LOT of flicker when watching the movie: Alien.  my max refresh rate is limited to 50Hz.  the specs for my monitor list the h/v frequency at 30 83kHz / 56 75Hz.   

my xorg file doesn't look anything like what others look like:  

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection



how can i fix this?

---

### Post by stonecoldjha on 2008-12-05
well, i don't understand that gobble-de-gook but,there is one thing that i can suggest if yours is an nvidia graphics card.install "nvidia-settings" using synaptic(i assume that you already have the driver installed).type in a terminal: **sudo nvidia-settings**,go to the resolution,choose the appropriate one,then go to the refresh rate and change it to something like 75Hz,click apply,and then click on "save to x configuration file".i believe you would have to restart to get the changes effected.

---

### Post by stefangr1 on 2008-12-05
> **stonecoldjha said:**
> well, i don't understand that gobble-de-gook but,there is one thing that i can suggest if yours is an nvidia graphics card.install "nvidia-settings" using synaptic(i assume that you already have the driver installed).type in a terminal: **sudo nvidia-settings**,go to the resolution,choose the appropriate one,then go to the refresh rate and change it to something like 75Hz,click apply,and then click on "save to x configuration file".i believe you would have to restart to get the changes effected.

What kind of movies are you watching, and what video card do you have?

Maybe, like the above sais, you don't have the drivers of your vc installed?

I had something similar when I bought a 1920x1200 display, my video card nvidia fx5200 just couldn't do it.

---

### Post by interceptorV8 on 2008-12-05
> **stefangr1 said:**
> What kind of movies are you watching, and what video card do you have?

Maybe, like the above sais, you don't have the drivers of your vc installed?

I had something similar when I bought a 1920x1200 display, my video card nvidia fx5200 just couldn't do it.



i have a geforce 7300 gs.  
a few days ago i downloaded envy to get the proper nvidia drivers since synaptic package manager would never allow me to download them (yet it would give me the restart icon in my panel afterwards)

---

### Post by interceptorV8 on 2008-12-05
> **stonecoldjha said:**
> well, i don't understand that gobble-de-gook but,there is one thing that i can suggest if yours is an nvidia graphics card.install "nvidia-settings" using synaptic(i assume that you already have the driver installed).type in a terminal: **sudo nvidia-settings**,go to the resolution,choose the appropriate one,then go to the refresh rate and change it to something like 75Hz,click apply,and then click on "save to x configuration file".i believe you would have to restart to get the changes effected.



hmm, well now, the nvidia x settings have the refresh rate set at 60 Hz while the "screen resolution" under "system">"preferences" has 50 Hz and a NEW option: 101 Hz

AND when i try to save the "x configuration file" in nvidia x settings, i get: "Failed to parse existing X config file '/etc/X11/xorg.conf'!"

---

