---
title: "Keyboard quick keys not working on kubuntu... ..."
date: 2010-02-15
forum: New to Ubuntu
---

### Post by techno-mole on 2010-02-15
Hello.

I have a minor issue with my kubuntu system.

I use a genius keyboard (model - kkb 2050) like a lot of keyboards it has various quick keys (short cut keys) for adjusting the volume, launching the browser and e-mail applications etc, but for some reason not all the keys are working.

I can use the volume up and down buttons and the volume will adjust fine, if I have firefox open the back and forward keys on the keyboard work, but the keys to launch the media player, and stop and play music dont work (nothing happens when I press them, the same goes for the browser, e-mail and calculator keys, along with the keys to put the system to sleep and wake it up etc.

If I run xev in a terminal and press the keys that dont work I get an output, for example pressing the key to launch the web browser gives me - ```
KeyRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x13c, subw 0x0, time 35909648, (-408,237), root:(256,259),
    state 0x10, keycode 180 (keysym 0x1008ff18, XF86HomePage), same_screen YES,                                                               
    XLookupString gives 0 bytes:                                       
    XFilterEvent returns: False  
```
the XF86HomePage is the key to launch the browser.

I am using kubuntu at the moment, but this has never been an issue when running ubuntu.

I have googled it and tried setting the keys up using xmodmap, but had no luck, and I cant find anything that allows me to adjust the keys in the system settings.

I have updated kde to version 4.4 (I think its 4.4) any ideas as to whats wrong would be appreciated, I know its not a major issue, but its one of those little niggling things.

cheers.

---

### Post by techno-mole on 2010-02-16
well i am no further along than i was.

I have changed the keyboard layouts in the system settings, and found my keyboard model, but the keys still don't work.

I have also tried keytouch and still no joy, I'm at a loss as to why my keyboard doesn't work as it should, especially when I can run ubuntu (gnome) and the keys will work with out any hassle.

---

