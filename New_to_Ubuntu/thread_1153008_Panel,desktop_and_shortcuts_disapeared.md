---
title: "Panel,desktop and shortcuts disapeared"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by vasiauvi on 2009-05-08
Hello all,
I don't know what is wrong but when I enter in Ubuntu 8.10 the panels,desktop and shortcuts disappeared.I can see only the wallpaper,that's all!
I have to say that I can use ALT+F2 and open the programs.
Before all this things have gone i had some similar problems: some time the panels were "invisible" after boot and after i put the mouse on above panel and click then appeared again.
I have restarted the gdm from terminal but nothing!
I have also to say that I have installed and kde4.2.Maybe is a compatibility issue between gnome and kde?

Can some body help me with this?

Thank you!

---

### Post by NightwishFan on 2009-05-08
Run gnome-system-monitor and see if the gnome-panel process is still there. Gnome should 'always' have at least one panel if it is setup normally.

---

### Post by vasiauvi on 2009-05-08
> **NightwishFan said:**
> Run gnome-system-monitor and see if the gnome-panel process is still there. Gnome should 'always' have at least one panel if it is setup normally.
Thanks for the answer!
Yes,I have a gnome-panel process but no gnome panels I can see.
I can not find the cause root of this behaviour :(. Maybe the ATI video board , maybe the kde 4.2 , maybe......?
Here is the screen shot of the processes:

---

### Post by NightwishFan on 2009-05-08
I do not think it is KDE4.2. We can try to reset your GNOME settings using this command.

```
gconftool-2 --direct \
  --config-source user-configuration-source \
  --recursive-unset
```

---

### Post by vasiauvi on 2009-05-08
This I get on the terminal :
```

paula@paula:~$ gconftool-2 --direct \
> --config-source user-configuration-source \
> --recursive-unset

(gconftool-2:6559): GConf-WARNING **: Failed to load source "user-configuration-source": Couldn't resolve address for configuration source: Bad address `user-configuration-source'
**
GConf:ERROR:gconftool.c:939:main: assertion failed: (err == NULL)
Aborted

```

---

### Post by Niniel on 2009-05-08
I had something similar some time after I upgraded to 9.04. In my case, the window manager wasn't running, so I started "metacity" using the run command.
I then added "gnome-wm" to the startup applications.

---

### Post by vasiauvi on 2009-05-08
> **Niniel said:**
> I had something similar some time after I upgraded to 9.04. In my case, the window manager wasn't running, so I started "metacity" using the run command.
I then added "gnome-wm" to the startup applications.
How did you add "gnome-wm" to startup applications??

---

### Post by Niniel on 2009-05-08
I can't look it up right now, but it's somewhere under System/Administration or System/Preferences. Then you just click the Add button, give the new entry a name, enter the command "gnome-wm" and close. Logout and log back in to test.
Sorry I can't tell you what configuration files to edit, if any.

---

### Post by Celauran on 2009-05-08
> **vasiauvi said:**
> How did you add "gnome-wm" to startup applications??

System -> Preferences -> Sessions

---

### Post by vasiauvi on 2009-05-08
Yes, in the Sessions menu, but the problem is that I can not see any panel to open the Preferences menu.:(
There is an other way?

---

### Post by Celauran on 2009-05-08
Are you not able to manually start it once, then access the menus to add it to sessions?

---

### Post by vasiauvi on 2009-05-08
> **Celauran said:**
> Are you not able to manually start it once, then access the menus to add it to sessions?
No, I can not acces anything from panels, what can I do is to acces ALT+F2 and run programs.

I have rebooted now and this error appeared- see below!

---

### Post by Niniel on 2009-05-08
To get the panel etc. back, run "metacity" - if you really had Gnome as your desktop before. Or is it KDE? The screenshot seems to suggest it was KDE...

---

### Post by vasiauvi on 2009-05-08
I have runed "metacity --replace" with Run command because "metacity" seems that doesn't work. And also after running "metacity --replace" there is no efect (only that the windows disapeare and appeared like when you choose or close compiz).
I had all the time Gnome but I have installed like second manager the KDE (the tutorial is on softpedia.com).
It's put after reboot the PC to enter in Gnome.

I don't know what is happening :(.

---

### Post by Niniel on 2009-05-08
Hm, that may be your problem - having installed KDE via Softpedia. It's better to do that through Synaptic.
When you enter your user name on the login screen, what session is selected by default? Do you have both Gnome and KDE? If so, does either of them start ok?

---

### Post by vasiauvi on 2009-05-08
Niniel,
thanks for your patience.I have searched on the internet and tried this: in the terminal I've just wrote :
```

killall gnome-panel

```
and the panels appeared.Now I hope that will be the same after reboot.
Next step is to uninstall kde4.2 and after that to upgrade to Ubuntu 9.04.

Thanks Niniel for your help!

---

### Post by vasiauvi on 2009-05-09
Hello,
after reboot the problem is that the desktop icons appear and also the panels, but only for one moment after then they disappear, only the panels.I have a keyring to enter for the wireless card but the label where i need to write the password it's not seen.
It's a little bit hard to explain, but I manage to enter the password and when the card trying to get an IP  the panels  appear.
How can I find out what is the problem?

---

### Post by NightwishFan on 2009-05-09
Try this perhaps:

```
sudo dpkg-reconfigure gnome-panel && sudo apt-get update && sudo apt-get upgrade && sudo apt-get install ubuntu-desktop
```

---

