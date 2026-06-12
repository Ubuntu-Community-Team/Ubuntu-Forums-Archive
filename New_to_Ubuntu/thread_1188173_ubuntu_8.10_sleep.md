---
title: "ubuntu 8.10 sleep"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by 5dolla on 2009-06-15
hello I have been having trouble with my computer going to sleep on me when downloading bit 
torrents over night. when i leave my computer on over night it goes to sleep and my download
speed drops very annoying. I have already set the power management settings to never sleep
but the damn thing still sleeps! i need help

---

### Post by albyrne on 2009-06-15
Check the computers BIOS settings.

---

### Post by s.fox on 2009-06-15
Hi and welcome to forums,

There may also be something else adding to the problem you are experiencing with power management not seeming to have any effect.  To fix try the following:
```

sudo nano /etc/X11/xorg.conf 
```Put your password in when it asks for it.

Go to the bottom and add:

```
 Section "ServerFlags"
 Option "blank time" "0"
 Option "standby time" "0"
[COLOR=Red]** Option "suspend time" "0"**[/COLOR]
 Option "off time" "0"
 Option "screen blank" "0"
EndSection 
```Then Ctrl-X to exit

Answer Yes to "Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES) ?"

And press enter to save to the file name you started with.

When you are done you need to restart gdm:
```
sudo /etc/init.d/gdm restart  
```Or you can just reboot.

```
sudo reboot
```Information copied from [here]("http://ubuntuforums.org/showpost.php?p=4917577&postcount=3").

Hope it helps you.

-Ash R

---

### Post by 5dolla on 2009-06-15
im sorry im a newb this is what is at that the bottom of that file. where do i put the command?

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

---

### Post by s.fox on 2009-06-15
Hi,

If that was your complete xorg file then i ***think*** it should be changed to this:
```

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection 
Section "ServerFlags"
 Option "blank time" "0"
 Option "standby time" "0"
 Option "suspend time" "0"
 Option "off time" "0"
 Option "screen blank" "0"
EndSection
```

I would make a backup first though.  Do a Save As.  

This may not work,  but its something similar i have seen for peoples computers going to sleep when they were watching movies.  It might be something similar :)

-Ash R

---

