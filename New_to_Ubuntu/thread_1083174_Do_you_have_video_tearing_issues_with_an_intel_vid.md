---
title: "Do you have video tearing issues with an intel video card?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by MillDaKill on 2009-02-28
If you have had video tearing issues with an intel video card this might be able to help you.  Tearing is a form of video distortion that makes the video look like it is tearing apart during fast full screen motion.

Command 1. 
"xvinfo | more"
xvinfo will display information about the xv video output driver that we will "pipe" to more so we can read the output page by page.

As you use the space bar to page through the output keep an eye out for "Adaptor #X: 'Intel(R) Video Overlay " where X will be a number.

Once you find the Video Overlay section look for a line called "port base: XXX" where the XXX will be a number, for me it was 115. 

once you have the "port base" number we will form a command for mplayer like this...

Command 2:
mplayer -fs -zoom -vo xv:port=115(use your own port base) filename.avi

-fs = full screen
-zoom = scale with software if you can't use hardware
-vo xv:port=XXX = Use the Intel(R) Video Overlay with the xv video driver at your "base port" value.

---

