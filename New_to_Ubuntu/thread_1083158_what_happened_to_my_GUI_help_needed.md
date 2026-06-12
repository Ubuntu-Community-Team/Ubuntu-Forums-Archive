---
title: "what happened to my GUI? help needed"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by nachos99 on 2009-02-28
after uninstalling superkaramba and hitting alt-cntrl-backspace, i cant get back into the GUI.

i am getting 

upsplash: Setting mode 1152x864 failed
usplash: Using mode 1024x \768
kinit:name_to_dev_t(/dev/disk/by-uuid/2685aded-8bf3-41c1-8778-dacd1f2ab6b4) = sdb (8,21)
kinit: trying to resume for /dev/disk/by-uuid/2685aded-8bf3-41c1-8778-dacd1f2ab6b4
kinit: No resume image, doing normal boot...

then asks for login and pass and afterwards gives me the 
:~$

any help would be really appreciated.  thanks.

---

### Post by oldos2er on 2009-02-28
After you login, enter 'startx'

---

### Post by nachos99 on 2009-02-28
thanks.  that gets me back to gnome.

however, when i go to restart or shutdown from icon on top of the screen, there is no option to restart or shutdown.  the available options are log out, lock screen, switch user, suspend, and hibernate.

and when i type reboot in the terminal, it will reboot but take me to the previously posted message above and i have to log in CLI.  

this all seems to have happened after uninstalling superkaramba.  

how can i go about restoring to the normal settings/functions?

---

### Post by nachos99 on 2009-02-28
seems to be an issue of GDM not running after KDE or something took over as desktop manager.  even after uninstalling superkaramba, GDM is still not running.

---

### Post by Perryg on 2009-02-28
> **nachos99 said:**
> seems to be an issue of GDM not running after KDE or something took over as desktop manager.  even after uninstalling superkaramba, GDM is still not running.

Try looking under the _system > administrator > services_ and make sure that there is a tick on the graphical login manager.

---

### Post by nachos99 on 2009-02-28
yes, it is checked.

when i go to /etc/X11/default-display-manager

it says 
/usr/sbin/gdm

but when i go to systems_adimin_login window
pop up box says GDM is not running.

---

### Post by kansasnoob on 2009-02-28
I'd recommend:

```
sudo apt-get install --reinstall ubuntu-desktop
```

Then:

```
sudo apt-get -f install
```

---

### Post by nachos99 on 2009-02-28
my problem of getting to the GUI has been solved.  thanks all.

the GDM issue is discussed further at 

[http://ubuntuforums.org/showthread.php?p=6816951#post6816951](http://ubuntuforums.org/showthread.php?p=6816951#post6816951)


btw kasasnoob, those 2 lines do not appear to have worked...

---

