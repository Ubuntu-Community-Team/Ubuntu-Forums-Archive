---
title: "NVidia settings won't stick"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by groeswenphil on 2009-06-03
Hi,
Just upgraded to 9.04. Everthing works except for one small irritation.
Upon startup, the screen resolution is set too low.
So, I go to System>Preferences>display and up pops a window that says,"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphic driver vendor's tool instead............so I click yes even though I'm wary of using anybody else's tool.
Up pops the NVidia Xserver window.
It's easy to set the correct resolution and then the screen becomes wonderfully usable.
When I click on Save to XConfiguration file it tells me that it is unable to remove the old XConfig file.
I'm expecting that I might need a spanner to do that?

Any ideas?

Phil

---

### Post by nengracia on 2009-06-03
Same here.

On reboot, it just keeps getting back to its low-res state.


Anyone???

---

### Post by nandemonai on 2009-06-03
In Gnome:

Alt-f2 to bring up a run prompt.

```
gksudo nvidia-settings
```

---

### Post by NightwishFan on 2009-06-03
No, it does not need root.

If you are running GNOME, go to preferences -> Sessions, or if not it is something like Started Applications. Add an entry with this being the command.
```
/usr/bin/nvidia-settings -l
```

If you are running KDE, go to the system settings, advanced, autostarted apps, and add a similar entry.

The -l is important.

The Nvidia settings needs to be run as your user, running as root will cause it to work for the user root. Autostarting it when you log in should cause it to take effect before all OpenGL applications.

---

### Post by groeswenphil on 2009-06-03
Solved..........easily.
Where it says *"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphic driver vendor's tool instead..*
Pick NO.......and a window pops up that lets you set your screen resolution. And this time it came back perfectly after shut down.
Thanks,
Phil

---

### Post by nandemonai on 2009-06-03
> **NightwishFan said:**
> No, it does not need root.

If you are running GNOME, go to preferences -> Sessions, or if not it is something like Started Applications. Add an entry with this being the command.
```
/usr/bin/nvidia-settings -l
```

If you are running KDE, go to the system settings, advanced, autostarted apps, and add a similar entry.

The -l is important.

The Nvidia settings needs to be run as your user, running as root will cause it to work for the user root. Autostarting it when you log in should cause it to take effect before all OpenGL applications.

Aha! Thanks for clearing that up. Another Nvidia trick to put up the sleeve. I was assuming root was needed in order to save the wanted config to xorg.conf.

> -l, --load-config-only
      Load the configuration file, send the values specified therein to the X server, and exit.  This mode of operation is useful to
      place in your .xinitrc file, for example.

---

### Post by nandemonai on 2009-06-03
> **groeswenphil said:**
> Solved..........easily.
Where it says *"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphic driver vendor's tool instead..*
Pick NO.......and a window pops up that lets you set your screen resolution. And this time it came back perfectly after shut down.
Thanks,
Phil

Glad you got it working.

---

### Post by NightwishFan on 2009-06-05
There is a way to get it to autostart with the xorg.conf I believe, perhaps that xinit file they mention. My way works well enough for me.

Also, if you use a WM, such as fluxbox, they normally have their own autostart configuration file to add the command in.

---

