---
title: "HELP! xorg.conf problem"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by hellodoggie on 2009-02-13
Hello

I followed a tutorial on the internet to try to get the back button on my mouse working. I restarted, and my resolution now is low.  How do I get my original xorg.conf back?  I forgot to back it up.

I replaced the inputdevices section with this code

Section "InputDevice"
Identifier "Configured Mouse"
Driver "evdev"
Option "Name" "Logitech USB Gaming Mouse"
Option "CorePointer"
# Option "Device" "/dev/input/mice"
# Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5 6 7 8"
Option "Emulate3Buttons" "true" 
EndSection

---

### Post by Rokurosv on 2009-02-13
You could try using 
```
sudo Xorg -configure

```
but make sure you've killed the X server, ctrl+backspace twice until you're in a terminal and then login, then sudo init 3 and run that command.
If you were using nvidia drivers and the drivers don't get added to xorg use nvidia-xconfig to modify the file.

---

