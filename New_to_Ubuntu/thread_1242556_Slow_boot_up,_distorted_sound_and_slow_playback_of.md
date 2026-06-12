---
title: "Slow boot up, distorted sound and slow playback of video"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by Kapli on 2009-08-17
New to ubuntu, so far pretty happy about the change from windows but there's a few things annoying.

First of all the boot time used to be really quick, then I was trying to fix my SD card not being recognized when inserted into my card reader in my dell computer. I gave up trying to fix this because I figured I could just use the usb cable to connect with my camera. While trying to fix it I think I installed some packages, I can't recall exactly what I did, so I was wondering if there are some logs or something to troubleshoot the boot up. 
The orange boot up fills about 2 and a half bars and then it hangs for a while, then the rest goes fast. So it's hanging at one point, and it didn't do that before.

Edit2: I think I fixed this by doing sudo apt-get remove usbmount, not sure if it as fast as it was when I first installed ubuntu, but at least it isn't hanging on 2,5bars anymore so I'm satisfied.

Second problem is with my sound. I have actually tried 09.04 two times, 08.10 once and now I'm in 08.04 for the second time (gfx driver issues is the reason I went from version to version). Every time I had a problem with my sound, it's not a big problem but an annoying one. Sometimes it happens, sometimes it doesn't. I can hear it very clearly when I go into System -> Preferences -> Sound and click on the test button. I am using a headset and it varies from my left ear to my right ear, usually it is in my left ear. The sound is distorted or something, I do not know how to properly explain it but it's you know.. broken. Rebooting usually fixes the problem. 

Third problem is with video playback, currently I've tried MPlayer, VLC and the default Totem player. I watch a lot of anime so there are quite a few different extensions to deal with. It's not that bad, it's just that it was better on windows. mkv, mp4, avi, all of it plays normally it's just something with the frames that seem to be lagging or something, it's a bit difficult to explain.

Edit: Got another problem now :( 
I play only one game and that is Heroes of Newerth and it has a native linux client. I had the proprietary drivers for my ATI x600 installed through hardware drivers, and the game was working good. The game had some bugs, and the developer on the forums told me to update my drivers to catalyst 9.3 which is the latest for my card, the drivers installed via hardware drivers were of catalyst version 8.10 I believe. Anyway, I uninstalled the drivers via hardware drivers, then i rebooted, then I installed catalyst 9.3 which I downloaded from the ATI site, installed it, rebooted, tried to play Heroes of Newerth but performance was way worse than on the previous drivers. Uninstalled it via /usr/share/ati/fglrx-uninstall.sh, rebooted, installed the old drivers again via hardware drivers, rebooted and then tried to play Heroes of Newerth, but the performance was now very bad again. 
Any idea what I've done wrong? Last time this happened I reformatted, but this time I've been here for a few days and yeah I don't want to start over again.
Edit3: Fixed this by completely removing everything that had anything to do with ATI drivers and then reinstalled, working now.

But I thought I would add another problem that I just recalled, my microhpone does not seem to work properly. There's a screeching sound in the background when I try to record. Might also add that my microhpone worked perfectly in 08.10 and in 09.04. Owh and of course the reason I can't use 09.04 is because catalyst 9.3 doesn't support the new Xorg there or something like that.

Edit4: I also have a problem with scanning, I can use the preview and it scans properly, but when trying to scan I get Error during read: Error during device I/O. I have a Canon PIXMA MP160 and scanning worked under 08.10 and 09.04.

Please tell if there's any additional information you need to help me solve my problems, and thanks in advance :)

---

### Post by Kapli on 2009-08-17
Bump

---

### Post by Kapli on 2009-08-17
Another bump; Also got another problem with the sound that I just noticed, if I'm listening to music and trying to view a video on youtube at the same time there won't be any sound on youtube. I googled a bit and installed alsa-oss but I'm not sure what else to do.

---

### Post by Kapli on 2009-08-18
Another bump :o

---

### Post by Kapli on 2009-08-19
Last bump;
I splitted this post and posted in the correct sections.
Scanning problem: [http://ubuntuforums.org/showthread.php?t=1244433](http://ubuntuforums.org/showthread.php?t=1244433)
Sound, video and microhpone probelms: [http://ubuntuforums.org/showthread.php?t=1244449](http://ubuntuforums.org/showthread.php?t=1244449)

---

