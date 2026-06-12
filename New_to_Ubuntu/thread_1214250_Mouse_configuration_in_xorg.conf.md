---
title: "Mouse configuration in xorg.conf"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by Phlex_de on 2009-07-15
I would like to have my mouse behave like I am used to it in windows and got some extra buttons to work with this:
```
Section "InputDevice"
       Identifier "Configured Mouse"
       Driver "mouse"
       Option "Name" "Razer Diamondback Optical Mouse"
       Option "Device" "/dev/input/mice"
       Option "CorePointer"
       Option "Resolution" "1600"
       Option "Buttons" "9"
       Option "Protocol" "ExplorerPS/2"
       Option "ZAxisMapping" "4 5"
       Option "ButtonMapping" "1 2 3 6 7 8 9"
       Option "one page back" "4"
       Option "one page forward" "5"
EndSection
```

With the code above Back and Forward in my browser is bound to buttons 6 and 8 (> Picture). I want them to to be 7 and 6. 
Clicking with my middle button (3) opens links in the background but does nothing when I click anywhere else. Is there a scroll modus I could bind to it? 
Last button was on-the-fly-sensitivity in windows, but I guess that's not possible in ubuntu. (Didn't use it often anyway.)

Can you help me to set it up?

Are there other things I could bind to the mouse? Like starting a gnome-terminal on button 8 or showing the desktop?

[IMG]http://img213.imageshack.us/img213/931/diamondback.gif[/IMG]  (This is not related to the numbering in org.conf. It's just how I would number them and I think it is similar to the windows drivers.)

---

### Post by AndThenWhat on 2009-07-16
I think there is a way to do that in the Compiz Config Settings Manager (Under the Commands Section). You just have to bind buttonx, where x is the mouse button number, to a command.

---

