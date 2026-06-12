---
title: "numlockx"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by DarinB on 2009-11-28
how do i get numlockx enabled in Jaunty, the option in keyboard for "Default numlockx not present 
i did add numlockx via synaptic

> Enabling Numlock in Jaunty

System -> Preferences -> Keyboard -> Layout -> Layout Options -> Miscellaneous compatibility options -> turn on "Default numeric keypad keys" 

---

### Post by DarinB on 2009-11-28
found it doh!

---

### Post by Virtual Liberty on 2009-11-28
Add it to startup application list ?

---

### Post by DarinB on 2009-11-28
yeah it didn't work as on the forum i will try adding it to startup application list

---

### Post by DarinB on 2009-11-28
where do i find it i have to browse for it? usr bin???

---

### Post by Virtual Liberty on 2009-11-28
/usr/bin/numlockx ( [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock) ).[URL="https://help.ubuntu.com/community/NumLock"]
[/URL]

---

### Post by wojox on 2009-11-28
Just put:

```
numlockx
```

---

### Post by DarinB on 2009-11-28
do i have to tick the remember application already running when logging out?

---

### Post by DarinB on 2009-11-28
still no num lock light on keyboard at log in? 
did i miss a step
1 added numlockx via synaptic
2 Enabling Numlock in Jaunty
System -> Preferences -> Keyboard -> Layout -> Layout Options -> Miscellaneous compatibility options -> turn 
on "Default numeric keypad keys"
3. made changes system wide
4. added to start up applications
humm seemed so simple ????? I have done enough keystrokes trying to save the one 
 i would have used logged on in a life time LOL

---

### Post by wojox on 2009-11-28
[http://myubuntublog.wordpress.com/2009/05/20/jaunty-enabling-num-lock-at-boot-after-login/](http://myubuntublog.wordpress.com/2009/05/20/jaunty-enabling-num-lock-at-boot-after-login/)

---

### Post by DarinB on 2009-11-28
Hey this worked it is fun when you get stuff to work.
Enabling NUM Lock at boot

The Default behaviour is for the NUM Lock key to be off at boot up, but if you wish to have it enabled for entering your login password, follow these instructions.
From Synaptic Package Manager, search for and install numlockx or, from the Terminal type or copy and paste:
sudo apt-get install numlockx
To get it working, you now have to edit the appropriate startup file. First, make sure you have a working backup of the file, in a Terminal type or copy and paste:
sudo cp /etc/gdm/Init/Default /etc/gdm/Init/Default.bak
Next, modify the gdm/Init file. In a Terminal type or copy and paste;
gksudo gedit /etc/gdm/Init/Default
Scroll down to the end of the file, and above the line that says “exit 0&#8243; add the following:
if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on
fi
Save the file then, next time you reboot, your NUM LOCK should default to “on.
Keeping Num Lock on afetr login:
Open [System], [Preferences], Startup Applications], click on add type numlockx in the 1st box numlockx in the 2nd box and keeps Num Lock on after login in the 3rd box, then click on [Add]. now restart your PC.
*copied from martin's ubuntu blog*

---

### Post by SuperSonic4 on 2009-11-28
That seems like a lot of trouble. Couldn't you just cp it into ~/.Autostart or the equivalent

---

### Post by DarinB on 2009-11-28
beats me if your idea would work try it out and post it.
the way i did it worked. it is a bit of a pain in the neck one would think that it would be a basic feature since passwords are more secure if they have numbers and letters.

---

