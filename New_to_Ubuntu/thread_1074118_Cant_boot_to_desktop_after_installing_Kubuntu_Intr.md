---
title: "Cant boot to desktop after installing Kubuntu Intrepid"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by HittingSmoke on 2009-02-18
So I decided to switch to Kubuntu and use KDE 4.2 from Ubuntu Intrepid which was working fine. I tried a Kubuntu live CD, I even installed KDE 4.1 and 4.2 along side Gnome and they both worked perfectly. After making my decision I formatted my root partition and installed Kubuntu keeping my Home partition from Ubuntu.

After installation finished and the system rebooted I got to the KDE log-in screen. After putting in my pass and hitting log in I get to the splash screen, but almost instantly I get a white screen, then a black screen with a mouse but nothing on it. The log in sound plays and then nothing. I can restart X and try to log in again with the same results. If I try to log in with failsafe mode I get this error:
```
Xsession: unable to launch failsafe XSessiojn x-terminal-emulator not found
```

I tried running recovery mode and dpkg just spits out a bunch of failed messages and says I should run apt-get update or apt-get update --fix-missing neither of which helped.

The file system check works fine and the X fix doesn't help. I tried running apt-get upgrade from the command line and  there didn't appear to be any errors, but it did not change my situation at all.

I'm posting this from my Live CD so the disk is fine and my system will run Kubuntu, there's just something going wrong here that I don't understand.

Anyone know how I can fix this? It's kind of a pain booting into the Live CD to use my PC.

*edit* I also tried apt-get install x-terminal-emulator but that was no help, it returns about 1700 package results.

---

### Post by HittingSmoke on 2009-02-18
After enough screwing around I figured it out.

I realized that if I stopped X all together after using alt+F2 then if I started X from the same command prompt then I could dump back out of X after it quit loading to check for errors. There were no errors, just a dead stop after something about configuring Xorg.

So I checked Xorg and the Xorg logs. Xorg was set to defaults and the Xorg log had no errors, just the same stop as if it just ended.

After figuring it was video related I checked what nvidia related things were installed and I had several packages but none containing the actual driver (all nvidia-*-modaliases, * being the version numbers). So after running an install for nividia-glx-177, because thats what i had running on my Ubuntu install, and rebooting it worked fine. It didn't use the drivers right away, but some how this let me finally reach my desktop.

So yea, all fixed. Hopefully posting this will be useful to someone so It's not just taking up space.

---

