---
title: "Weird Video Problem"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by D3SI on 2010-11-01
So I was watching film on my PC (scott pilgrim vs. the world) 720 BRRip, using VLC player

i noticed that when there were fast scenes picture kinda gets cut of from the middle and stuff, something like frame drop but not exactly same.

tried in Windows 7 and no problem at all..

Edit: i also tried other videos like Dexter (TV Show)  720 .mkv file and same problem.


any fix to this?  can't post screen shot because when i pause the video picture is fine.

PC Specs:
Q8200 Quad
Nvidia 8600GT
6GB RAM

---

### Post by papibe on 2010-11-01
It looks like that is due to the lack of video hardware acceleration. As far as I known, the repository version of VLC is a little behind the windows version (which has experimental support for it).

The easiest way to get good HD play is:
[LIST=1]
[*]Install the nvidia driver.
[*]Install libvdpau1.
[*]Install mplayer (excellent player, but complicated interface).
[*]Install smplayer (nice GUI for mplayer).
[/LIST]
After that you open smplayer and go to Options -> Preferences -> General -> Video tab. Select vdpau as Output driver.

That should do it. Use smplayer to see your HD movies.

Good Luck!

---

### Post by D3SI on 2010-11-02
mplayer was already installed

unless you are referring to **mplayer Media Player**?

---

### Post by papibe on 2010-11-02
> **D3SI said:**
> mplayer was already installed...

Nevertheless, nvidia harware acceleration (vdpau) on mplayer is only achievable with both the nvidia driver, and libvdpau1.

VLC is not "related" to mplayer. It won't change playing quality if mplayer is installed.

Regards.

---

### Post by D3SI on 2010-11-02
done everything in earlier post and tried the mkv file in smplayer and still same problem.

---

### Post by P4man on 2010-11-02
It doesnt sound like frameskipping due to cpu load/VDPAU. His cpu is probably fast enough to do it without VDPAU. Sounds more like tearing due to vsync? If you are using compiz (desktop effects), try installing ccsm and experiment with

Settings -> General Options -> Display Settings -> Sync To VBlank

Or set it in your nvidia drivers and turn desktop effects off to see if that solves it.

---

### Post by D3SI on 2010-11-02
@p4man have tried you solution yet but just noticed that its same with even YouTube videos :|

---

### Post by D3SI on 2010-11-02
bump...

---

### Post by D3SI on 2010-11-06
bump...

---

