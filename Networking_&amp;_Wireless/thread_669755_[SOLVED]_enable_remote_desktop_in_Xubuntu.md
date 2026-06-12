---
title: "[SOLVED] enable remote desktop in Xubuntu?"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by xunil76 on 2008-01-16
i'm trying to get my Xubuntu system set up so i can access it remotely (securely via SSH) from work, and have run into a snag.

i'm following the steps in [this thread](http://ubuntuforums.org/showthread.php?t=383053&highlight=vnc), but i'm stuck at step #6.  since i'm running Xubuntu (XFCE) instead of Ubuntu (Gnome), i don't have a "**_System->Preferences->Remote Desktop_**".

so how do i go about getting remote desktop enabled in Xubuntu?  i've tried searching all over the web, and have found lots of places that show me how to do it in regular Ubuntu, or even Kubuntu, but i can't find anything about how to do it in Xubuntu......  :confused:

---

### Post by xpod on 2008-01-16
I`ve not read the other thread but rdesktop is already installed in Xubuntu,not sure if thats any good to you.
You can run it from the terminal...
```
rdesktop
```
Although i`ve never got round to using ssh/rdp on Xubuntu in any way,shape or form yet so i`m not too sure myself i`m afraid.Too busy playing with new toys.
Cant be tooo much difference though.

I`ve been using normal Ubuntu too long as well me thinks....thats my excuse anyway:)

---

### Post by xunil76 on 2008-01-16
ok, i'm at work right now, so i can't try this out at the moment.....is that the command to use for configuring rdesktop?  or just to start it up?

if that only starts it, how do i configure its options?  i need to do the 3 things listed in step #6 on the other thread, which requires accessing the configuration settings.

thanks


edit:/  just a thought, if i already have the SSH server set up and configured, would i be able to enable/configure the rdesktop remotely?  that would be really nice if i could.....

---

### Post by xunil76 on 2008-01-18
ok, an update:

i've got VNC installed and set up (by following the tutorial at [this site](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html), and i can SSH into my box remotely, but when i try to use any windows-based VNC Viewer software, i get the following:

[img]http://mysite.verizon.net/res0kd2j/dsmpluginerror.jpg[/img]

is there a particular windows-based VNC Viewer that i should be using, or some other way to enable the DSMPlugin to get it to work?

---

### Post by xunil76 on 2008-01-18
ok, one last update to report success!

after i got home from work this morning, i uninstalled vnc4server and chose to install [tightvnc server](https://help.ubuntu.com/community/VNC) instead, and set it up to use GDM (in the XDM/GDM section a little more than halfway down the page).  i kept the existing SSH installation/setup intact, as it was working fine, and just changed the internal port from 5900 in putty to 5901 (tightvnc uses 5901 instead of 5900 for vnc4server).

once i tunnelled in via putty over SSH, i started up ultravnc viewer, plugged in 127.0.0.1:<port#>, got the password box, entered the password, and lo & behold!!!  i'm looking at a nice and (not quite so) shiny remote desktop!!

i credit [this thread](http://ubuntuforums.org/showthread.php?p=4160700#post4160700) with most of the information needed to get it working, but also see my notes in that thread regarding VNC & Xubuntu, which i spent many many hours searching & reading to finally figure out, which lead to the link posted above.

---

### Post by xunil76 on 2008-01-19
ok, well.....time to "unsolve" this thread.....

i wasn't happy with the keys used to support the SSH tunnel, so i created new ones and now VNC is broken again.  SSH is working fine, however.

I even went so far as to completely uninstall VNC & SSH, then reinstall them using the exact same steps as before, but it still will not work.  SSH is no problem, but when i try to VNC in, i get the same message as in the screenshot above.....

could use some help here, before i say to hell with it and wipe out the drive and go over to regular Ubuntu....  :mad: :mad: :mad:

---

### Post by xunil76 on 2008-01-19
ok, after some more testing, i've found that it's only when i try to enable my VNC session over the ssh tunnel that it gives me problems (this is after installing x11vnc, btw).  i tried a vnc connection from within a virtualbox install of WinXP, and went over the local network directly to port 5900, instead of over the port the ssh tunnel is using, and it is working.

so why can't i access the vnc server over the ssh tunnel?

---

### Post by xunil76 on 2008-01-19
man, there's something definitely screwy going on here.....i didn't change any of the configs for VNC or putty (well, i did, but i set them back exactly the way there were before), and all of a sudden, it is now working over the SSH tunnel again........  :confused: :confused: :confused:

i guess i'll mark this as "solved" again, and just not screw with the configuration any more.....

---

### Post by xpod on 2008-01-20
Sorry i never got back xunil76, the avatar should kinda tell you just hectic things can get round here when i get home.Purely symbolic you understand:wink:

Glad you managed to suss it out.
Good stuff.:)

---

