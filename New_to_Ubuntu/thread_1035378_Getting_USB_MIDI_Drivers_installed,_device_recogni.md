---
title: "Getting USB MIDI Drivers installed, device recognized"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by kbabl on 2009-01-09
I am using ubuntu for the first time and I am trying to get my M-Audio midisport 2x2 USB midi device working with the OS. I have installed the midisport-firmware package but the device is not being recognized and is not being powered. Looking for assistance with getting it working. Thanks

---

### Post by Michael.Godawski on 2009-01-09
hi,

can you please plug in the midisport and post the output of this terminal command
```

lsusb
```

---

### Post by Michael.Godawski on 2009-01-09
addendum:

found something on the german ubuntuforums which might be helpful:


[LIST=1]
[*]download the package fxload
[*]```
sudo apt-get install fxload
```
[*]download the midisport drivers:
[*][http://sourceforge.net/project/showfiles.php?group_id=87777&package_id=92666](http://sourceforge.net/project/showfiles.php?group_id=87777&package_id=92666)
[*]compile the drivers with
[*]```
./configure
```
[*]```
make
```
[*]```
sudo make install
```
[*]umplug and plug in the midisport again, should work now
[/LIST]
If you have question just ask.

---

### Post by kbabl on 2009-01-09
Thanks for the helpful suggestions. I found a tutorial that got it powered up. This was my first day using ubuntu and I am amazed at the supportiveness of the community. Cheers.

---

