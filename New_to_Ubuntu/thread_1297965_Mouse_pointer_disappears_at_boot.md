---
title: "Mouse pointer disappears at boot"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by blues2use on 2009-10-22
Running jaunty 9.04 - 2.6.28-15-generic...downloaded some updates, finished my session and shut down. Later when I turned the pc on again, there was no spinning pointer (waiting) as the desktop booted and the mouse pointer is missing after the desktop has loaded and is ready. 

If I hold down the left button and drag I can see where it's supposed to be on the desktop but the pointer doesn't show on the screen. If I hit the CTRL key, I can see the circular indicators for where the mouse should be...I had to enable that feature so I could try to navigate the desktop...

I have found that the only way (so far) that I can get the pointer to appear after the boot to desktop is to start Pan and reply to an article...usually that will make the pointer appear within the reply window...

I have also noticed that **I -do not- have a spinning waiting pointer as the desktop boots.** If I log out, the pointer is enabled...as soon as I log back in, it disappears again...

Anybody have any idea what the deal is?

Thanks for the help...

---

### Post by blues2use on 2009-10-22
> **blues2use said:**
> Running jaunty 9.04 - 2.6.28-15-generic...downloaded some updates, finished my session and shut down. Later when I turned the pc on again, there was no spinning pointer (waiting) as the desktop booted and the mouse pointer is missing after the desktop has loaded and is ready. 

If I hold down the left button and drag I can see where it's supposed to be on the desktop but the pointer doesn't show on the screen. If I hit the CTRL key, I can see the circular indicators for where the mouse should be...I had to enable that feature so I could try to navigate the desktop...

I have found that the only way (so far) that I can get the pointer to appear after the boot to desktop is to start Pan and reply to an article...usually that will make the pointer appear within the reply window...

I have also noticed that **I -do not- have a spinning waiting pointer as the desktop boots.** If I log out, the pointer is enabled...as soon as I log back in, it disappears again...

Anybody have any idea what the deal is?

Thanks for the help...

I think this problem started when I updated the following:

Commit Log for Wed Oct 21 13:32:46 2009

Upgraded the following packages:
libpoppler-glib4 (0.10.5-1ubuntu2.2) to 0.10.5-1ubuntu2.4
libpoppler4 (0.10.5-1ubuntu2.2) to 0.10.5-1ubuntu2.4
libpurple-bin (1:2.6.1-1ubuntu0~pidgin1.9.04) to 1:2.6.3-1ubuntu1~pidgin1.9.04.1
libpurple0 (1:2.6.1-1ubuntu0~pidgin1.9.04) to 1:2.6.3-1ubuntu1~pidgin1.9.04.1
pidgin (1:2.6.1-1ubuntu0~pidgin1.9.04) to 1:2.6.3-1ubuntu1~pidgin1.9.04.1
pidgin-data (1:2.6.1-1ubuntu0~pidgin1.9.04) to 1:2.6.3-1ubuntu1~pidgin1.9.04.1
poppler-utils (0.10.5-1ubuntu2.2) to 0.10.5-1ubuntu2.4
tzdata (2009n-0ubuntu0.9.04) to 2009n-0ubuntu0.9.04.1
**xserver-xorg-video-intel (2:2.7.1-0ubuntu1~xup~1) to 2:2.9.0-1ubuntu2~xup~3**

Can I remove this latest update manually and/or restore the previous update (shown below) from 6/22?

Here's the only other update showing for my system having to do with the Intel Video: 

Commit Log for Mon Jun 22 09:56:47 2009

**xserver-xorg-video-intel (2:2.6.3-0ubuntu9) to 2:2.6.3-0ubuntu9.3**

---

### Post by markus.readus on 2009-10-22
I'm having the same problem. I use a laptop and have a separate monitor that I use instead of the laptop's own monitor. The problem only occurs for me when the separate monitor is plugged in (and that only ever works when it's plugged in when I start up the computer). 

The separate monitor runs at a higher resolution than the laptop's own monitor. During a normal (before the problem described here) log into ubuntu, at the log in screen, the separate monitor shows the same as the laptop's own, but at the laptop monitor's resolution. When I log in, both screens go blank, the laptop screen turns off (this is deliberate) and the separate monitor comes back with a higher resolution, showing a mouse and then slowly building the desktop. 

During my current startup, with the present bug, the mouse is present on both monitors at the log in screen. When I log in, everything is as described above, except that the mouse does not re-appear when the resolution gets bumped up. Its still there, I can click on things, but I can't actually see the pointer. When I remove the separate monitor and boot, using just the laptop monitor, everything is fine. 

Needless to say, this is making work a little difficult. Any ideas how I can undo whatever crippled my computer?! I noticed that the recent update, today, installed a new kernel. Selecting an older kernel makes no difference, same bug appears. 

Thanks,

Mark

---

### Post by blues2use on 2009-10-22
> **markus.readus said:**
> I'm having the same problem. I use a laptop and have a separate monitor that I use instead of the laptop's own monitor. The problem only occurs for me when the separate monitor is plugged in (and that only ever works when it's plugged in when I start up the computer). 

The separate monitor runs at a higher resolution than the laptop's own monitor. During a normal (before the problem described here) log into ubuntu, at the log in screen, the separate monitor shows the same as the laptop's own, but at the laptop monitor's resolution. When I log in, both screens go blank, the laptop screen turns off (this is deliberate) and the separate monitor comes back with a higher resolution, showing a mouse and then slowly building the desktop. 

During my current startup, with the present bug, the mouse is present on both monitors at the log in screen. When I log in, everything is as described above, except that the mouse does not re-appear when the resolution gets bumped up. Its still there, I can click on things, but I can't actually see the pointer. When I remove the separate monitor and boot, using just the laptop monitor, everything is fine. 

Needless to say, this is making work a little difficult. Any ideas how I can undo whatever crippled my computer?! I noticed that the recent update, today, installed a new kernel. Selecting an older kernel makes no difference, same bug appears. 

Thanks,

Mark

I fixed my problem but I'm not sure if it is relevant to your problem. Just backup your xorg stuff before you make any drastic changes.

Here's what I did: **[http://webupd8.blogspot.com/2009/05/reverting-xorg-video-intel-driver-of.html](http://webupd8.blogspot.com/2009/05/reverting-xorg-video-intel-driver-of.html)**

Fixed the mouse problem straight away.

I tried to fix my xserver settings manually but the method shown was much easier. Now I have to make sure I don't download any of the newer Intel Video updates and mess it up again.

Hope this helps...

---

### Post by joanmunoz on 2009-10-23
Hi

I have a similar problem running jaunty 9.04 - 2.6.28-16-generic. After upgrading tzdata and intel video a couple of hours ago, the monitor is just showing the spinning pointer on a black window instead of the start session window at boot. I tried the recovery start both with jaunty 9.04 - 2.6.28-16 and jaunty 9.04 - 2.6.28-15 and tried to fix the video problems, but nothing occurs. I've renamed a xorg.conf backup file I found in etc/X11 directory hoping it will help, but didn't work. Also, I'm not able to connect to the internet at prompt so I can't neither update nor upgrade with apt-get. I need help!!

Thx!!

---

### Post by kemargrant on 2009-10-23
I had the same issue of my mouse not appearing at boot after update my computer two days ago. Eventually after opening some programs the pointer will appear. Its not a fix but that is what I am doing.

---

### Post by joanmunoz on 2009-10-23
But I can't even open my session, so I can't start any program in Gnome Desktop. How can I get back to my original xorg configuration? Maybe starting with a LiveCD and modifying any xorg.conf file?

Please help!

Thx!

---

### Post by hornbyben on 2009-10-23
I had a similar problem.  The first thing I did was to enable 'Show position of pointer when the Control key is pressed' in the mouse preferences, so that I could work out where the invisible pointer is more easily.  Like mentioned above the mouse pointer appears after opening a few programs, but I didn't think that was good enough. So I went to synaptic package manager searched for 'xserver-xorg-video-intel', and then used the Package, Force Version option to force it back to the previous version (2.2.6.3-0ubuntu9.3).  My mouse now works perfectly again.  Obviously it would be better to have tha latest drivers, and maybe I'll try updating when the next update comes out, but this works for the mean time.

Hope that helps.

Ben

---

### Post by taiji_jian on 2009-10-23
I have this same problem after a recent update to xserver-xorg-video-intel. It seems to be related to some account setting. I created a new account for testing and the pointers work fine there. Possibly there is some GNOME setting that doesn't like the updated intel driver?

Any ideas?

---

### Post by joanmunoz on 2009-10-23
A bit desperate now... how can I solve my problem? I boot with LiveCD but I don't know how to fix an XServer fail. Do I have to modify xorg.conf file? Or is it a mouse pointer fail with nothing to do with the tzdata and intel video updates? It will help if I post here the exit of any command, like dmesg?

Any help? Somebody has the same problem?

Thx!

---

### Post by ricardo06 on 2009-10-27
I have the exact same problem. 
I found a solution that is satisfactory. 
A couple of days before the latest xserver-xorg-video-intel update there was an another update. On my machine this before latest update happens to be in the /var/cache/apt/archives under the file name of : xserver-xorg-video-intel_2%3a2.9.0-1ubuntu2~xup~1_i386.deb.

In my case forcing an old version of xserver as proposed by Synaptic would not work. after the downgrade, gdm would not start ! 
So what I did :
Using synaptic "Force" option, I downgraded to version 2:2.6.3-Oubuntu9.3. Then with "Gdebi" installed the packet xserver-xorg-video-intel_2%3a2.9.0-1ubuntu2~xup~1_i386.deb. restart computer. 
Mouse is back.\\:D/

Cheers
Richard

---

### Post by choclo on 2010-01-07
I have that problem, instead of reverting and all that I just move the workspace over and back. As in holding CTRL and ALT and moving right and then left with the directional keys. Hey presto, quick fix!

Of course this is just a quick fix so do the proper stuff as described above if you want it fixed properly!!!!

---

