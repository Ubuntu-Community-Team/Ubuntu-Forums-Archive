---
title: "KDM starts but X fails after login"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by jbrown96 on 2009-02-09
I updated to KDE 4.2 on Kubuntu 8.10 with the PPA provided by the Kubuntu devs. I ran the updates successfully, but now I am having trouble. KDM will start, and I can login. The wallpaper appears, then a dialog pops up. It's not a typical KDE dialog, it looks like X generated it. It reads > Xsession: unable to launch failsafe X session --- x-terminal-emulator not found; aborting. Clicking okay takes me back to the KDM login. I don't know what this means, but I can get X working.

I can switch to a virtual terminal and login. Then I stop X with ```
sudo /etc/init.d/kdm stop
``` I can now startx with ```
startx
``` and everything works properly. 

I thought maybe it had something to do with the xorg.conf, so I reconfigured X with ```
sudo dpkg-reconfigure xserver-xorg
``` but it didn't seem to help at all.

Thanks for the help

---

### Post by cmnorton on 2009-02-09
This sounds like you are missing some files from the install. The dpkg-reconfigure step was a good thing to do. The only thing I can think of is to look at your logs under /var/log.

---

