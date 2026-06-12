---
title: "cannot watch videos..."
date: 2009-01-10
forum: New to Ubuntu
---

### Post by ja660k on 2009-01-10
hey guys, 
as the title suggests i cannot watch videos, any videos except .flv (flash video )

but anything like .wmv .avi .mpg etc wont work, i can open them in vlc or whatever i use. 

it opens, plays a few seconds then the desktop shuts down(freezes).
i have not installed any drivers or whatever for video 

i only have apps to play them like vlc and what ubuntu comes with

any ideas?

i dont know what chipsets or gpu i have all i know is im using a compaq cq60-119tu laptop with ubuntu 8.04

---

### Post by taurus on 2009-01-10
If you have not installed any codecs, try them first.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by 2hot6ft2 on 2009-01-10
Well first thing would be to install the drivers for the graphics card in.
System>Administration>Hardware Drivers
select the one it recommends and it will download and install it.
It will require a reboot afterwards.

After the reboot go back to
System>Administration>Hardware Drivers
and make sure it's set to active, if not activate it. If it is go to
System>Preferences>Screen Resolution
and set the resolution and refresh rate

Then get the needed codecs for multimedia
The complete way
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Or the short way
Applications>Accessories>Terminal

```
sudo apt-get install ubuntu-restricted-extras
```

Then your password and Enter (your password will not be displayed)

It will fix that as well as other missing multimedia you haven't found out about yet.

When it gets to the agreement hit Tab then Enter to accept the Java agreement.

---

