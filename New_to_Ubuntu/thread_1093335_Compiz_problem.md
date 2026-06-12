---
title: "Compiz problem"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by hashashi on 2009-03-11
Hi everyone, 
I have installed ubuntu just yersterday. I have a vista preinstalled notebook with a nvidia graphic card. I activated the recommended nvidia driver manuel, and then installed compiz desktop effects and etc. Then i have chosen my preferences and activated cube effects and so on. When i pressed the key combination for these effects on desktop it didn't work. So i got the idea that the program was not running yet. 
Then i wrote into the terminal, "compiz", which i expected to start the application. Then it began checking some stuff which i didn't understand. 
then it got stuck somewhere.
Now comes the problem, after this i lost all window headers above all windows. The buttons for closing or maximizing  the windows, and the bar on which these butoons were supposed to be doesn't exist anymore. On some windows i can't write anything, i can't move windows because the header isn't there. I searched it in internet, and found some similar problems about ubuntu 7.0.4 and beryl, there were mentions about xorg but i don't know what it is and how to modify it, and this wasn't my case. Now i can only close the computer by pressing the power button and after restart, if i write it to terminal again, it does the same thing. 
I wrote a pretty long message, but i wanted to give as much clue as i can about the problem, sorry for bothering you. 
Could you please help me to make compiz run, and could you please tell me if it is the right way to run a program, by wrighting its name into the terminal:)?

---

### Post by Therion on 2009-03-11
First thing to check:

Open CCSM and make sure the plugin called **Window Decorations** is checked "ON".

If it is and you still don't have window borders open a Terminal and Copy the following into it:```
compiz --replace
```

If you have Compiz Fusion installed correctly, you don't need to start it; it will start automatically when you boot your computer.

---

### Post by bailbath on 2009-03-11
What version of Ubuntu?
What Nvidia card do you have?
Ian

---

### Post by hashashi on 2009-03-11
It's Nvidia Geforce 9600M GT 512 ram, i didn't install or activate any other driver for any other device on my computer (they just worked), but i had to activate only this one manuel, and ubuntu 8.10.

---

### Post by hashashi on 2009-03-11
I went to preferences at CCSM, there is a list of plugins. There is a plugin called decoration, which is enabled but there isn't any plugins called windows decoration nor enabled neither disabled. 
And i copied what you wrote into the terminal, the same thing happened again, no window headers, not beeing able to change windows... And by the way i installed, both the manager and the effects extension via this program manager to add or remove programs. I assume they have been installed correctly.

---

### Post by WakkiTabakki on 2009-03-11
This may be a problem related to the Nvidia drivers.
Try editing your xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```
and add the line
```
    Option         "AddARGBGLXVisuals" "True"

```
to the "Device"-section

Log out and log in again...

/N

---

### Post by hashashi on 2009-03-11
I edited xorg saved and closed, logged out logged in, nothing changed. I hit the default combination for cube, which i didn't change, ctrl+alt+down, and nothing happens. 
In the meanwhile i opened system monitor, in the list of processes i see, compiz, compiz-decorator, compiz.real all sleeping. Are they supposed to be sleeping or running?
Should i try again the code therion wrote after editing the xorg file?
Sorry for taking your time, but it's really annoying, not to get it work. I am not a very experienced computer user, but i want to work with multiple desktops, if it's possible.

---

### Post by Therion on 2009-03-11
To get the Desktop Cube working enable the following plugins (by checking the box next to them):

[INDENT]    * Desktop Cube 
    * Rotate Cube
    * Viewport Switcher (optional) - so you can rotate the cube with your mouse wheel.
    * Cube Caps (optional) - looks better.[/INDENT]

Next, increase the number of the virtual desktops to 4 by going into CCSM:

General Options/Desktop Size/Horizontal Virtual Desktop Size.  

Increase this setting to "4".  The other two options have to be left at 1.

Now you can move the Cube around with Ctrl+Alt+Left Mouse Button (hold them down).

---

### Post by oldos2er on 2009-03-11
You should reboot after changing xorg.conf.

 Check System, Preferences, Appearance, Visual Effects, make sure 'Extra' is checked.

---

### Post by WakkiTabakki on 2009-03-11
> **oldos2er said:**
> You should reboot after changing xorg.conf.
Since 8.04 (I think) XOrg restarts when you log out, so there should be no need. 


hashashi:
Did you try running gtk-window-decorator from command line?



/N

---

### Post by chamber on 2009-03-11
Check this post.

[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by hashashi on 2009-03-11
Thank you everyone,
The problem is solved, the cube works fine. By the way, i did xorg editing, it wasn't enough i guess, but after also making the desktop number 4, everything worked fine. Other commands for Compiz work now also, which didn't work before xorg editing. I am not sure which one solved the problem, both probably. Thank you for everything again.
Ps: Now i lost every sound, even the notification alerts, which i tested at the previous login, and were working perfect. I guess i am gonna find them somehow, but it is going to take me some time to get used to new os :)

---

