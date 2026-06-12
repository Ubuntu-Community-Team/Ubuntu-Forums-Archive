---
title: "Where is my xorg.conf????"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by Abu_Dayya on 2010-04-17
I want to view/edit my xorg.conf file, but I can't seem to find it???? Its not under /etc/X11/xorg.conf. I tried: ```
sudo ls -l /etc/X11
sudo find / -name "xorg.conf"
kdesudo dolphin (and then navigate to /etc/X11)
```
Yet I can't seem to find it.

I'm on kubuntu 9.10, KDE 4.4.2

---

### Post by mikewhatever on 2010-04-17
There is none. You can generate one with: [I]sudo Xorg -configure
[/I]  .

---

### Post by Abu_Dayya on 2010-04-17
> **mikewhatever said:**
> There is none. You can generate one with *sudo X -config*.

What?? Why?? Is this only a KDE thing or 9.10 thing? I only recently switched from Gnome to KDE, but I do remember having xorg.conf in earlier ubuntu releases...

Anyway, Thanks alot. What does this command actually do? do I have to reboot/logout to get the file? Thanks again

---

### Post by 3rdalbum on 2010-04-17
> **Abu_Dayya said:**
> What?? Why?? Is this only a KDE thing or 9.10 thing?

Neither, it's an Xorg thing. X doesn't need an xorg.conf anymore. But it can generate one, if you wish to edit it. This isn't a new thing, X has been able to run without a configuration file since some time in 2007. It's only "recently" (2008, I think) that it doesn't actually generate a file unless you ask it to.

> What does this command actually do? do I have to reboot/logout to get the file? Thanks again

Assuming that you're not already running an X server, the command uses Xorg's inbuilt hardware detection to generate a valid xorg.conf file, and puts it into the current working directory. You still need to copy it to the correct location. After doing that, you can reboot or run:

```
sudo service gdm start
```

---

### Post by Abu_Dayya on 2010-04-17
Ok one more question ( I know I sound stupid, but please bare with me): Once I generate the file and copy it to /etc/X11, Do I just make whatever change I want and then delete it? or does it have to stay in the right directory in order for my changes to take effect??

Thanks again guys

---

### Post by dwarfolo on 2010-04-17
It must stay in place. If you delete it Xorg will start normally without it.

---

### Post by dlw on 2010-04-17
I also have an xorg.conf problem I need help with.
Following the above steps did not help.

I have a dual monitor system that was working fine with an ati driver. After adding an Nvidia grafics card to add two more monitors, I lost it all. Just a blank screen after booting up.

Booting up in safe mode, I tried the above steps plus tried other xorg.conf.* files that are in /etc/X11.

Also when installing the Nvidia driver, there was suppose to be a xorg.conf.original made from the original xorg.conf file for backup. There is no xorg.conf.original.

Any help will be appreciated.

dlw

---

### Post by Abu_Dayya on 2010-04-28
OK. I just generated my xorg.conf file, did my tinkering, then rebooted, and now I broke my xserver. When I boot I just get a green screen for a few seconds then it turns black and stays there. I set my KDM to login automatically (no password required). Now I just need to know how to drop to shell so I can revert the modificationa I made to xorg.conf again. Any help?

---

### Post by sadaruwan12 on 2010-04-28
Use the Live CD and edit your xorg.conf file or delete it and try booting in to the normal mode.

---

### Post by Grenage on 2010-04-28
> **Abu_Dayya said:**
> OK. I just generated my xorg.conf file, did my tinkering, then rebooted, and now I broke my xserver. When I boot I just get a green screen for a few seconds then it turns black and stays there. I set my KDM to login automatically (no password required). Now I just need to know how to drop to shell so I can revert the modificationa I made to xorg.conf again. Any help?

When the screen goes blank, can you *Ctrl-Alt-F6* to get a shell?

---

### Post by Abu_Dayya on 2010-04-29
The Live CD trick worked. Thanks

---

