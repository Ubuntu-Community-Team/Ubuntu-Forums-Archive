---
title: "Can only play avi format movies."
date: 2011-08-17
forum: New to Ubuntu
---

### Post by Neoncamouflage on 2011-08-17
I run Ubuntu 10.10. I have the restricted extras installed, I've tried the standard movie player and VLC. I cannot play any sort of video file unless it is in .avi format, then the standard movie player will play it. If I place a dvd/blu-ray in the cd tray (and yes it reads both) then it cannot play them, if I download other movie formats then it is unable to play them.

I would really like to be able to actually watch my movies on Ubuntu, but as it is I can only play them on my Windows computer. Any suggestions?

---

### Post by nomko on 2011-08-17
Did you also installed the extra multimedia files from Medibuntu?
Check my English site where you can read how to add multimedia.

---

### Post by mastablasta on 2011-08-17
also i am not sure blu ray is alrady supported. i could be wrong though...

---

### Post by nomko on 2011-08-17
Did you checked the section about full DVD playback? If you follow the instruction of how to get full dvd playback, it migth help you.

---

### Post by seawolf167 on 2011-08-17
You should get a couple extra items:

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
sudo apt-get install vlc
```Then see if you can play the dvds, video files with mplayer or vlc

---

### Post by Neoncamouflage on 2011-08-17
I had already installed vlc and the restricted extras, and I update just as part of my daily routine when I turn on the computer, so it wasn't that. I went through the site for dvd playback and was able to watch a movie that I had tried repeatedly before, so I'm quite happy about that. Have not gotten around to trying a blu-ray again yet but hopefully it's all fixed now. Thanks guys.

---

### Post by seawolf167 on 2011-08-18
> **Neoncamouflage said:**
> I update just as part of my daily routine when I turn on the computer

Just want to make sure when you "update" you do the update & upgrade right?

```
sudo apt-get update && sudo apt-get upgrade
```

If everything has been worked out, please mark the thread as solved

---

