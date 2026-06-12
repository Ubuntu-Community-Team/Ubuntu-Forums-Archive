---
title: "Desktop effects"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by Scorcher21 on 2010-10-28
Okay having a problem Ill try to catch you up to speed as painless as possible. Was having issues during boot where the only way I could get into my OS (Ubuntu 10.10) was using the DVI port on my graphics port, going to recovery, starting , in failsafeX, then restarting X. However, It wont recognise my graphics card and nothing graphical will work. i.e Blender, or games... It also wouldn't accept the sudo nvidia-xconfig. I did something (not sure what) and for a short period of time I was able to load in to my OS using the VGA port and everything worked fine. Had everything set up including my nvidia settings it recognised my monitor, was able to use blender and play a couple of the games on here Foobilliard, Torcs, and a couple others with no problem. Then This morning I plugged my mp3 player in to charge it up and my system froze up. I rebooted and the same junk started happening. I've managed to somehow (again not sure how (been doing a lot of fiddling and haven't been keeping notes)) but now I'm able to log in regularly through the VGA port but now I cant access anything graphical. I can run sudo nvidia-xconfig , sudo dpkg-configure xserver-xorg , sudo Xorg -configure (did hose last two with gdm stopped), but now I'm at the end of my knowledge ( I know just enough to really foul something up :-))

---

### Post by beew on 2010-10-28
Which Nvidia driver do you install (or do you install any?) and how did you do that?

---

### Post by Scorcher21 on 2010-10-28
nvidia current, the recommended one under system additional drivers. In the process now of removing it and reinstalling it. Also its a 7300 gt


EDIT: nope that didn't work

---

### Post by Scorcher21 on 2010-10-28
Im sure this is result of whats going on but when I try to click OpenGL/GLX Information under NVIDIA xserver settings it blanks out.

---

### Post by beew on 2010-10-28
Hmm. Sorry, this is beyond my ability to help. I have a Nvidia card using the current package and I haven't had a problem. I thought the problem might be related to an older card with the older driver (nvidia-96) which is not supported in Maverick, in that case there are a few work arounds,  but I was wrong.

---

### Post by Scorcher21 on 2010-10-28
thats okay, thanx anyway.

To anyone else just removed and reinstalled nvidia-glx-185, and well pretty much that had nvidia-185 through synaptic... still nothing...

---

