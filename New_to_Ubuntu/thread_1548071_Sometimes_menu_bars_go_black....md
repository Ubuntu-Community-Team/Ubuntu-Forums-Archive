---
title: "Sometimes menu bars go black..."
date: 2010-08-07
forum: New to Ubuntu
---

### Post by lcdrovers on 2010-08-07
Hi. This may be my first post, but I'm not a complete beginner. I've solved a few problems I've had myself, but anything important is way beyond me. Occasionally, I've had a (seemingly) completely random blacking out of menu bars. It looks like this (look at the top of the screen): [IMG]http://i737.photobucket.com/albums/xx18/cosmicexplorer/ubuntu%20menu%20bar%20problem/Screenshot.png[/IMG] and comments on images and other things are blacked out too, like this (the small black box just to the right of center): [IMG]http://i737.photobucket.com/albums/xx18/cosmicexplorer/ubuntu%20menu%20bar%20problem/Screenshot-1.png[/IMG] This doesn't appear in the menu bar of Google Chrome, and I suspect that is because Chrome makes its own menu bar. I'm running Ubuntu 10.04 on kernel version 2.6.32-24, on a Dell Studio 15 laptop. This happens seemingly randomly, and nothing else is changed. I hope you guys can help. It's not much of a problem, but I'd like to know how to solve it. I have no idea how to approach this, so I'd appreciate any help anyone could give.

EDIT: I forgot to mention this, it's normal when I restart the computer.

EDIT2: The terminal is completely blacked out. Commands still work, but I can't see anything.

---

### Post by Ozymandias_117 on 2010-08-07
It sounds to me like it could be a graphics driver problem. Do you have proprietary graphics drivers installed? If you don't, try installing them. If you do, make sure they're the newest, and reinstall them.

---

### Post by ubudog on 2010-08-07
You can do that at System> Administration> Hardware Drivers.

---

### Post by lcdrovers on 2010-08-07
Sorry for responding slowly. Yes, I do have the latest proprietary graphics driver installed. I tried changing around the title bar options in apps/metacity/general in gconf-editor, to see if it would refresh the title bar or something like that and relieve the problem, but it didn't work. The problem manifests itself in new windows, too, once it's started; I don't think I mentioned that earlier.

---

### Post by lcdrovers on 2010-08-08
bump :(

---

### Post by 0004tom on 2010-08-08
Do you have an nVidia or ATi graphics card?

---

### Post by lcdrovers on 2010-08-08
Yes. An ATI Mobility Radeon HD 4570.

---

### Post by 0004tom on 2010-08-08
Trying installing the proprietary drivers from the ATi site. This is a known bug with ATi drivers, al tho it shouldn't be that bad. Ati claim that they fixed it with the 10.7 drivers. However it still happens for me on some occasions.

---

### Post by lcdrovers on 2010-08-08
OK, I have the driver but it says it's going to install on x.org, while I'm using GNOME as a desktop environment. Should I be worried or will it still work fine?

EDIT: It has an option to install on x.org or to "Generate Distribution Specific Driver Package" Which should I pick? I'm leaning toward the latter, but as the installer has x.org as the default choice, I'm not sure.

---

### Post by 0004tom on 2010-08-08
Yeah your wanting to "Install Driver 8.753 on X.Org 7.5"

The problem with the FGLRX driver from the repo's/Hardware Drivers, Is it's almost 4 months out of date. ATi release a new updated driver every month.

---

### Post by lcdrovers on 2010-08-08
OK I did that, but it hangs at "Postprocessing Kernel Modules"

EDIT: No it doesn't, it just takes a while.

EDIT2: OK, after I rebooted, even though the driver is activated, all of my desktop effects have been removed and can't be enabled. Now I'm really confused. How can I fix this? Is there a way to rollback the driver?

EDIT3: I got this output from aticonfig --initial -f:

Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

Does anyone have any idea?

---

### Post by Ozymandias_117 on 2010-08-08
> **lcdrovers said:**
> OK I did that, but it hangs at "Postprocessing Kernel Modules"

EDIT: No it doesn't, it just takes a while.

EDIT2: OK, after I rebooted, even though the driver is activated, all of my desktop effects have been removed and can't be enabled. Now I'm really confused. How can I fix this? Is there a way to rollback the driver?

EDIT3: I got this output from aticonfig --initial -f:

Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

Does anyone have any idea?

Was the command run as root (Or with sudo)? Perhaps it's running into problems because it's not allowed to write to those directories?

---

### Post by lcdrovers on 2010-08-08
Well now I've made a huge mess.
I attempted to uninstall the driver by clicking remove in System->Administration->Hardware Drivers. It removed it, or so I thought. When I clicked activate, it gave me this message: "SystemError: installArchives() failed"
Then it automatically opened the Update Manager which gave me this: [IMG]http://i737.photobucket.com/albums/xx18/cosmicexplorer/ubuntu%20menu%20bar%20problem/updatemanager.png[/IMG]
Clicking "Install Update" gave me this message: "You have 1 broken package on your system!

Use the "Broken" filter to locate it."
But then continued with attempting to install it and gave me this error message after finding an error in installation: "E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu4_amd64.deb: subprocess new pre-installation script returned error exit status 1" So I'm really confused. When I opened Synaptic it said I had 1 broken package on my system, so I located it and found that it was fglrx-amdcccle! It required fglrx to be installed, so I got the same error message as above. At this point I'm getting really annoyed, because I had a perfectly functioning system, with only a small problem, but I now have a much bigger, much more annoying problem. I realize that this transition from bad to worse was all my fault, but I would really appreciate it if someone helped me out here. I'm not trying to say that the previous responders didn't help, they just didn't have enough information from me to do so. Again, if anyone can help, I'd appreciate it tremendously.

---

### Post by lcdrovers on 2010-08-08
bump...I'm sorry.

---

### Post by lcdrovers on 2010-08-08
I'm such a horrible person, but I won't bump this again if no one responds.

---

### Post by alphacrucis2 on 2010-08-09
> **lcdrovers said:**
> I'm such a horrible person, but I won't bump this again if no one responds.

Which method of installing the ATI driver did you use, (buildpkg or install). Also did you try sudo aticonfig --initial -f before restarting. Note that sometimes the -f switch is required otherwise it doesn't seem to update xorg.conf properly. The instructions only say to do sudo aticonfig --initial

---

### Post by lcdrovers on 2010-08-09
> **alphacrucis2 said:**
> Which method of installing the ATI driver did you use, (buildpkg or install). Also did you try sudo aticonfig --initial -f before restarting. Note that sometimes the -f switch is required otherwise it doesn't seem to update xorg.conf properly. The instructions only say to do sudo aticonfig --initial

I reinstalled the driver from ATI's site, then ran sudo aticonfig --initial -f, then installed fglrx from the update manager, then clicked "Activate" on system->administration->hardware drivers, rebooted, and it worked! Thanks a lot, to you and to everyone who has helped me through this. I really appreciate it. This was my first thread and my first post after using Ubuntu for many months, and this first experience really helped me to understand and to  appreciate the Ubuntu community at large. Again, I'd like to thank you all, and especially appreciate your putting up with me not knowing really anything. You're all so awesome!:D

---

### Post by jtarin on 2010-08-09
Ha,Ha,....that was a close one wasn't it? :)

---

