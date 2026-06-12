---
title: "Compiz issue in intel 82845G/GL"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by migrate from windows on 2011-03-04
HI
I have ubuntu 10.10 installed in my old pc with intel 82845G/GL brookdale chipset. Though I have managed to workaround the blacklisting of the card by compiz. Iam not able to run compiz all I get is a black screen!! (I know may be thats why it was blacklisted... But I do read about people with the same card using compiz. So I guess there is something wrong with my xorg.conf

Section "Device"
      Identifier "Configured Video Device"
      Driver "intel"
EndSection
Section "Monitor"
      Identifier "Configured Monitor"
EndSection
Section "Screen"
      Identifier "Default Screen"
      Monitor "Configured Monitor"
      Device "Configured Video Device"
EndSection


Any suggestions like AccelMethod etc????? (how to know which accelmethod Im using right now?

---

### Post by Dutch70 on 2011-03-04
This may work for you. Just be sure to write everything down before you go into a tty.

Good luck & let us know how it works out for you.

1) Work in a tty (Control + Alt + F1). and remove the following

```
sudo aptitude remove compiz compiz-core
```

2) After that, reinstall/install the followings

```
sudo apt-get install compiz compiz-core fusion-icon emerald simple-ccsm
```

3) Back to the graphic environment (Ctrl + Alt + F7) and run Compiz Fusion Icon (Apps -> System tools -> Compiz Fusion Icon.

4) The compiz fusion icon should appear in your notification bar, there, right click -> Compiz options -> Indirect Rendering

5) Select Window Manager -> Compiz<

6) Run compiz icon at the start-up:

System -> Preferences -> Start up apps -> Add
Name: Compiz Fusion Icon
Command: fusion-icon -f
Comment:

7) Reboot

Once again in the desktop compiz should work properly. Configure it with

Code:

```
simple-ccsm
```

I did not write this, check here if you want to know who did.
[Intel 82945G Desktop Freeze]("http://ubuntuforums.org/showthread.php?t=1307001&page=3")

---

### Post by migrate from windows on 2011-03-04
I tried what u said ...when I right click the compiz fusion icon there is no compiz options or ...anything to do with indirect rendering?  so I tried to enable compiz still the same old story :-(

---

### Post by Dutch70 on 2011-03-04
> **migrate from windows said:**
> I tried what u said ...when I right click the compiz fusion icon there is no compiz options or ...anything to do with indirect rendering?  so I tried to enable compiz still the same old story :-(

If you've done everything correctly, when you right click the compiz icon "**in your panel**" you should get this list of options...

[I]Settings Manager
Emerald Theme Manager
Reload Window Manager
Select Window Manager 
Compiz Options        
Select Window Decorator 
Quit   [/I]  

Loose Binding & Indirect Rendering will come up when you hover your mouse over Compiz Options. 

If not, what are you getting?

Step #6 is a very important step, you can't just right click the icon in your menu & select "add to panel". It won't work. 
If, when you right click the icon, you're getting...
Launch
Properties
Remove from panel
Move
Lock to panel

You did not do #6 correctly!!!

---

### Post by migrate from windows on 2011-03-04
The compiz options is greyed out not selectable

---

### Post by Dutch70 on 2011-03-04
> **migrate from windows said:**
> The compiz options is greyed out not selectable

:( Truly sorry to hear that! 

AFAIK, it may run in an older version of Ubuntu. Mine ran fine in Hardy 8.04 without any workarounds. When I upgraded to 10.04 & 10.10, I had a time getting it to stop freezing my system. I Never tried 9.04 or 9.10.

---

### Post by migrate from windows on 2011-03-06
tried intel driver from ppa glasen ...a small change now xstarts but only cursor and background.....is this bump or any more ideas??

---

### Post by wep940 on 2011-03-06
I'm suprised you even get an X window - I would have thought you'd get dumped to the command line if you even got that far.  As far as I remember, the 845 is a problem - most people have to put either i915.modeset=1 or if it doesn't work then i915.modeset=0 on the boot line.  I would do the edit of the boot line from the grub menu and try this temporarily to see if it helps - remember to try the =1 first and if that doesn't help change it to the =0.  Since the edit is only for a single boot, if you find this helps you, post back and we can figure out which file needs to change in grub2.

---

