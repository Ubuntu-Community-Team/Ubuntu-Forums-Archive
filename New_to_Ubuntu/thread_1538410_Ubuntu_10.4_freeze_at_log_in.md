---
title: "Ubuntu 10.4 freeze at log in"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by twonew on 2010-07-25
When I turn on my laptop, as the system gets to the log in screen my mouse will work.  Once the log in message appears, the mouse and keyboard will do nothing.  I cannot use ctrl-alt commands, type anything or get any mouse movement.  

This all seems to have started a couple of days ago, but in that instance there was a ICEauthority error message that is no longer appearing now. I turned the computer off then and did not turn it on again until tonight.

I have no idea what to do next, but I do know I really like Ubuntu vs Windows so need some help

---

### Post by Paddy Landau on 2010-07-25
I've done a quick Google on this problem, and it seems that somehow you've lost permission to access your own files.

[LIST=1]
[*] When you turn on your computer, you should be given the option to choose  which operating system to boot in. (If you have only Ubuntu, then it won't. To do so, press and hold the Shift key when you turn on your computer, and release when you see the menu.)
[*]Use your down-arrow to choose the second from the top (recovery mode) and press Enter.
[*]When you get a list of choices, scroll down to the last one (Drop to root shell prompt) and press Enter.
[*]Enter the following four commands (replace *twonew* with your actual Ubuntu username on your computer). Copy the commands carefully, and note the dot before [FONT=Courier New].ICEauthority[/FONT].
```
sudo  chown  *twonew*:*twonew*  /home/*twonew*
sudo  chmod  u+rwx  /home/*twonew*
sudo  chown  *twonew*:*twonew*  /home/*twonew*/.ICEauthority
sudo  chmod  u+rw  /home/*twonew*/.ICEauthority
```
[*]Type [FONT=Courier New]sudo reboot[/FONT] and press Enter.
[/LIST]
Let us know whether it works.

---

### Post by nathan.osborn1 on 2010-07-25
I have been expirenceing the same problem, but I think mine is from me messing around with the codes. I think I messed up giving something rights and thats pretty much when my stuff started freezing up. Good thing I just switched to Ubuntu....I just plan on reinstalling it to fix all my coding errors. Hope it works.

---

### Post by TimEnid on 2010-07-25
i experience this same thing, once in a while though.

---

### Post by linux18 on 2010-07-25
```

-choose recovery mode at grub
-drop to a root prompt
-type telinit 3 and login
-then type xinit
-when xinit starts type: metacity & - for ubuntu OR compiz & - if you have it OR flux/openbox & - if you have it OR fvwm & - for xubuntu
-then type gnome panel & -for ubuntu OR xfce4-panel & -for xubuntu
-lastly type nm-applet & -for networking

```

---

