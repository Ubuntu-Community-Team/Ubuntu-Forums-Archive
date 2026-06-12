---
title: "How to get Logitech G5 back button working..."
date: 2009-02-26
forum: New to Ubuntu
---

### Post by hellodoggie on 2009-02-26
How to get Logitech G5 back button working...?

I tried looking at Ubuntu hacks book
but I don't know what Zaxis means

Hack 47. Configure Multibutton Mice
  

Seven buttons, a tilt/scroll wheel, and who knows what else? Find out how to put all those bells and whistles to good use. 

Gamers love mice with more buttons than the Space Shuttle because the extra buttons can be mapped to provide quick access to common functions, but getting them working under Linux can be a bit tricky.

Open the Xorg configuration file at /etc/X11/xorg.conf in a text editor (for example, using the command sudo vi /etc/X11/xorg.conf) and look for a stanza labelled InputDevice. If your computer is a laptop with a touchpad, it may have several InputDevice enTRies, so make sure you find the one that refers to your mouse. If it was configured automatically by Xorg, it will probably look something like this:

Section "InputDevice" 
    Identifier   "Configured Mouse" 
    Driver        "mouse" 
    Option        "CorePointer" 
    Option        "Device" "/dev/input/mice" 
    Option        "Protocol" "ImPS/2" 
    Option        "ZAxisMapping" "4 5" 
    Option        "Emulate3Buttons" "true" 
EndSection


Start by changing the Protocol value. The ExplorerPS/2 driver supports more devices than the older ImPS/2 driver, so substitute this line:

    Option        "Protocol" "ExplorerPS/2"


Since your multibutton mouse almost certainly has a middle button, you don't need the Emulate3Buttons option anymore, so delete it.

Unfortunately, there is no way for your computer to automatically determine the number of buttons available on a mouse, so you need to add an option that explicitly tells Xorg how many it has. It's obvious that you need to count all the actual physical buttons on the mouse, but remember that you usually need to add three more: one for clicking the scroll wheel, one for scroll-up, and one for scroll-down. A typical scroll mouse with two main buttons on the top, two on the side, and a scroll wheel actually has seven buttons as far as the driver is concerned, so add a line like this:

    Option        "Buttons" "7"


Next, map the action of the scroll wheel to virtual buttons using the ZAxisMapping option. In the case of a simple scroll wheel that moves only up or down, you can assign two values, which are associated with negative (down) and positive (up) motion, respectively:

    Option        "ZAxisMapping" "4 5"


Some mice have a scroll wheel that also rocks from side to side, and some even have two scroll wheels, in which case you can add mappings for negative and positive motion in the second axis:

    Option        "ZAxisMapping" "4 5 6 7"


Unfortunately, you may find the second scroll direction isn't recognized by Xorg at all because there is currently no standard for defining how mice should encode horizontal scroll data when it's transmitted to the driver. Even if it is recognized, you may find the rocker or second scroll wheel moves in the opposite direction to what you expect, so you may need to reverse the third and fourth values.

Some browsers such as Firefox are hardcoded to use buttons 4 and 5 as shortcuts for "back" and "forward," but because some wheel mice report wheel-up and wheel-down as the fourth and fifth button events, respectively, you may need to do some extra work to use the side buttons as back and forward. You can remap the reported button events by calling xmodmap:

xmodmap -e "pointer = 1 2 3 6 7 4 5"


The xmodmap command will need to be run each time you log in to GNOME, so go to SystemPreferencesSessionsStartup Programs and put in the whole line; then compensate for the offset button values by using a modified ZAxisMapping line in /etc/X11/xorg.conf:

    Option       "ZAxisMapping" "6 7"


One final option you can configure is mouse resolution. Many multibutton gaming mice run at very high resolutions to enable accurate targeting, but you may find that it throws off Xorg's response curve. In that case, it may help to add a Resolution option in dpi (dots per inch):

    Option       "Resolution" "2400"


Once you have made all of these changes, your mouse configuration will look something like this:

Section "InputDevice" 
    Identifier   "Configured Mouse" 
    Driver       "mouse" 
    Option       "CorePointer" 
    Option       "Device" "/dev/input/mice" 
    Option       "Protocol" "ExplorerPS/2" 
    Option       "Buttons" "7" 
    Option       "ZAxisMapping" "4 5" 
EndSection


To apply changes, you need to restart Xorg. The easiest way to do so is to log out of your current session and then press Ctrl-Alt-Backspace, which will kill Xorg and force GDM to restart it (if GDM doesn't restart it, log in at the console and run the command sudo /etc/init.d/gdm restart).

Log back in and launch xev, the X EVent reporter, and click each button and scroll the scroll wheel in both directions. Each event will cause a button number to be reported in the terminal. If everything went as planned, each button will report a different button number.

---

### Post by Xiong Chiamiov on 2009-02-27
Take a look at [btnx](http://ubuntuforums.org/showthread.php?t=455656).

---

