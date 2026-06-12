---
title: "Yet another tablet"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by martin.burianjr on 2010-01-14
Hi there,
it seems tio me that every second ubuntu user has to have had a tablet issue (beautiful english, isn't it? pretty sure it's incorrect, but it sounds nice :-)). So here I am.
I followed a howto [here]("https://help.ubuntu.com/community/TabletSetupWizardpen"). I got the tablet working, pressure sensitive etc, but it completely ignores the bounds and settings in my xorg.conf! It works only in a small area of the screen, top left corner of the same aspect ratio as my monitor, but the area on te tablet sits in the bottom left corner, aspect ratio ok. I tried other settings in the xorg.conf, but they don't change anything. I should add that the configure script of the wizardpen package works ok and gives reasonable bounds...
Any ideas about what went wrong?

P. S.: here is my xorg.conf
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
EndSection


Section "InputDevice"
    Identifier "Tablet"
    Option "Name" "Tablet"
    Option "SendCoreEvents" "true"
    Driver "wizardpen"
    Option "Device" "/dev/input/tablet"
    Option        "TopX"        "0"
    Option        "TopY"        "0"
    Option        "BottomX"    "16300"
    Option        "BottomY"    "16300"
    Option        "MaxX"        "16300"
    Option        "MaxY"        "16300"
EndSection

Section "ServerLayout"
    Identifier "DefaultLayout"
    Screen "DefaultScreen"
    InputDevice "Configured Mouse" "CorePointer"
    InputDevice "Tablet" "SendCoreEvents"
EndSection

```Thanks!

---

### Post by Favux on 2010-01-14
Hi martin.burianjr,

It could be another driver, not the wizardpen, has your tablet.  We can look at the output of:
```
xinput --list
```
And your Xorg.0.log in /var/log/.  The Xorg.0.log will exceed the upload limit so right click on it and use Create Archive to compress it and then upload it with Manage Attachments.

---

### Post by martin.burianjr on 2010-01-14
Thanks for the hint, it's solved now.
I've overlooked some settings in the configuration file I created during the howto. This ment X created the tablet device twice, once from an fdi file and once from the conf. The first one happened later, so it had overriden the xorg.conf settings...and that was it. There were completely nonsense settings in the fdi which caused the behavior I described. So it took a simple edit and reboot to fix. Thanks though, your reply was pretty fast!
Martin

---

### Post by Favux on 2010-01-14
Hi Martin,

Nice work!

---

