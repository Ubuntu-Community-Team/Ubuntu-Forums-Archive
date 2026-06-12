---
title: "Videos won't play"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by tk1269 on 2009-10-01
Ok, pretty big noob over here. I've been running Ubuntu 8.04 for a while now, with mostly no complaints. I've had a few small problems but have been able to find answers I needed on forums and such for most of them. But now I've got a problem that after hours of forum searching I'm still stuck.

Ever since I upgraded to Ubuntu 9.04, I have not been able to play videos with MPlayer, VLC or any of the other main players. Audio still works, but no video. Mplayer or Movie Player or VLC will open, look like its about to start playing, even bring up the time remaining, but then will just shut down. I can play videos in Firefox without trouble, at least I haven't had a problem yet.

I've downloaded all the codecs that anyone in the 20 or so relevant forum pages has offered, but none of them have helped. I've set up a couple new repositories, but nothing there either. I'm tempted to say that its a driver issue, but I have an integrated video card and from what I have read, Ubuntu handles those without any further driver downloading.

I've searched through tons of forums and found many people with the same problem, but one thing or another has fixed their problem but hasn't helped mine. Like I said, I'm a noob but can follow directions. Somebody please help!!!

---

### Post by utnubuuser on 2009-10-01
Hi -- have you tried completely removing(including configuration files) then reinstalling the offending packages?

---

### Post by tk1269 on 2009-10-01
What would the offending packages be in this instance?  I've been having the problem ever since I upgraded from 8.04 to 9.04 (through 8.10 obviously).  Do you mean totally re-installing 9.04 on my system?

---

### Post by andrew.46 on 2009-10-01
Hi tk1269,

> **tk1269 said:**
> Ever since I upgraded to Ubuntu 9.04, I have not been able to play videos with MPlayer, VLC or any of the other main players. Audio still works, but no video. Mplayer or Movie Player or VLC will open, look like its about to start playing, even bring up the time remaining, but then will just shut down. I can play videos in Firefox without trouble, at least I haven't had a problem yet.

This is often a sign that a video output device has been selected that will then fail under playback. An easy solution to this problem, which does not actually address the underlying issue, is to select another video output. I attach a screenshot showing the vlc options and outlining the best choice for change which is x11.

All the best,

Andrew

---

### Post by tk1269 on 2009-10-02
Ok Andrew, you're on to something.  When I set up the output to x11, I can play videos through VLC.  Thank you.  But I would really like to get to the bottom of this problem.  Anyone have any other great ideas?

---

### Post by tk1269 on 2009-10-04
Bump

---

### Post by hackerlife on 2009-10-08
This worked for me as well... Not sure what the underlying problem is, maybe the video card just isn't very compatible with the other outputs??? (I too have an integrated card) TBH I'm kinda a newb. Either way.

---

