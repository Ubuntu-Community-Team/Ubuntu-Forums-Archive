---
title: "codes keep programs from running in ubuntu 8.10"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by thomz92 on 2009-03-07
Hi! Ubuntu newbie here. I had ubuntu 8.10 on my computer and i tried to install DVD codecs. I did that by sticking in a DVD, waiting for it to ask me if i wanted it to search for codecs, and checking BOTH boxes (could that be what I did wrong??) Anyhow, many of my games stopped working, or if they did work, the sound doesn't work. It worked fine again after I restarted the computer, but it quits later on (seemingly after it goes into standby mode).

I reinstalled ubuntu 8.10, and got everything working again. Then I decided to download vlc media player and ardour2. And it happened again!! I'm going crazy because i dont want to spend hours reinstalling, upgrading, and downloading again!! Please help!

P.S. - update, sorry about the spelling error in the title

---

### Post by simtaalo on 2009-03-07
follow the instructions here
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Redache on 2009-03-07
Need a bit more information:

What Games are you trying to run? 
Are you using Wine to try and run them?

It could be that the Codecs are causing issues with Wine if you're using it.

---

### Post by thomz92 on 2009-03-07
im running ubuntu (by that i mean that they are in add/remove programs) games such as glest, torcs, gl-117, etc

---

### Post by thomz92 on 2009-03-07
ok. the problem is, I already have some codecs (or something) that are already installed and didnt come off when i uninstalled vlc media player and ardour. I need to figure out how to get them OFF, not on!

---

### Post by simtaalo on 2009-03-07
substitute "purge" for "install" in those tutorials and will make sure you get rid of everything

---

### Post by thomz92 on 2009-03-09
hi again! i read through the manual, but it didn't really get me the answer im looking for. the problem is, im not sure which codecs (or if it IS even codecs) are causing the problem. i have an idea its one of the codecs that comes with vlc media player, but doesn't come off when you uninstall vlc media player.

maybe if i had a list of what packages are installed with vlc media player, then i could just remove all of them completely. Do you have any other ideas?

---

### Post by thomz92 on 2009-03-09
Does ANYONE have an idea? i could really use some help here because i have to restart my computer every time i want to listen to music or play a game. the other programs seem to run fine, though. please help!

---

### Post by thomz92 on 2009-03-14
i have here a list of errors that i get when i try to open glest in the terminal:

ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
AL lib: alsa.c:344: Could not open playback device 'default': Device or resource busy
AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busy
OpenAL Vendor: Exception: Couldn't open audio device.

does anybody know what this means?

---

