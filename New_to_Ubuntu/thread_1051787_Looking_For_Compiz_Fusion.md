---
title: "Looking For Compiz Fusion"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Tek-E on 2009-01-27
Does anybody know where I can find a Compiz Fusion .deb???
I have looked around continuously but have come up with nothing.
Any help?

Thanks!

---

### Post by 3rdalbum on 2009-01-27
Compiz Fusion is preinstalled on Ubuntu. To configure it, you should install compizconfig-settings-manager - this will give you access to System > Preferences > Advanced Desktop Effects where you can enable the cube, the burning windows, and all the other effects that you've seen on Youtube :-)

---

### Post by Tomatz on 2009-01-27
> **3rdalbum said:**
> Compiz Fusion is preinstalled on Ubuntu. To configure it, you should install compizconfig-settings-manager - this will give you access to System > Preferences > Advanced Desktop Effects where you can enable the cube, the burning windows, and all the other effects that you've seen on Youtube :-)

Install **compizconfig-settings-manager** with the **synaptic package manager** in ***system, administration***

Compiz will only work with a half decent GPU (intel, nvidia, ATI). If you have one, check that the drivers are enabled in ***system, administration, hardware drivers***.

Not all drivers will show there though. If you **ctrl alt right-arrow** and see a nice slide effect, compiz **IS** enabled.

;)

---

### Post by Tomatz on 2009-01-27
BTW are you running Xubuntu?

[EDIT]

Obviously.

---

### Post by halovivek on 2009-01-27
you can try some more [here]("http://sonique54.free.fr/compiz-fusion/compiz-fusion.html")

---

### Post by talsemgeest on 2009-01-27
Since the packages in the repositories are the same across ubuntu distributions, you should be able to install compiz fusion through synaptic package manager (I think synaptic is the default package manager in xubuntu.) Just do a search for compiz, and install the related packages.

---

### Post by Tek-E on 2009-01-27
> **Tomatz said:**
> BTW are you running Xubuntu?

[EDIT]

Obviously.

Im running Ubuntu 7.10 on one partition, and I am also running Xubuntu 8.10 on another partition.  And sadly I still have a partition for windows xp :) why?

---

### Post by Tek-E on 2009-01-27
Thank you for your help everybody!:)

---

### Post by Tomatz on 2009-01-27
I personally haven't used Xubuntu since 7.04 and didnt know if compiz ran by default.

To install compiz fusion, do the following in a terminal:

```
sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
```

Then to make compiz autostart, add the following command to ***system, preferences, sessions***:

```
compiz --replace
```

;)

---

### Post by Kevbert on 2009-01-27
No. Compiz is an extra that you have to install all the components (at least in 8.04 Xubuntu). It can be a bit fiddly to get it going but it works.

---

### Post by sir4taye on 2009-01-28
Compiz settings manager is installed and I'm able to change settings but I don't get the 3d effects. In fact I don't get any control of any settings using the manager. I'm on 8.10 amd64 2g ram scalable upto 128mb nvidia 6100 mobile on a presario f730us laptop. My compiz worked fine on the previous install.

---

### Post by sir4taye on 2009-01-28
1

---

### Post by Tomatz on 2009-01-28
> **sir4taye said:**
> Compiz settings manager is installed and I'm able to change settings but I don't get the 3d effects. In fact I don't get any control of any settings using the manager. I'm on 8.10 amd64 2g ram scalable upto 128mb nvidia 6100 mobile on a presario f730us laptop. My compiz worked fine on the previous install.

Open a terminal and post the output of:

```
compiz --replace
```

---

### Post by sir4taye on 2009-01-28
daddy@daddy-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

The terminal is frozen but the effects work now, but not after reset. I have to run this compiz --replace every time?

Running the script fowls more than just the terminal it screws the whole desktops ability to switch windows and shut down programs.

---

### Post by Tomatz on 2009-01-28
> **sir4taye said:**
> daddy@daddy-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

The terminal is frozen but the effects work now, but not after reset. I have to run this compiz --replace every time?

Add that command to ***System, Preferences, Sessions***. Then compiz will autostart.

---

### Post by sir4taye on 2009-01-28
But if it will not finish this command, freeze up and lose functionality, it doesn't seem to be the fix. Am I wrong? Will I get different results if its auto run on startup?

---

### Post by Tomatz on 2009-01-28
> **sir4taye said:**
> But if it will not finish this command, freeze up and lose functionality, it doesn't seem to be the fix. Am I wrong? Will I get different results if its auto run on startup?

It will lock the terminal up because the command is running in the terminal (*ctrl C* will end the command). If you add the command to ***sessions*** it will not run in a terminal and will be persistent ;)

_**EDIT (just re-read your post):** Press alt F2 then run the command there (NOT in terminal) if all is good, then add it to ***sessions***._

---

### Post by sir4taye on 2009-01-28
> **Tomatz said:**
> It will lock the terminal up because the command is running in the terminal (*ctrl C* will end the command). If you add the command to ***sessions*** it will not run in a terminal and will be persistent ;)

_**EDIT (just re-read your post):** Press alt F2 then run the command there (NOT in terminal) if all is good, then add it to ***sessions***._
thank you. it worked

---

### Post by Nightstrike2009 on 2009-01-28
I have also figured out how to get a Nvidia 6600GT graphics card to use the NVidia 177 drivers and run compiz desktop effects too (the 3D Cube) (there is a slight titlebar glitch but this affects most other compiz users to with Ubuntu 8.10), quite easily for Ubuntu 8.10 newcomers (involving no command lines, just .deb files) Which I have provided a thread link to provided below, I do use Gnome GUI though;

My NVidia 6600GT & Compiz How-to Thread Link: [http://ubuntuforums.org/showthread.php?t=1035634](http://ubuntuforums.org/showthread.php?t=1035634)

PS: I have included all .deb website locations for NVIDIA and Compiz in the How-to itself, also covers how to get cube-reflection effects, hope this helps you too :-)

---

