---
title: "Cannot play 1080p movie well"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by paker on 2011-07-10
I am playing a 8.7 GB 1080p mkv file from hard disk. It doesn't run smooth. The movie skips frames. Do I need to upgrade hardware or software?

Intel Q9300 quad processor
GeForicee GT 240 graphics card
17" LCD monitor.
10.04 LTS
Movie player (default)
I installed video drivers based on How-To Video guide.

Thanks.

---

### Post by rosencrantz on 2011-07-10
Your specs look OK, and you do have the Nvidia drivers, right? How about a different player? MPlayer or VLC?

---

### Post by LowSky on 2011-07-10
Try using VLC, I find it much better than Movie Player (aka Totem)

---

### Post by paker on 2011-07-10
Yes, vlc plays 90% better. I am not running any other program. How do I remove the remaining skipping? 
Yes, nvidia proprietary driver installed.
All those medibuntus installed.
I noticed one thing. When I write this note, the movie skips a little. Does it mean I lack computing power or graphics power?
Thanks.

---

### Post by wildmanne39 on 2011-07-10
> **paker said:**
> Yes, vlc plays 90% better. I am not running any other program. How do I remove the remaining skipping?
Thanks.Hi, open VLC click on video 
Deinterlacing,then Blend.

---

### Post by paker on 2011-07-10
> **wildmanne39 said:**
> Hi, open VLC click on video 
Deinterlacing,then Blend.
Tried it. Still skips frames. Skipping gets worse when frames move fast like football game.
FYI: video: 1920x1080 H264 24 frames, audio: DTS DCA Stereo 48000 Hz 1536 kbps

---

### Post by casanova frankenstein on 2011-07-11
Just a thought, is it possible 3D acceleration is not activated or that you are using outdated drivers? 

Edit: Sorry but I just noticed you already have the latest video drivers installed and have shut down additional programs. I don't have any other suggestions at this point but will come back if I can think of anything.

---

### Post by abybaddi on 2011-07-11
renice the vlc to -20 and close all applications.

Open system monitor->Processes->pause the playback in vlc->In SM locate the vlc executable->Right click and change priority to very high.

---

### Post by SeijiSensei on 2011-07-11
Try installing smplayer from the repositories, then go to Options > Preferences > General > Video and choose VDPAU as your video driver.

You could also just install mplayer (for which smplayer is a GUI front-end) and use

```
mplayer -vo vdpau /path/to/movie.mkv
```

Any improvements?

---

### Post by paker on 2011-07-13
Thanks for the suggestions.
1) Changing vlc to -20: Not a noticeable difference. Selected Deinterlace to Blend. No change.
2) smplayer: it plays audio but no screen.

---

### Post by paker on 2011-07-16
All of you were indicating it wasn't a hardware problem. So I reinstalled OS. The 1080p movie plays well now. Thank you.

---

