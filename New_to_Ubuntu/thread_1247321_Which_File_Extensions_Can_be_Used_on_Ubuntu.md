---
title: "Which File Extensions Can be Used on Ubuntu?"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by Unethical on 2009-08-22
Can somebody list off which video files I can play (without installing extra programs)? Ubuntu 9.04 

I tried doing a forum search, but since it only searches for tags, the results were sort of mixed up. Sorry =O.

Many thanks,

---

### Post by Codix121 on 2009-08-22
.OVG, um I think mp3's are also now standard, and AVIs and MPGs...
ahh i think that's it, but I'm not sure, lol.
I've done so much work on my linux, I hardly remember what was
originally packaged with it?

Why not just download the streamers and such, it's easy.
usually a small kb, you can try to run any type of file,
often the program will tell you, you need an extra plugin,
download it and it should be fine.

---

### Post by Revolutionary101 on 2009-08-22
These are the ones that I think work.

.ovg
.ogg
.avi (maybe)
.mkv

I know that .mp3 doesn't work neither does .mp4 so i would think that .mpg and .mp2 doesn't work either. I had to reinstall ubuntu not too long ago so I am familiar with which ones work and which ones don't.

---

### Post by Unethical on 2009-08-22
Ok thanks :] I may just end up doing some downloads in the end :P

---

### Post by Codix121 on 2009-08-22
Yeah the downloads are the easiest way,
Anything virtually possible on windows is possible on linux,
just a matter of find how and right things to download :)

---

### Post by starcraft.man on 2009-08-22
> **Unethical said:**
> Can somebody list off which video files I can play (without installing extra programs)? Ubuntu 9.04 

I tried doing a forum search, but since it only searches for tags, the results were sort of mixed up. Sorry =O.

Many thanks,

Hello fellow Canadian :)

You don't need to install extra programs, you do need the codecs though that don't come standard. If I'm not mistaken, only a handful of open codecs are available by default like Ogg movie and audio, and flac. More common formats like xvid, h264, mp3 and aac codecs are not standard, but are available from the repos. To install everything needed in one big shot, install the **ubuntu-restricted-extras** package. Alternatively, you can also install the vlc player which supports almost everything out of box. For inststructions on how to install in general, see my sig. For just a quick example, open a terminal (applications > accessories) and then type in following and return:

```
sudo apt-get install ubuntu-restricted-extras
```

Unfortunately, most of the codecs required simply aren't installed by default and probably never will be.

Edit: Also, some folks above seemed to have confused containers and codecs quite different. Just because mkv is an open format for instance univerally supported, doesn't mean it will play on a standard install of Ubuntu if it is encoded with h.264 as most mkv containers in my experience have been. Just clarifying, I'd just install the extras package and not worry about it.

---

### Post by Unethical on 2009-08-22
Thanks Starcraft.man. I will do that :]

Consider this solved. 
Thanks all.

---

