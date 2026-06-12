---
title: "Wireless MS mouse scrolling issues"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by garybrad on 2008-12-30
Hello
 On a dual boot system (XP and 8.10 Ubuntu (AMD 64 bit)- the scrolling wireless laser 5000 mouse scrolls way to fast. 
When Ubuntu is up and running- I can remove and reinsert the wireless receiver and the mouse scrolls ok- 3 lines per click- everything ok.
A restart- which defaults to Ubuntu 8.10- mouse still works ok (also on shutdown)
However- after booting to Windows XP and then restarting to Ubuntu- the mouse scrolls way to fast.

Note: after some research on the web- I modified the etc/x11/xorg.conf to add an input device as shown below
Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
 Option "CorePointer"
 Option "Device" "/dev/input/mice"
 Option "Protocol" "ExplorerPS/2"
 Option "Buttons" "9" 
 Option "ZAxisMapping" "4 5"
 Option "ButtonMapping" "1 2 3"
 Option "Emulate3Buttons" "false"
 EndSection


This worked fine without unplugging and reinserting the mouse receiver, however, after Win XP startup and then reboot to Ubuntu-- the same issue occured.
The xorg.conf did not show the previously added input device.
There is now another xorg.conf.20081230120506 -- presumably this is now the old one- it does have the input device correctly listed.

How can I get the correct input device in permanently??

Thanks

---

