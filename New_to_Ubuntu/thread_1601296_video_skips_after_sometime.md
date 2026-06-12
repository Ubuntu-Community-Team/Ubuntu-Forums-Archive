---
title: "video skips after sometime"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by olderek on 2010-10-20
hi im new here to the ubuntu and linux world.
i recently installed ubuntu 10.10 and was loving every bit of it, not until i started watching a movie on vlc and after sometime, the video is distorted. 

i tried to switch to the default movie player and the some thing happened. it is only when i restart my laptop that i can watch the movie for another 30 minutes until it starts to skip.

any help....
olderek.

---

### Post by P4man on 2010-10-20
Is possible something is overheating? What laptop do you have?

---

### Post by olderek on 2010-10-22
i have an acer aspire 5732Z the previous version of ubuntu had no problems.
i also have install the compiz-theme effects and its working well but all my video players keep skipping though the audio is fine.

---

### Post by P4man on 2010-10-22
open system monitor and see if something is hogging your cpu and eating up your ram during those 30 minutes.

---

### Post by JIGNESH RAVAL on 2010-10-22
yes I have also this problem in linux...
but not all time , rarely...

---

### Post by olderek on 2010-10-22
how do i tell if something is hogging up my cpu and if found, how can i stop it. how does that affect the video clogging?

---

### Post by P4man on 2010-10-22
Just open system > administration > system monitor and check the CPU (and memory)load and the processes using it. Make sure in the  view menu you select ALL processes, not just your own. 

If you are not playing the movie or doing anything else, CPU load should be below ~10% or so and no process other than a big application you know is running (like firefox) ought to take up more than a 100-200Mb or so. If you see something using 100% of a CPU core and/or many hundreds of megabytes, let us know which one.

---

### Post by olderek on 2010-10-23
non of the programmes i normally use like vlc and totem, use up my cpu. actually, non of the programmes i run eat up my cpu. i have a dual core and i'm sure they should be able to handle all my programmes.
sometimes when playing a song with rythmbox, my sound starts to skip and stops after a while. when watching a movie with movie player or vlc, i watch it very well for the first 20-30 minutes and then it starts to skip for a while till it stops. in the middle of its skipping, i sometimes move the mouse/cursor around the screen and the skipping will stop, when i stop moving the mouse, the skipping continues. 
i have tried to uninstall compiz-theme effects, but the problem is still persistent. 
any help....
olderék

---

### Post by sandyd on 2010-10-23
> **olderek said:**
> non of the programmes i normally use like vlc and totem, use up my cpu. actually, non of the programmes i run eat up my cpu. i have a dual core and i'm sure they should be able to handle all my programmes.
sometimes when playing a song with rythmbox, my sound starts to skip and stops after a while. when watching a movie with movie player or vlc, i watch it very well for the first 20-30 minutes and then it starts to skip for a while till it stops. in the middle of its skipping, i sometimes move the mouse/cursor around the screen and the skipping will stop, when i stop moving the mouse, the skipping continues. 
i have tried to uninstall compiz-theme effects, but the problem is still persistent. 
any help....
olderék

post output of
```

aplay -l
lspci
cat /etc/X11/xorg.conf
```

also try
```

metacity --replace
```

---

### Post by NightwishFan on 2010-10-23
Edit: Before you try this do this:
Press Alt+f2 and type gstreamer-properties
Change "video default output" it from auto to "X window system (no xv)"


The problem may be alsa. To fix (or see if this works) Do the following:

Press alt+f2 and type: gksudo gedit /etc/pulse/default.pa
Find the line that looks like this (without quotes): "load-module module-udev-detect"
Change that line (without quotes) to: "load-module module-udev-detect tsched=0"
Save the file and reboot.

To fix just remove the "tsched=0" you added.

If this works, consider filing a bug by pressing alt+f2 and typing:
```
ubuntu-bug alsa-base
```

---

### Post by olderek on 2010-10-25
thanks guys, but i think i got another workaround.

**STEPS**: *Compiz Configuration*

1. Download CompizConfig Settings Manager from Ubuntu repository.
2. Navigate to.. System --> Prefences --> CompizConfig Settings Manager
3. Navigate to.. General --> General Options
4. Click "General Options" to open window
5. Click "Display Settings" tab
6. Uncheck "Detect Refresh Rate"
7. Move "Refresh Rate" slider to 60, or set 60 in the box
8. Check "Sync to VBlank"
9. Click back button to move back to main CompizConfig window
10. Navigate to.. Utility --> Video Playback
11. Uncheck "Video Playback" then exit the CompizConfig Settings Manager.


**STEPS**: *Nvidia Configuration*

1. Pull up nvidia-settings
.. Navigate to.. Applications --> System Tools --> nvidia-settings
.. or open a terminal, type "nvidia-settings" , press enter
2. Click "X Server XVideo Settings"
3. Check "Sync to VBlank" _IF_ not checked
4. Click "OpenGL Settings"
5. Uncheck "Sync to VBlank" _IF_ checked
6. click quit button
7. click quit button
8. Reopen nvidia-settings to verify that config changes were saved.
.. IF they were saved, you are done with step 8.
.. IF they were not saved, ~/.nvidia-settings-rc in your home directory
.. may be under root permissions. You will need to chown chgrp for the file.
.. Then you will need to start back at Step 1 and repeat all steps.

**IMPORTANT**: Reboot your machine when finished. The driver changes won't function correctly until you reboot

when i did this, my videos started playing straight on till the end with out any disturbance/skipping/clogging.
have fun...
olderek

---

### Post by P4man on 2010-10-25
Thats surprising that would help. What you are doing is basically fixing vsync, which would have the same effect the first minute as after a few hours?

---

