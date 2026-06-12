---
title: "Touchpad Preferences wont save my pref's"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by steve228 on 2010-03-21
Ok I have a heavy hand when I type.  I hate the touchpad being able to "Tap" instead of clicking.  Everytime I am typing something I hit the touchpad and wind up clicking something.  

Anyways I went Under System -> Preferences -> Touchpad and disabled "Enable Tapping" and it works! but only for a few minutes or until the system reboots :-( ... 

_**Is there a configuration file that I can just type into that automatically disables the tapping for me?**_

My system(in case it matters):
> Distro:  Ubuntu 9.10 Karmic Koala
Kernel:  2.6.31-20-generic-pae

Thanks in advance :-) ... This is a great forum BTW I love it here.

---

### Post by quixote on 2010-03-22
I hate (hate, hate, hate!) tap to click too.  In Ye Olde Days you had to edit synaptic's config file.  This is what my notes from back then say: 

list touchpad parameters
```
synclient -l       *("l" as in "list")*
```

Changes can be made if SHMConfig is enabled in  /etc/x11/xorg.conf
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
**        Option          "SHMConfig"             "on"**
EndSection
```

Then, to change one of the synaptic touchpad variables:
```
synclient MaxTapTime=180
```
That changes the tap time interval so it no longer registers as tap to click.  Or something like that.  It's been a while and this is from oldish notes....  You can change any of the variables you see when running "synclient -l" the same way.  Running "man synclient" (without quotes) brings up the manual pages, which aren't wildly useful but they're better than nothing.

---

