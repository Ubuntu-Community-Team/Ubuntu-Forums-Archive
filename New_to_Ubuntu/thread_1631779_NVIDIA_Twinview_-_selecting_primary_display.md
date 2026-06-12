---
title: "NVIDIA Twinview - selecting primary display ?"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by myotis on 2010-11-27
I have just installed an adaptor Asus Geforce  210 graphics card (Ubuntu 101.10) and am trying to set up dual monitors. I am now at the stage of being a bit scared that I break something that might be difficult to fix.

The second monitor isn't automatically detected, but I can detect the second monitor and get it working through the NVIDIA XServer settings dialog GUI.

However, even though I have ticked the box to say that the main monitor should be the primary display, and the corresponding box is unticked for the second monitor, the second monitor has the dock moved to it. I obviously want the dock on my main monitor and don't really understand why this is defaulting to the second monitor

There is an option to save X to configuration files, can anyone tell me if saving and rebooting might fix this.  

Searching the forum suggests that setting up the primary display needs to be done running as root, so I am assuming that this change will need my password and then a re-boot.

However I am nervous about ending up with some difficult to fix display problem if I change the x config file wrongly.

Can anyone give me some advice, on whether I should just go ahead and save the x-config and reboot, or if I am missing something.

Many thanks,

Graham

---

### Post by djmac on 2010-11-27
I am not really sure if saving the configuration will fix your problem, (it might?) . . . so sorry on that front.

 . . . But if you would like to try ... you can easily make a backup of the current configuration file (i.e. xorg.conf) by:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

And then, if the solid waste hits the rotary blades, then you can easily restore the previous configuration in a command line with:

```
~$ sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

Also, you need to run "nvidia X Server Settings" as root, (otherwise the configuration file won't save)

```
gksudo nvidia-settings
```

Good luck!

---

### Post by myotis on 2010-11-27
> **djmac said:**
> I am not really sure if saving the configuration will fix your problem, (it might?) . . . so sorry on that front.

Also, you need to run "nvidia X Server Settings" as root, (otherwise the configuration file won't save)

```
gksudo nvidia-settings
```

Good luck!

Well, for some reason, after a morning of repeatedly trying this, with repeated booting and rebooting, this has suddenly started to work, and the "Save" from the GUI also seems to have made the change permanent, as even after a complete shutdown , the two monitors are working as expected.

What actually happened was when I opened the NVIDIA GUI config settup. For the first time in probably eight attempts the little illustration of the two monitors showed the monitors overlapping, before the second monitor was on the left. I dragged the second monitor to the left, clicked apply, and the Gnome console etc stayed on the main monitor.

When I tried to save the config file, I got a parsing error, but when I closed that error box down, I got a second dialog box, which when clicked allowed me to save the file. So it seems to be solved but I have no idea why.

---

### Post by myotis on 2010-11-27
As a follow on to this, I now realise what the difference is.

Both monitors now have their position set to "Absolute". Before the main monitor was set to absolute and the left hand monitor set to on left.

Graham

---

### Post by glide on 2011-12-06
Still can't save the file with gksudo nvidia-settings.
I copy/pasted the content into a file and manually put it in /etc/X11/, rebooted, and the dock is still appearing in the wrong screen.
Notice that my primary display is located on the right.

---

### Post by zero2xiii on 2011-12-06
Hay,

I see the thread is marked as solved, yet it seems like you still have a problem? Hmmm, well just for the record. I have noticed things are backward in there. Try making the other monitor the Main or absolute monitor, that should fix things up.

Good luck

Oooh nervermind, now I see. :)

---

### Post by glide on 2011-12-06
Thanks but nothing is changed

---

