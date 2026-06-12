---
title: "could not start the x server error"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by som1special2 on 2009-01-19
installed skype, kopete and connected a logitech quick cam chat.

noticed OS started to slow to an almost halt. restarted and cpu said:

could not start graphical enviroment, please restart GDM when corrected.

gives me spot for login and password, (terminal wiondows)

please help

---

### Post by kokkus on 2009-01-20
Open recovery mode from grub and from the list on the blue screen choose "try to fix x server", now you're graphic works again, go to hardware drivers and enable your graphic card again.

---

### Post by som1special2 on 2009-02-01
how do I do that?

---

### Post by zabien1970 on 2009-02-01
If you can get to a terminal, most likely you'll have to choose recovery mode from your boot list, then ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` may help

---

### Post by haasalmi on 2009-02-02
Hi,
I'm getting the same error message, although I did not install anything... Only removed my camera memory card without unmounting it first, which I think caused the problem. 
The suggestion above [sudo dpkg-reconfigure....] helped for one session in GNOME, but when I turned on the laptop the next time, the same issues were back. In GNOME safe mode, I can log on and everything looks normal, except files are locked and regular programs like Firefox and OpenOffice will not start at all.
I have an Asus Eee PC with eeebuntu. And the installation CD is not with me since I'm travelling... Would appreciate any tips! Thanks!

---

### Post by Eisenwinter on 2009-02-02
Post the output of:

```
cat /etc/X11/xorg.conf
```

---

### Post by haasalmi on 2009-02-02
In the terminal, I cannot see the full output of ```
cat /etc/X11/xorg.conf
```, because the terminal window is not a proper scrollable window, just a square with no edges...
Anyhow, what I can see (the end of the output) is

...
   Option   "Protocol"   "auto-dev"
   Option   "HorizEdgeScroll"   "0"
EndSection

Section "Device"
   Identifier   "Configured Video Device"
EndSection

Section "Monitor"
   Identifier "Configured Monitor"
EndSection

Section "Screen"
   Identifier   "Default Screen"
   Monitor   "Configured Monitor"
   Device   "Configured Video Device"
EndSection

Section "ServerLayout"
   Identifier   "Default Layout"
   Screen   "Default Screen"
   InputDevice   "Synaptics Touchpad"
EndSection

...

It seems that the x server error message is very generic and various complicated issues lay behind the problems people are posting on the threads similar to this, which is why I haven't found anyone with exactly the same situation..?
Thanks for your help.

---

### Post by som1special2 on 2009-02-14
by simply pressing "esc" as grub starts will vault you into recovery mode.

---

### Post by haasalmi on 2009-02-22
What I finally ended up doing was starting up the laptop with a pen drive (memory stick) which had another (newer) version of EEEbuntu on it. This way, I could access my files, save them onto the stick, and then re-install EEEbuntu. I have no idea what caused the problem in the first place, but at least the laptop is working normally again.. :)
Thanks to everyone who gave me tips!

---

