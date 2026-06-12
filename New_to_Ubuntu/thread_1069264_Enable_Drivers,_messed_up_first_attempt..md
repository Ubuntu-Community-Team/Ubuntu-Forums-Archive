---
title: "Enable Drivers, messed up first attempt."
date: 2009-02-13
forum: New to Ubuntu
---

### Post by jono2009 on 2009-02-13
I have installed Ubuntu 8.10 on a friends Laptop as well as my own PC and I only realized yesterday that his Drivers were not correctly installed. This was due to the fact he was unable to hear any sound from his external speakers.

I opened System/Administration/Hardware Drivers and on find nothing installed( keep in mind I attempted to install them 3days before and unknowingly failed), the Hardware Drivers page blank and "Enable button" non-functional. Is it possible to start process again.

Thank you for any help from two noobs.
       :popcorn:

---

### Post by geirha on 2009-02-13
Check all the volume controls, might be one of the needed ones are just muted or set all the way down.

Also see if you find the laptop model at [https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops) and see if mentions any issues with the audio on that model (if it is listed)

---

### Post by jono2009 on 2009-02-13
> **geirha said:**
> Check all the volume controls, might be one of the needed ones are just muted or set all the way down.

Also see if you find the laptop model at [https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops) and see if mentions any issues with the audio on that model (if it is listed)


geirha thanks for helping,

I have checked the volume control/preferences, everything ok. My mate has dual both and M/Soft sound ok. 

The problem I have, is I need to reinstall the Hardware Drivers again. Currently the Hardware Drives page is blank and "Enable button" non-functional, I need to be able to reactivate Hardware Drivers all other again.:(

---

### Post by geirha on 2009-02-14
What audio controller does it have?
```
sudo lshw -class multimedia
```

Are you able to select the audio controller in System -> Preferences -> Sound?

Only way to get the option to install any proprietary drivers back, is to uninstall it. I doubt that will have any effect, but if you still want to try, you'll need to figure out what the package with that driver is called. A google search on the output of lshw or lspci's listing of the audio controller may help on that.

---

### Post by jono2009 on 2009-02-14
> **geirha said:**
> What audio controller does it have?
```
sudo lshw -class multimedia
```

Are you able to select the audio controller in System -> Preferences -> Sound?

Only way to get the option to install any proprietary drivers back, is to uninstall it. I doubt that will have any effect, but if you still want to try, you'll need to figure out what the package with that driver is called. A google search on the output of lshw or lspci's listing of the audio controller may help on that.


I'm seeing my mate Gordon in a few days time and I'll try all of you have suggested. Will post as soon as possible with the results. 

Till then, Cheers.

---

