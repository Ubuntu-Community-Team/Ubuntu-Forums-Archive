---
title: "Problem playing mkv file"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by mvalviar on 2010-03-11
First let me just get this out: "WHAT THE FREAKING HELL?!"

Ok, I'm having a problem. I'm trying to play an mkv file.

**Video**
*Dimensions:* 1280x720
*Codec*: H264
*Framerate:* 24 frames per second
*Bitrate:*N/A

**Audio**
*Codec:*Dobly Digital(AC-3)
*Channels:*Surround 5.1
*Sample Rate:* 48000 Hz
*Bitrate:*256 kbps

I tried totem and vlc. Both drains the CPU 100%. Please don't ask me to try mplayer I coudn't get it to play anything in 9.10.

This is just so frustrating. I have number of unresolved questions already. Then this? I'm simply trying to play a video that I believe any reliable and general consumption desktop system could do.

I could play other mkv files for some reason. Please I really don't know what to do. I'm just about ready to give up on ubuntu and linux altogether. It just seems so not worth it.

---

### Post by Daveth on 2010-03-13
which version of vlc did you use to try that file with? I find it plays most things. Can you post a link to the file so we all can try?

---

### Post by spectralblue on 2010-03-13
> **mvalviar said:**
> First let me just get this out: "WHAT THE FREAKING HELL?!"

Ok, I'm having a problem. I'm trying to play an mkv file.

**Video**
*Dimensions:* 1280x720
*Codec*: H264
*Framerate:* 24 frames per second
*Bitrate:*N/A

**Audio**
*Codec:*Dobly Digital(AC-3)
*Channels:*Surround 5.1
*Sample Rate:* 48000 Hz
*Bitrate:*256 kbps

I tried totem and vlc. Both drains the CPU 100%. Please don't ask me to try mplayer I coudn't get it to play anything in 9.10.

This is just so frustrating. I have number of unresolved questions already. Then this? I'm simply trying to play a video that I believe any reliable and general consumption desktop system could do.

I could play other mkv files for some reason. Please I really don't know what to do. I'm just about ready to give up on ubuntu and linux altogether. It just seems so not worth it.

Are you able to play the mkv in another OS such as OSX or Windows? Be sure to check before blaming ubuntu.

Next, a player is entirely different from the OS (except for ones such as WMPlayer or Quicktime), so you can't blame the OS, you have to find a suitable player or plugin. 

I haven't had any difficulty playing an mkv file with VLC at all. Perhaps your mkv file is corrupted, or encoded improperly. 

Are you able to play the file btw? You say it drains your CPU, but are you able to play it? I see that you have a 720p video - close to high def - that itself will use a lot of CPU power, and if your processor is old, then you know what would happen on that.

---

### Post by costre on 2010-03-20
If you have an Nvidia card, you can get smoother playback by using mplayer with vdpau support.

[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

---

