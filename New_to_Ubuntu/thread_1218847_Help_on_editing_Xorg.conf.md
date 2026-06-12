---
title: "Help on editing Xorg.conf"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by AjShare on 2009-07-21
I have installed Ubuntu 9.04 and the resolution available at the display is 960x600 which is not the right one. I have read a lot of threads about editing Xorg.conf. This is how my Xorg.conf looks like
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

What can you infer from this?

and the command "sudo dpkg-reconfigure -phigh xserver-xorg" gives the following output
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090721131111
Is the problem with my motherboard?..I have  AMD64 on ASUS K8S-MX motherboard.

---

### Post by mthalis on 2009-07-21
I think this will help you.
[http://ubuntuforums.org/showthread.php?t=156243](http://ubuntuforums.org/showthread.php?t=156243)

---

