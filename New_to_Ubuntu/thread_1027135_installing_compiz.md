---
title: "installing compiz"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by FM101 on 2008-12-31
Hello,
This must be a beginner question.
I installed compiz from the add/remove apps.
I Searching around I see you need to enable your video card.
So I go to System>admin>hardware drivers.
I see something strange.  Device driver is wl.  and it is enabled.
Not sure if that is my video driver?
By the way I am on a dell mini9.  if that helps.

However I do not see the menu item for "Advanced desktop effects"

thanks for any help

---

### Post by eBoxNet on 2008-12-31
hello happy new year :

first you have to enable visual fx on your computer :

System -> Preferences -> Appearance -> Fx -> Enable

then install Compiz Config Manager (if its not installed)

type in terminal : 
```
sudo apt-get install compizconfig-settings-manager
```

System -> Preferences -> can't remember the name it should be something about compiz.

---

### Post by adult swim on 2008-12-31
wl is for your broadcom wireless card.  to make sure that compiz is enabled, go to system>preferences>appearance and then go to the visual effects tab.  make sure that extra is selected.  if you want to further configure compiz youll need to download the compiz settings manager.  to do this go to a terminal, applications>accessories>terminal and enter in ```
sudo apt-get install compizconfig-settings-manager
```  once it downloads you can find it in system>preferences>compizconfig settings manager.

---

### Post by Coder543 on 2008-12-31
install [CCSM]("apt:compizconfig-settings-manager").

---

### Post by eBoxNet on 2008-12-31
> **Coder543 said:**
> was that a failed apt link? install [CCSM]("apt:compizconfig-settings-manager").

my bad i didn't want to post an apt link.
sorry,i fixed it.

---

### Post by 73ckn797 on 2008-12-31
> **adult swim said:**
> wl is for your broadcom wireless card.  to make sure that compiz is enabled, go to system>preferences>appearance and then go to the visual effects tab.  make sure that extra is selected.  if you want to further configure compiz youll need to download the compiz settings manager.  to do this go to a terminal, applications>accessories>terminal and enter in ```
sudo apt-get install compizconfig-settings-manager
```  once it downloads you can find it in system>preferences>compizconfig settings manager.

The graphical solution if terminal commands are not your bag is System/Administration/Synaptic.
Find "compixconfig-settings-manager".  Right click "Mark for Installation" and "Apply".

---

### Post by FM101 on 2008-12-31
Thanks for helping.

If I go to 
System -> Preferences -> Appearance 
I do not see Fx or visual effects tab
I have theme, background, fonts and interface

---

### Post by Coder543 on 2008-12-31
What ubuntu are you using again? [URL="http://farm3.static.flickr.com/2276/2521711081_97f80af6ec.jpg"]Visual Effects
[/URL]

---

### Post by FM101 on 2008-12-31
> **Coder543 said:**
> What ubuntu are you using again? [URL="http://farm3.static.flickr.com/2276/2521711081_97f80af6ec.jpg"]Visual Effects
[/URL]

It came with my new dell mini 9.
The about says ubuntu 8.04
also the gnome desktop. version 2.22.2

thanks

---

### Post by eBoxNet on 2009-01-01
you should install 

    *  compizconfig-settings-manager
    *  emerald
Reboot

and then go to System > Preferences > Advanced Desktop Effects Settings

---

### Post by adult swim on 2009-01-01
if there is no way to turn it on via the appearance menu then you can enable compiz by pressing alt+f2 and entering in ```
compiz --replace
```  either way you should install the compiz settings manager so you can set up how you want compiz to behave.

---

### Post by FM101 on 2009-01-01
> **eBoxNet said:**
> you should install 

    *  compizconfig-settings-manager
    *  emerald
Reboot

and then go to System > Preferences > Advanced Desktop Effects Settings

Thanks for your help
I installed 
    *  compizconfig-settings-manager
    *  emerald
rebooted.  
I have the Advanced Desktop Effects.
However, I do not think they are working.
I think I might still have to enable the visual effects?
I still do not have that tab.

?

---

### Post by eshant_engineer on 2009-01-01
except cube,water,fire effect everything is hanging my system, beside this shift switcher(shift+super+s) put my sys into unstability(bank screen then cross pointer repeatedly)
config-
 C2D 1.86 GHz
 2.5 GB
 1077 MB swap

---

### Post by FM101 on 2009-01-01
Bumping back up.  Trying to get some help.

I installed
* compizconfig-settings-manager
* emerald
rebooted.
I have the Advanced Desktop Effects.
However, I do not think they are working.
I think I might still have to enable the visual effects?  Somehow?
I still do not have that tab.

---

