---
title: "Changing screen resolution causes logout"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by resander on 2011-02-18
I need to experiment with Rosegarden, Piano Booster and other Linux music programs, so found an old PC with AMD Athlon 1.8GHz and a heavy DELL crt terminal that I will place next to the MIDI (piano) keyboard.

Made a dual-boot Windows XP & Ubuntu 10.10. 

In Windows mode I can choose resolutions from 640x480, 800x600 and 1024x768. That works. Windows installer sets the default to 800x600.

In Ubuntu mode the default set by the installer is 1024x768. This is too 
high for my wonky eyes and crt, but when I try to change to a lower
resolution (800x600 or 640x480) I can see a zig-zag pattern for about a
second and then the system pops up the login screen. After login the 
resolution is still 1024x768.

The zigzag pattern is taller for 640x480 than for 800x600. Another
observation: the refresh rate is shown as 87Hz that I think is high for 
an ancient crt like this.

How can I overcome this?

---

### Post by Keiran230 on 2011-02-18
The random logging out means that X (the graphical session) has crashed. This can be from a number of things.

Ubuntu 10.X does resolution settings weird in comparison to 9 and previous. It attempts to auto-detect your monitor, but sometimes does it incorrectly. There's a proper way to fix this using the xrandr command and some other command, but it's difficult.

The easiest way to fix this would probably be to generate an /etc/xorg.conf file, then manually edit its contents.

To do this follow these steps:
1. Stop X with **sudo service gdm stop**
2. Generate the xorg.conf file with **sudo X -configure**
3. Edit the file with **sudo nano /etc/X11/xorg.conf**
****It might generate the file in /etc/xorg.conf. If it does, type **sudo mv /etc/xorg.conf /etc/X11/xorg.conf**
****You are then in a text editor; look for the line containing the resolution and refresh rate, and change it.
4. Either type **startx **to start X again, or reboot with **sudo init 6**

If you completely screw up the xorg.conf file in the process, boot a live disk, mount your hard drive, then delete the xorg.conf file

---

