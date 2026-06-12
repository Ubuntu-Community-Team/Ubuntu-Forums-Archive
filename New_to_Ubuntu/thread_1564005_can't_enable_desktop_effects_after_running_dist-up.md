---
title: "can't enable desktop effects after running dist-upgrade"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by romar_31 on 2010-08-30
I am completely new to ubuntu and to any linux distributions. I recently ran the command sudo apt-get dist-upgrade for some reasons. after completing and installing the downloaded updates, restarted the pc, the there came 2 items added to the grub bootloader: the one with linux _**[COLOR=Red]"2.6.32-24"[/COLOR]**_(the updated one i think) and its recovery mode. when i booted there, desktop effects couldn't be enabled but when i booted the one with linux _[COLOR=Red]**"2.6.32-21"**[/COLOR]_[COLOR=Red], [/COLOR][COLOR=Red][COLOR=Black]are running w/o problems[/COLOR][/COLOR]. hope you would get what i mean and your suggestions of solving this will be much appreciated.

---

### Post by romar_31 on 2010-08-30
bump :(

---

### Post by Flimm on 2010-08-30
It looks like a bug to me.

Here's what the wiki page on [debugging compiz](https://wiki.ubuntu.com/DebuggingCompiz) recommends:
> Try different visual effects settings from the appearance preferences (System -> Preferences -> Appearance -> Visual Effects). If the problem still occurs with effects set to "None" then the problem is no in Compiz but one of the systems mentioned above [kernel, X and mesa].

If you have changed the default settings in "CompizConfig Settings Manager" (package name compizconfig-settings-manager) then try resetting these to the defaults by launching it from from System -> Preferences and clicking on the "Preferences" button and then on the "Reset to defaults" button.

Try running the following in a terminal and give us the output:
```
compiz --replace
```

Are any restricted drivers installed? See System, Administration, Hardware Drivers.

---

### Post by romar_31 on 2010-09-01
here'es the result:
```
romar@romar-desktop:~$ compiz --replace
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager


```

---

### Post by realzippy on 2010-09-01
means you have no hardware acceleration/graphics driver installed...?

---

### Post by MisterLambda on 2010-09-01
...essentially meaning the NVidia/ATI drivers (the manufacturer's ones that provide hardware accelerated 3D) haven't caught up to the latest kernel. They take a pretty long time unfortunately.

---

### Post by realzippy on 2010-09-01
> **MisterLambda said:**
> ...essentially meaning the NVidia/ATI drivers (the manufacturer's ones that provide hardware accelerated 3D) haven't caught up to the latest kernel. They take a pretty long time unfortunately.
...Nvidia drivers run perfectly with 2.6.32-24.....

---

### Post by warfacegod on 2010-09-01
But not necessarily the Proprietary drivers that can be downloaded directly from the site. I think that may be what happened here. Those drivers don't carry over with kernel updates. They need to be reinstalled.

---

