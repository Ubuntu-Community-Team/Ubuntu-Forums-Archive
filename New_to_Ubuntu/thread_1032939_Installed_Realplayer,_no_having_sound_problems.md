---
title: "Installed Realplayer, no having sound problems"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Caletara on 2009-01-06
I wanted to be able to play my RM files, so I installed realplayer 11. Big mistake. The sound didn't sync up and all my sounds in my AVI files, MPGS, OGGS, and on YT were loud and choppy and staticy. I installed it as a .bin file I think, so I can't uninstall realplayer by synaptic. I manually deleted real through terminal in opt/real/realplayer, but it's not all gone. I'm still having the problem, and some parts of real player are still on my computer. I'd like to be able to play my RM's, but at this point I think I'd settle for having my computer back to normal. How do i uninstall?(and if you all know a good way to play RM's without realmedia I'd be much appreciated!)
Thank you! I'm on Intrepid.

---

### Post by boglio on 2009-01-07
As far as playing RM files, I think you could download the codecs from [www.mplayerhq.hu](www.mplayerhq.hu) and extract them to /usr/local/lib/codecs/ and use MPlayer.

edit: Here is the codec pack that i always use without problems

[http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2)

---

### Post by Caletara on 2009-01-07
Thanks so much! I tried to extract them, but I don't seem to have a file named usr/local/lib/codecs. I have usr/local/lib/python. Should I try and go into terminal and make one or did something screw up Intrepid?

---

### Post by evilkastel on 2009-01-07
NO NO, thats not the way.
Install mplayer from synaptic.
Have you the medibuntu repos? If not, get them. [www.medibuntu.org](www.medibuntu.org)
Then do
```
sudo apt-get install w32codecs
```
if you are on a 32 bits ubuntu, Or
```
sudo apt-get install w64codecs
```
if you are in a 64 bits ubuntu. 

Then open Mplayer, and in the codecs tab, coose Realvideo codec.
In audio tab Set audio to pulse.
In video tab set X11
if you get an error msg try changing the video tab and audio tab options.

---

### Post by LowSky on 2009-01-07
Also Realplayer is availible as a deb file from their website. which make is easier to install and remove 

.deb files are the prefered option for installing any software not in the repos

also check out a website called [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by Caletara on 2009-01-07
Thanks so much! I can play realplayer files now, but the sound is still off from the video. It doesn't line up. Is there a way to fix that? Also, do you know how to uninstall the rest of realplayer from my system? That might be what's doing it. Ever since I installed realplayer the sound is very loud and still choppy and has to be manually adjusted, it effects my videos, my mp3's, everything except DVD's. It's actually so bad I'm ready to just reinstall ubuntu and start fresh.

---

### Post by evilkastel on 2009-01-07
.rmvb stands for real media variable bitstream. this "variable bitstream" creates a lot of sync issues with audio/video. I have those issues when i forward or rewind the video, but if i play it from beginning without touching it, it will play sync'd. If you get Miss sync from beginning maybe the issue is with the file and not your pc.

---

### Post by Caletara on 2009-01-07
Ahh i get it! thanks. It is when I forward or rewind the video. Do you know how to uninstall realplayer though? I feel dirty with it on my computer!

---

