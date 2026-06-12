---
title: "Compiz Screencast is Choppy"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-04-10
I'm using gtk-recordmydesktop to make screencasts of the compiz cube. I have the frame rate for recordmydesktop at 50 fps and compiz refreshing at 75 fps. When I go to record the cube rotating and then play it back in VLC, the cube rotation is choppy. The video will show the cube kinda hanging there for a second when I'm actually rotating it back and forth. I'm not sure, but I think I noticed less of a problem when I lowered recordmydesktop's fps down to 35. Does that make sense or is it just my perception? 

Is there a problem with recordmydesktop, compiz, or do I just need a better graphics card?

---

### Post by CLomax on 2009-04-10
Compiz might be causing the video playback problem if you leave it on whilst playing the video.

Enter;
```
metacity --replace
```
in the terminal and try playing the video again.

---

