---
title: "nVidia (177) drivers not leting me use dual screens"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Xyloid on 2008-12-02
Okay, I'm very new, and working on learning this. I went through my install okay, and seem to be all up to date, and current, at least that is what it tells me. I installed a new video card, EVGA (nvidia) GTX 260 and am having trouble telling the nvidia x server setting window that I have 2 screens.
I go to save here "/etc/X11/xorg.conf" and it says "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'" I've tried to rename it and that doesn't seem to work. Not sure what I need to do or where to even look to see if the drivers I have are good, which are version 177, that are recommended. Please help. Bryan

---

### Post by stchman on 2008-12-02
> **Xyloid said:**
> Okay, I'm very new, and working on learning this. I went through my install okay, and seem to be all up to date, and current, at least that is what it tells me. I installed a new video card, EVGA (nvidia) GTX 260 and am having trouble telling the nvidia x server setting window that I have 2 screens.
I go to save here "/etc/X11/xorg.conf" and it says "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'" I've tried to rename it and that doesn't seem to work. Not sure what I need to do or where to even look to see if the drivers I have are good, which are version 177, that are recommended. Please help. Bryan

According to Ubuntu the 177 drivers support the GTX 260.

[http://packages.ubuntu.com/intrepid/nvidia-glx-177](http://packages.ubuntu.com/intrepid/nvidia-glx-177)

Install nvidia-settings

```
sudo apt-get install nvidia-settings
```

There is a menu that lets you configure multiple displays if your card is capable.

You will need to use sudo for the settings to change.

---

### Post by Xyloid on 2008-12-02
okay, so is Sudo something I need to install from the applications menu or do I type that line in to that file that I referenced above in my original post?

---

### Post by ubu84 on 2008-12-02
> **Xyloid said:**
> okay, so is Sudo something I need to install from the applications menu or do I type that line in to that file that I referenced above in my original post?

sudo is something you run from the command line.  you need to bring up a terimal and run the previously specified command as noted.

---

### Post by Xyloid on 2008-12-02
okay, I typed that and this is what I got
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-settings is already the newest version.
nvidia-settings set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

should I reboot my machine for the changes to take effect or not? also the nVidia screen where I tell it to set up the second screen still gives me an error when trying to save configuration. it is working in windows but can't get it to work here, not sure what else I need to do.

---

### Post by overdrank on 2008-12-02
> **Xyloid said:**
> okay, I typed that and this is what I got
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-settings is already the newest version.
nvidia-settings set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

should I reboot my machine for the changes to take effect or not? also the nVidia screen where I tell it to set up the second screen still gives me an error when trying to save configuration. it is working in windows but can't get it to work here, not sure what else I need to do.

When using the nvidia-settings try the command ```
gksu nvidia-settings
``` to open and then try and save the configure. It should not need reboot. It should apply right then.

---

### Post by Xyloid on 2008-12-04
Okay, I've been using those screens that you have shown, as well as the command to open that window, and it says that it requires an x restart. Now when I hit apply it acts like it worked. Then when I hit the save to X configuration file, it gives me "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'." error. How do I get nVidia to save this setting so that I can use the two monitor?

---

### Post by Xyloid on 2008-12-04
can I run a restart in a command window (terminal) while the nVidia window is open to do the restart?

---

### Post by Xyloid on 2008-12-05
[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)
or 
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

---

### Post by bodhi.zazen on 2008-12-05
You need to

Open a terminal and enter:

```
gksu nvidia-settings
```

If you do not run as root (with gksu) you will not be able to save the settings.

Set you video options -> save your settings. When you save your settings, DO NOT merge with the existing settings (un check the merge option when asked).

The restart X (log out and back in) this is a one time configuration, so you should not need to run nvidia-settings every time you log in.

---

### Post by Xyloid on 2008-12-05
Thanks, that is what I needed. That makes more sense to me too.

---

### Post by kolibri on 2008-12-05
I'm having this problem as well, again, after upgrading to Intrepid.

Hardware drivers says that NVIDIA driver 1.77 is activated and currently in use.

When I try to start NVIDIA X server settings it says
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

sudo nvidia-xconfig gives me :
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

However, when i restart the x server, or when i restart the system, it still won't let me access the NVIDIA X-server settings, and I start the loop above again.

---

