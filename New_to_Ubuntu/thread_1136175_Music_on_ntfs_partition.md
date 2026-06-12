---
title: "Music on ntfs partition"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by ricardo_sdl on 2009-04-24
Hi guys! My laptop has windows xp and ubuntu 8.10 installed on a dual boot configuration. My music files stay in the windows partition (ntfs), sometimes the music suddenly stops playing, I'm using audacious to play the files. After the stop just rebooting the laptop to get this working again. Anyone can tell me whys this happens?
Thanks in advance.

---

### Post by a7j_72 on 2009-11-20
I was having a similar problem w/ 9.04...
 when I would mount my Windows partition and play music off of it, on Audacious2, playback would suddenly stop. 
Hitting play would resume the song from the beginning 

I thought It would be better If it was read locally from my ext3... so I transfered my whole music lib. without any result. 

Next, I checked all my alsa settings. (alsa was running smoothly). 

*****************

Now I have installed 9.10 Studio using pulseaudio settings.
I still have the same issue.
All my files are local on ext4
& audacious2 just randomly stops playback.

****************

I believe its an audacious problem... since I dont have this issue w/other software.
I really liked the look and feel of audacious. If anyone know how to fix this... help would be appreciated

---

### Post by arnab_das on 2009-11-20
> **ricardo_sdl said:**
> Hi guys! My laptop has windows xp and ubuntu 8.10 installed on a dual boot configuration. My music files stay in the windows partition (ntfs), sometimes the music suddenly stops playing, I'm using audacious to play the files. After the stop just rebooting the laptop to get this working again. Anyone can tell me whys this happens?
Thanks in advance.

try installing ntfs-config

---

