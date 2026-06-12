---
title: "No GUI after 10.10 upgrade"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by paulop on 2010-10-16
I just upgraded my PC from 10.04 to 10.10 and after the first reboot I get the command line rather than the GUI, along with the following messages. 

moutall: Disconnected from Plymouth
mount.nfs: Failed to resolve server 192.168.10.4: Name or service not known
mountall: mount /home/shared [1247] terminated with status 32

I'm not sure whether the NFS mount issue is what is causing the GUI to go missing. Please can someone advise me what I need to do to fix the upgrade and get the GUI back.

> Update:
I removed the NFS mount by commenting out the line in /etc/fstab, and then rebooted. The three messages above have disappeared, but I still get the command line.

> Update:
Looking at other forum posts with similar issues, it seems that I should be able to get the GUI to start with the xstart command, so I tried that. I got a screen full of messages, mostly informational. The first error is:
(EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
followed by
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.

So it seems that my nvidia driver got lost in the upgrade. Any idea why, and more importantly, how can I get it back?

---

### Post by gyussz on 2010-10-16
> **paulop said:**
> The first error is:
(EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
followed by
(EE) Failed to load module "nvidea" (loader failed, 7)
(EE) No drivers available.

I guess you should fix that "nvidea" to "nvidia" (/etc/X11/xorg.conf try in recovery mode).

If that doesn't fix the problem you should reinstall and reconfigure the graphics driver.

---

### Post by paulop on 2010-10-17
The "nvidea" was a typo in my first post. The log actually did say "nvidia". After further investigation the problem seems to be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394)

The pertinent comment appears to be that the driver hasn't been updated yet to support Xserver 1.9 (see [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394/comments/22](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394/comments/22)
and [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394/comments/30](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394/comments/30)).

As per this comment ([https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394/comments/31](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394/comments/31)), I have worked around the problem by renaming /etc/X11/xorg.conf to /etc/X11/xorg.conf.tmp (i.e. effectively removing the config file), which enables ubuntu to load up the GUI in safe mode.

---

### Post by paulop on 2010-10-17
> **paulop said:**
>  After further investigation the problem seems to be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394)


In fact the canonical (ha-ha), i.e. original, version of the bug is here: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974)

---

### Post by cariboo on 2010-10-17
You may be just as well off to use the nouveau drivers, add libgl1-mesa-dri-experimental from the repositories for 3D. I'm using the nouveau drivers at the moment, and when running gtkperf, there is less than ½ a second difference between the nouveau drivers and the latest Nvidia drivers.

You can remove the nvidia drivers from the command prompt by typing:

```
apt-get purge  nvidia*
```

---

### Post by paulop on 2010-10-17
> **cariboo907 said:**
> You may be just as well off to use the nouveau drivers, add libgl1-mesa-dri-experimental from the repositories for 3D. I'm using the nouveau drivers at the moment, and when running gtkperf, there is less than ½ a second difference between the nouveau drivers and the latest Nvidia drivers.

You can remove the nvidia drivers from the command prompt by typing:

```
apt-get purge  nvidia*
```

Please can you explain a bit more what you mean by the "nouveau" drivers. I have libgl1-mesa-dri installed, so why couldn't I use that? Also, why do I need to purge the nvidia drivers? Shouldn't it be possible to tell ubuntu to use the libgl1-mesa-dri or even libgl1-mesa-dri-experimental drivers without removing the nvidia drivers? Is it a case of changing the config in /etc/X11/xorg.conf?

---

### Post by gyussz on 2010-10-18
Easiest way to install the latest drivers:
[http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/](http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/)

---

### Post by paulop on 2010-10-18
> **gyussz said:**
> Easiest way to install the latest drivers:
[http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/](http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/)

Thanks for posting this, but that doesn't help if the latest driver you need doesn't actually work with 10.10 (which mine doesn't).

---

### Post by beew on 2010-10-18
> **paulop said:**
> Please can you explain a bit more what you mean by the "nouveau" drivers. I have libgl1-mesa-dri installed, so why couldn't I use that? Also, why do I need to purge the nvidia drivers? Shouldn't it be possible to tell ubuntu to use the libgl1-mesa-dri or even libgl1-mesa-dri-experimental drivers without removing the nvidia drivers? Is it a case of changing the config in /etc/X11/xorg.conf?

I have the same problem, moreover /etc/X11/xorg.conf apparently doesn't exist.

I have started a thread here.
[http://ubuntuforums.org/showthread.php?t=1598591](http://ubuntuforums.org/showthread.php?t=1598591)

This doesn't work for me, but you may find it useful.

[http://ubuntuforums.org/showthread.php?t=1590367&page=2](http://ubuntuforums.org/showthread.php?t=1590367&page=2)

---

### Post by paulop on 2010-10-29
> **cariboo907 said:**
> You may be just as well off to use the nouveau drivers, add libgl1-mesa-dri-experimental from the repositories for 3D. I'm using the nouveau drivers at the moment, and when running gtkperf, there is less than ½ a second difference between the nouveau drivers and the latest Nvidia drivers.

You can remove the nvidia drivers from the command prompt by typing:

```
apt-get purge  nvidia*
```

After scouting around in other related threads I finally took the plunge and did

```
sudo apt-get purge nvidia*
```

and then changed my /etc/X11/xorg.conf file to be the same as christian.remboldt in this post [http://ubuntuforums.org/showthread.php?t=1590367](http://ubuntuforums.org/showthread.php?t=1590367)

I rebooted and everything looks good again. Hurrah. As I don't even really need 3D (I only use my ubuntu PC for spreadsheets and Gnucash) I didn't even bother with the extra steps in Christian's post.

I've seen that nvidia are working on the 96 driver to upgrade it to support xorg-1.9 ([http://www.nvnews.net/vbulletin/showthread.php?t=155622&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=155622&page=2)) but to be honest, I'm not sure I'll even bother to switch back once it's fixed. I'm happy enough with the nouveau driver and at least I can have confidence that future upgrades of ubuntu are not likely to break my display again.

---

### Post by Nikp2003 on 2010-11-13
> **paulop said:**
> I just upgraded my PC from 10.04 to 10.10 and after the first reboot I get the command line rather than the GUI, along with the following messages. 

moutall: Disconnected from Plymouth
mount.nfs: Failed to resolve server 192.168.10.4: Name or service not known
mountall: mount /home/shared [1247] terminated with status 32

I'm not sure whether the NFS mount issue is what is causing the GUI to go missing. Please can someone advise me what I need to do to fix the upgrade and get the GUI back.

> Update:
I removed the NFS mount by commenting out the line in /etc/fstab, and then rebooted. The three messages above have disappeared, but I still get the command line.

> Update:
Looking at other forum posts with similar issues, it seems that I should be able to get the GUI to start with the xstart command, so I tried that. I got a screen full of messages, mostly informational. The first error is:
(EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
followed by
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.

So it seems that my nvidia driver got lost in the upgrade. Any idea why, and more importantly, how can I get it back?

Hey, so this is what i did... 

   ( im new to linux..) 

So i hit CTRL + ALT F7? and got into text mode. 

It had asked me to authenticate, so i did (The username you set up durring the "Who are you" ) 

Just as "cariboo907" had suggested, i did "apt-get purge  nvidia* ", to find out i didnt have authentication. So i found out you do " sudo apt-get purge  nvidia*     " , it asks if your sure and stuff, you say yes, it deletes a ton of stuff. ( Not sure if this is necessary, i did it this way. ) 
(Which it looks like you dont have the nvidia drivers anyways.. so if it doesnt work, whatever :P ) 

Then, i did more research and found out how to re download all of the updates for Nvidia graphics cards, ([http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/](http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/)). 

   So i did the stuff it said to do on that page
"
For the latest Nvidia binary drivers:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

For the latest ATI/AMD binary drivers:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install fglrx

If you previously had an old version on your machine follow these instruction instead.  It makes no difference if you are using an Nvidia or ATI/AMD card.

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade

All you need to do now is reset machine and you&#8217;ll have everything up to date.
" 

I then restarted the whole computer, which i  couldnt figure out the reboot command, so unplugged the damn thing... Once i started it back up, the screen showed some zig zag lines, and then loaded my logon screen (GUI) 

So try this, i think it will work!! Good luck! 

(P.s, haha sorry i dont know much about linux..)

** if this doesnt work, im not sure if you know, "Plymoth" is the boot screen (Which i think its only importance it "Looks cool"? ) . if you do all the steps, and it successfully downloads all the drivers, and still no go, i would enter: "Logout" and then push CTRL + ALT + F8  (Might be F7?).. i know one of those will load the GUI  **

---

### Post by Nikp2003 on 2010-11-13
Oh and i forgot to mention,  on the last line of the command to download all the new nvidia drivers (Or update), i had to do a double space between every word... which was odd, but its the only way it worked for me.. ( "sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings) goto that website i put in my last message and if you pay attention to that last line, youll see what has double spaces.. Good luck!

---

