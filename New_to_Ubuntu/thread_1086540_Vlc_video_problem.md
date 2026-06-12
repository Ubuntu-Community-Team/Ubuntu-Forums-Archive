---
title: "Vlc video problem"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by championboxes on 2009-03-04
Not really sure what is wrong with my vlc player because totem does not have this problem but when I play a video in vlc the sound will distort for a second and this happens all throughout the video... its kinda hard to describe the sound it makes but I doubt it is hardware related b/c I have AMD turion 2.4Ghz with 2Gig ram and Nvidia 7900GS... Ive tried reinstalling vlc and disabling desktop effects but I still have the problem... does anybody know what could be my problem? Thanks in advance

---

### Post by gdn1947 on 2009-03-04
Hi, I had very similar problems yesterday and could not fix VLC. Using MPlayer has resolved the issue. Videos play correctly under that player. Download MPlayer through Applications, Add/Remove. Hope this helps

---

### Post by championboxes on 2009-03-04
Thanks for your input I will use mplayer but I still would like to get my vlc player working b/c it seems to do better with subtitles...

should installing the new nvidia video drivers have any effect? I ask this b/c I had enough trouble getting the 177 drivers installed and working properly?

---

### Post by championboxes on 2009-03-04
Searching around on the net I found some interesting things about vlc and the terminal so I opened up a .avi file from the terminal using ```
vlc -v2 filename
``` and this is the output

```
[00000454] main audio output warning: output date isn't PTS date, requesting resampling (41641)
[00000454] main audio output warning: output date isn't PTS date, requesting resampling (41730)
[00000454] main audio output warning: output date isn't PTS date, requesting resampling (41622)
[00000454] main audio output warning: audio drift is too big (135211), dropping buffer
[00000454] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[00000454] main audio output warning: output date isn't PTS date, requesting resampling (44420)
[00000454] main audio output warning: audio drift is too big (143131), dropping buffer
[00000454] mpgatofixed32 audio output debug: libmad error: Huffman data overrun
[00000454] main audio output warning: output date isn't PTS date, requesting resampling (40324)
[00000454] main audio output warning: audio drift is too big (149497), dropping buffer
[00000454] main audio output warning: audio drift is too big (125497), dropping buffer
[00000454] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[00000454] main audio output warning: resampling stopped after 38799693 usec (drift: -100017)
[00000454] main audio output warning: buffer is 100184 late, triggering upsampling
[00000454] main audio output warning: output date isn't PTS date, requesting resampling (41680)
[00000454] main audio output warning: audio drift is too big (141406), dropping buffer
[00000454] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[00000454] main audio output warning: output date isn't PTS date, requesting resampling (41510)
[00000454] main audio output warning: audio drift is too big (153666), dropping buffer
[00000454] main audio output warning: audio drift is too big (129666), dropping buffer
[00000454] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[00000454] main audio output warning: output date isn't PTS date, requesting resampling (40204)
[00000454] main audio output warning: audio drift is too big (134661), dropping buffer
[00000454] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer

```

with the mpgatofixed32 audio output debug being every time it glitches

---

### Post by Ampi on 2010-06-06
I see there are no replies and I don't know the answer. But I have the same problem, so I was hoping to restart this topic...

---

### Post by Ampi on 2010-06-06
Okay the following seems to help, in the VLC menu:

Tools -> Preferences (Show Settings: "All") -> Input/Codecs -> Access modules
There I changed the "cache value in ms" from 300 to 5000 for ALSA, OSS and File. For now it seems to work, but I still need to see a whole video. 
But it is probably not a correct fix, so an actual fix would be nice :).

Edit: It did not entirely fix it, it does seem to stutter less, but still audio is not perfect and kind of annoying..

---

