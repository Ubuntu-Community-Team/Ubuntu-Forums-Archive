---
title: "Full Screen Video Stutters Awfully"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by djk21108 on 2010-07-26
Hi all. You are all such great help I thought maybe you could tackle the issue I'm having with my video.

I have a fairly fast computer, nothing that should struggle with playing DVD quality movies on full screen.

They play great on my computer, with compiz effects wiggling all around the movie still plays frame-skip free.

The second I full screen it on VLC player though, everything goes to hell.

Please help me out in any way you can!

Thanks

---

### Post by djk21108 on 2010-07-26
I'm on 10.04 and have an ati x1400 mobility card. 2.0 Ghz dual core processor and 2GB of RAM

---

### Post by RJARRRPCGP on 2010-07-26
> **djk21108 said:**
> Hi all. You are all such great help I thought maybe you could tackle the issue I'm having with my video.

I have a fairly fast computer, nothing that should struggle with playing DVD quality movies on full screen.

They play great on my computer, with compiz effects wiggling all around the movie still plays frame-skip free.

The second I full screen it on VLC player though, everything goes to hell.



Sounds like the MTRR bug, but I only saw that bug with Jaunty and it was fixed with Karmic. 
(Except, I saw this occurring with YouTube in fullscreen.)

Jaunty has a bug where MTRR erroneously has the write combining disabled.

Since Karmic, that bug was crushed! 

/facepalm

---

### Post by philinux on 2010-07-26
> **djk21108 said:**
> I'm on 10.04 and have an ati x1400 mobility card. 2.0 Ghz dual core processor and 2GB of RAM

ATI on linux can equal problems.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

[http://ubuntuforums.org/search.php?searchid=74830384](http://ubuntuforums.org/search.php?searchid=74830384)

---

### Post by anewguy on 2010-07-26
Try turning off compiz before you run the movie and go to full screen mode.

---

### Post by djk21108 on 2010-07-26
Disabling Compiz seems to take some strain off the video, but it's far from what it would be on lets say a windows computer.

Any other solutions?

---

### Post by djk21108 on 2010-07-26
PS:

It's issues like this that make me thing that while Linux is a very lightweight platform, it doesn't utilize modern day hardware, hence making it LESS efficient at running applications than a PC with windows installed.

Yes maybe it uses way less of my CPU, but could it ever actually utilize both of my 2.0 ghz dual core processors? 

Does this statement have merit, because I can play some pretty high quality games on my rig, but in linux I can't watch movies.

---

### Post by anewguy on 2010-07-26
I think you'll eventually find that since ATI driver support has pretty much disapeared, most people are going to nVidia - but not without its' own problems.

Dave ;)

---

### Post by Jazzy_Jeff on 2010-07-27
I have to agree here. ATI drivers and support for linux sucks. I will not buy anything with their video cards anymore.

---

### Post by clhsharky on 2010-07-27
djk21108

I have a ATI X1650 card , same generation technology as your chip all though with different hardware configuration than you. VLC, Totem movie player and Mplayer all work well with DVDs or video files at full screen.
Sounds like VLC not configured properly(not enough buffer,or using xv output).
I like Mplayer because its easer to configure.
With CompizConfig settings manager use Unredirect in general options.

Sharky

To much FUD in this thread.

---

### Post by NightwishFan on 2010-07-27
As was said, try VLC using both X11 and Xvideo. I also advise you try other players, such as mplayer/totem.

---

### Post by djk21108 on 2010-07-27
> **NightwishFan said:**
> As was said, try VLC using both X11 and Xvideo. I also advise you try other players, such as mplayer/totem.

I'm sorry to sound like a dummy, but what does it mean to use both X11 and Xvideo?

---

### Post by NightwishFan on 2010-07-27
I should clarify, try either. Xvideo has GPU acceleration, but if it is troublesome, then use x11, which uses CPU.

---

### Post by 4Orbs on 2010-07-27
You'll find those options in the vlc Tools>> Preferences>> Video>> Output Modules. Mine is set to default, which works ok... the video takes a few seconds to recover after switching to full screen. The Open GL output requires no recovery time, but still I leave it set to Default. I've never had this problem with previous versions of vlc and hopefully they'll fix it in the near future for this version. Or maybe it only needs the settings tickled a bit more.

---

### Post by djk21108 on 2010-07-27
> **4Orbs said:**
> You'll find those options in the vlc Tools>> Preferences>> Video>> Output Modules. Mine is set to default, which works ok... the video takes a few seconds to recover after switching to full screen. The Open GL output requires no recovery time, but still I leave it set to Default. I've never had this problem with previous versions of vlc and hopefully they'll fix it in the near future for this version. Or maybe it only needs the settings tickled a bit more.

Awesome Mr. Orbs, all these different modules seem to act differently, but they all offer a lot more performance than the default.

Thank you all very much!

---

### Post by anewguy on 2010-07-28
> **clhsharky said:**
> djk21108

I have a ATI X1650 card , same generation technology as your chip all though with different hardware configuration than you. VLC, Totem movie player and Mplayer all work well with DVDs or video files at full screen.
Sounds like VLC not configured properly(not enough buffer,or using xv output).
I like Mplayer because its easer to configure.
With CompizConfig settings manager use Unredirect in general options.

Sharky

To much FUD in this thread.

I have an ATI 9250 pro myself, but I hope the last line of your post is not directed at anyone posting anything about ATI in this thread.  It is a well-known fact that ATI support has slipped, that the new drivers do not support the older cards - I could go on.  If your remark was directed at someone like myself in this thread, then you need to PM me.

---

