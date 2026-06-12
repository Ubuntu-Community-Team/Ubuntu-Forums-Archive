---
title: "Can I stop Ubuntu detecting my monitor when booting"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Frodgey on 2009-01-09
I have successfully (thanks to many posts - Thanks) managed to turn my old desktop XP machine into a headless file server.  It all works as I want EXCEPT:

If I have to re-boot it because I have been changing things (I knwo I said it works as I want, but it can always be improved....), I have to attach a monitor or it stops at a screen waiting for an "OK" from the keyboard.

Can I stop Ubuntu checking the monitor on boot?

Thanks in advance.

---

### Post by blueridgedog on 2009-01-09
At what point does this happen?  As a file server, it should not start X.  If it waits when starting X, the you could change the defalault run level and configure the files for that run level to not start X.  

Since the default run level for Ubuntu is 2, you can use 3 as a default non-gui one.  To accomplish this you will need to do the following:

```
sudo gedit /etc/inittab
```

This will be a new file, add the line:

```
id:3:initdefault:
```

Save the file.  Then tell Ubuntu not to run the display manager at run level 3:

```
sudo mv /etc/rc3.d/S30gdm /etc/rc3.d/s30gdm
```

When going to a specific run level, your system will run all the scripts/programs in that run level directory that start with a capital S, so moving S30gdm to s30gdm causes it not to run, but also allows you to "turn it on" again if you decide to by simply renaming it with a capital S.  So, the end result will be your server will boot to run level 3 and at that run level you will not get the windows system.

If you want to go into graphical mode once booted as described, you can:

```
sudo telinit 2
```

Which will revert to run level 2, with the window manager.

There may be an Ubuntu specific way to do this, but this is the way a Linux system varies the service that start at different levels.  If there is a better way, perhaps others will chime in.

---

