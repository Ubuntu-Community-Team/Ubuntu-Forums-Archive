---
title: "ATi Driver issues"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by radiopools on 2010-05-24
Running Ubuntu 10.04, ati radeon hd 4870. I have looked online for ways  to install ati drivers but I keep reading different things, or things  that only pertain to the 5xxx series of cards. I think I have some sort  of video drivers installed, as the splash image is displaying at my  monitor's native resolution, and I am able to run the neat compiz wiggly  windows and desktop-cube-rotating animations, yet when I power up WoW  through wine, it gives me a frame every 3-4 seconds, and the graphics  are very distorted. Not exactly sure what drivers/if i actually have any  drivers installed. How can I check that / how can I get these working? [IMG]http://www.overclock.net/images/smilies/teaching.gif[/IMG]

I'm almost debating moving over to nvidia since I'd prefer linux to be  my primary OS haha.

EDIT: Okay, I went to System>Admin>Hardware Drivers, and activated  that fglrx driver. I restarted, and now I have a black border around  the splash image. It's still the correct resolution, but everything is  squished due to this black border around the splash image. WoW is  running correctly now though. Any ideas on how to fix this border?

Edit2: Border still here, tried messing with resolutions in WoW, but  when I try to change the resolution to anything but the smallest window,  the game crashes.

Edit3: Went ahead and downloaded drivers from ati, figured out how to  install them, did that, now I still have a border around the screen, my  windows don't move fluidly (they leave copies that dissipate off the  screen as the window moves) and I no longer have the animated cube flip  thingy. it's as if there aren't any drivers installed at all.

---

### Post by sandyd on 2010-05-24
> **radiopools said:**
> Running Ubuntu 10.04, ati radeon hd 4870. I have looked online for ways  to install ati drivers but I keep reading different things, or things  that only pertain to the 5xxx series of cards. I think I have some sort  of video drivers installed, as the splash image is displaying at my  monitor's native resolution, and I am able to run the neat compiz wiggly  windows and desktop-cube-rotating animations, yet when I power up WoW  through wine, it gives me a frame every 3-4 seconds, and the graphics  are very distorted. Not exactly sure what drivers/if i actually have any  drivers installed. How can I check that / how can I get these working? [IMG]http://www.overclock.net/images/smilies/teaching.gif[/IMG]

I'm almost debating moving over to nvidia since I'd prefer linux to be  my primary OS haha.

EDIT: Okay, I went to System>Admin>Hardware Drivers, and activated  that fglrx driver. I restarted, and now I have a black border around  the splash image. It's still the correct resolution, but everything is  squished due to this black border around the splash image. WoW is  running correctly now though. Any ideas on how to fix this border?

Edit2: Border still here, tried messing with resolutions in WoW, but  when I try to change the resolution to anything but the smallest window,  the game crashes.
**Thats normal. Its becasue the ATI propreity drivers don't have KMS (Kernel MOde Setting)**

Edit3: Went ahead and downloaded drivers from ati, figured out how to  install them, did that, now I still have a border around the screen, my  windows don't move fluidly (they leave copies that dissipate off the  screen as the window moves) and I no longer have the animated cube flip  thingy. it's as if there aren't any drivers installed at all.
[B]run
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
restart

and install the drivers from the "System -> Administration -> Hardware Drivers" window
[/B].

---

### Post by radiopools on 2010-05-24
running that command and restarting fixed the splash image issue (hooray!) but I no longer have the neato wobbly windows or desktop cube animations, and WoW doesn't load. The system>admin>hardware drivers selection is already activated. Should I deactivate it?

---

### Post by sandyd on 2010-05-24
> **radiopools said:**
> running that command and restarting fixed the splash image issue (hooray!) but I no longer have the neato wobbly windows or desktop cube animations, and WoW doesn't load. The system>admin>hardware drivers selection is already activated. Should I deactivate it?

deactivate it, restart and reactivate it. the OSS aradeon drivers are incpmatible with the Ati opengl drivers, so you wont have any opengl until you do the above.

---

### Post by radiopools on 2010-05-24
Okay, I deactivated it and restarted. Now I'm trying to reactivate it and I'm getting

"SystemError: installArchives() failed"

Edit: I'm also getting a note saying that I have 1 Broken package, when i looked in the package manager, the broken package is "fglrx-amdccle"

---

### Post by sandyd on 2010-05-24
> **radiopools said:**
> Okay, I deactivated it and restarted. Now I'm trying to reactivate it and I'm getting

"SystemError: installArchives() failed"

Edit: I'm also getting a note saying that I have 1 Broken package, when i looked in the package manager, the broken package is "fglrx-amdccle"
go into the package manager and install "fglrx"

---

### Post by radiopools on 2010-05-24
"E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb: subprocess new pre-installation script returned error exit status 1"

Sorry, dont know why it's being such a pain :(

---

### Post by radiopools on 2010-05-25
the fglrx driver is uninstalled / deactivated. When I go to  System>Admin>Hardware drivers and it brings up the FGLRX driver, I  click activate, and it gives me an error:

SystemError: installArchives() failed

In my upper panel, I have a red circle with a white line through the  center, telling me I have one broken package. When I try to fix the  broken package, I get:

E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb:  subprocess new pre-installation script returned error exit status 1

When I look at the details, it says:

Errors occured while processing:
fglrx-amdcccle

completely removed fglrx-amdccle from package manager, restarted, and  tried to reinstall it. Got this error:

[Warning] Uninstall : inst_path_default or inst_path_override

 does not exist in /etc/ati.  This suggests that the ATI driver

 is not installed, the ATI driver is only partially installed,

 or the current ATI driver installed is an older version than the

 one this script was designed for.  Both files listed above are

 required for determining where installed files are located.

 To force uninstallation of the driver by guessing where the

 uninstallation files are located, set the FORCE_ATI_UNINSTALL

 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this  is not recommended).



dpkg: error processing  /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb (--unpack):

 subprocess new pre-installation script returned error exit status 1

Selecting previously deselected package fglrx-amdcccle.

Unpacking fglrx-amdcccle (from  .../fglrx-amdcccle_2%3a8.723.1-0ubuntu3_amd64.deb) ...

Errors were encountered while processing:

 /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb

dpkg: dependency problems prevent configuration of fglrx-amdcccle:

 fglrx-amdcccle depends on fglrx; however:

  Package fglrx is not installed.

dpkg: error processing fglrx-amdcccle (--configure):

 dependency problems - leaving unconfigured


When I tried a second time, I got a pop-up saying this:
Check if you are using third party repositories. If so disable them,  since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

running that command just gives me the above error.

---

### Post by GothicSatan187 on 2010-05-27
Anyone found a fix for this yet?  i'm having the same exact problems running Ubuntu Lucid 64 bit, ati radeon mobility 4200HD?

---

