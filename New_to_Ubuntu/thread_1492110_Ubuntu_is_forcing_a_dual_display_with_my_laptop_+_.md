---
title: "Ubuntu is forcing a dual display with my laptop + external monitor"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by Xenphor on 2010-05-24
I'm a linux noob. I installed xubuntu 10.04 through wubi and now my computer always  defaults to a dual display, even if I boot into Windows. Since this only  started happening since I installed Ubuntu, I'm thinking that there is  some option in there that is forcing a dual screen setup. Also, since  this happens even if I don't boot into Ubuntu, does that mean it's an  option at boot that is causing this? 

I tried going to the "Displays" panel but it showed only my external  monitor. When I've used other flavors of Linux or Ubuntu, I seem to have recalled it showing both my external and laptop monitor settings. I'm not sure where else I can look to disable this option. 

I'm unable to use my Fn+F4 to cycle the screens manually. 

I tried to generate an xorg.conf but couldn't find any option in there that I could possibly change.

---

### Post by sbergman on 2010-05-25
I found something similar with my laptop in 8.04 (when I still had one).

When in Linux, I would not be able to just plug in a monitor / projector and press the hotkey combination to have it appear... I had to restart the Xserver (ctrl+alt+backspace) and both monitors would then activate. If I then rebooted into Windows I'd find that the settings I applied when in linux would persist even in Windows.

I then just made the assumption that the settings regarding the extra monitor are saved elsewhere (perhaps in the BIOS?) and the OS reads those on startup.

So as a longshot, try starting your pc and when you get to the login screen, unplug the external monitor and try the ctrl+alt+backspace combo to restart your xserver

---

