---
title: "Display setting Problem, won't keep my settings on restart/log in/out"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by MikesGuitar on 2009-05-07
Whenever I log in/out, or restart my comp, my display settings do not keep. I when I try to use the display configuration in preferences I get this message, "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" At which point I say yes and it brings me to my NVIDIA X Server Settings. This did not use to happen, only when I upgraded to 9.04, and when I first upgraded I had no issues with the display. My NVIDIA Driver Version is 180.44 if that helps in any way, I am still somewhat of a novice in Linux world. How can I ensure my display settings remain intact after rebooting and login/out?

---

### Post by Didius Falco on 2009-05-07
Hi,

There is a bug report on this in LaunchPad at:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/362704](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/362704)

Thee seems to be a work-around that has done the job for a couple of people:

> [Phil Riley]("https://bugs.launchpad.net/%7Ephillipriley92")          wrote     on 2009-05-03:     [              (permalink)     ]("https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/362704/comments/7")   
                   just an update on my last post,
 I found that my nvidia configuration settings were not being loaded at start-up,
 Try - System>Preferences>Startup applications, select 'add' and name it something like 'nvidiastartup' and in the command line (the important bit) insert this text "nvidia-settings --load-config-only" (excluding inverted comma's) then click 'add', now your nvidia configuration will run at startup.

        
    


I don't use an nVidia card, so I can't vouch for it, but I hope it helps...

Regards,

Didius

---

### Post by MikesGuitar on 2009-05-07
Thanks for the help, I have found another way to fix this (it worked for me at least). When I went to the display settings manager there is an issue between NVIDIA and the display manager, it says my graphics driver does not support the necessary extensions to use this tool and if I want to use the graphic driver tool instead. I just hit No and it still brings me to the display setting manager, but does not detect my settings. I CAN however still change my display resolution (which was my problem) and when I did this it kept the settings. Other people should try doing this!

---

### Post by Didius Falco on 2009-05-07
You should go add that to the bug report. it may help resolve that bug. How cool would that be?!?

Regards,

Didius

P.S. Please mark this thread solved - see my sig.

---

