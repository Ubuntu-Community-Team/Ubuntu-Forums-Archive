---
title: "901 display ratio"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Gutterflower on 2009-11-27
Hi all.

I've just upgraded my eeePC 901 to 9.10 and there is but one thing that is causing me grief that was not an issue on 9.04.

When the resolution changes the images is stretched to fill the entire screen rather than maintaining the aspect ratio.  Makes it a little annoying when trying to play my old SCUMM games.

I can't see a setting in the display options and the maintain aspect ratio in SCUMMVM makes no visible difference.

Any suggestions greatly appreciated.

---

### Post by Gutterflower on 2010-01-25
Ok eeebuntu it is then just as soon as 4.0 of that comes out I'll move across.

---

### Post by nerdy_kid on 2010-01-25
if your using NVIDIA there might be an option in nvidia-settings

---

### Post by hessiess on 2010-01-25
This is a fundamental problem with meny open-source games/emus, they are programmed to run at one resolution, which is almost always 4:3 and have no capability of adapting to the actual resolution or aspect ratio of the actual display device. Some hardware drivers do have a capability of working around this problem such as the `force hardware scaling' option in the NVidia drivers. However this is extremely hardware specific.

The only true way to fix this problem is to always render at the native screen resolution and preform software or preferably hardware(OpenGL) scaling and letter boxing. This is exactly how Quad-ren(see signature) works.

If you want to see a solution to this problem, the best option would be complaining to the application developer and get them to add display letterboxing.

---

### Post by Gutterflower on 2010-04-03
Actually complaining to the application creator is exactly the wrong way to go about it.  This is a driver/hardware issue.  I could just as easily describe it as desktop not showing correct aspect ratio when set to a non wide screen resolution.

The Intel chip in the 901 is capable of correcting the aspect ratio should you set the screen to 800x600.  Ubuntu doesn't seem to be able to do it but other custom distributions based off it can.

---

