---
title: "mkv file stops suddenly when playing in VLC"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Dangger on 2010-02-11
**UPDATE**: It's a bug so it's not solved but there's nothing I can do about it except play the file with mplayer. 

That's about it. When I try to play a mkv file it only plays for a few seconds (with audio and everything) and then stops and vlc closes. Any ideas?

---

### Post by howefield on 2010-02-11
Try running the file through terminal.

```
vlc name_of_file
```

Do you get any errors ?

---

### Post by Dangger on 2010-02-11
> **howefield said:**
> 

Do you get any errors ?

```
VLC media player 1.0.3 Goldeneye
[0x9e39e68] main interface error: no interface module matched "globalhotkeys,none"
[0x9e39e68] main interface error: no suitable interface module
[0x9d92088] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9d92088] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[***] Init
Fontconfig error: Cannot load config file "&#65533;&#65533;K
&#65533;"
[***] No usable fontconfig configuration file found, using fallback.
[***] Updating font cache
[0xa4b8e48] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:224000
[0xa503858] pulse audio output: No. of Audio Channels: 6
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[***] Glyph bounding box too large: 1349632x32px
Segmentation fault

```

Any ideas? Thanks in advance.

EDIT: I think it's a bug.

---

### Post by howefield on 2010-02-11
Looks like this one...

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/495199](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/495199)

Have you tried any other media players ?

---

### Post by Dangger on 2010-02-11
> **howefield said:**
> Looks like this one...

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/495199](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/495199)

Have you tried any other media players ?

Indeed. Thanks. On a side note, I have successfully played this file in Windows XP with VLC. It builds a cache before playing it (1.5 Gb file), which doesn't happen in Ubuntu. Just in case this is helpful.

EDIT: Playing it with mplayer was the solution.

---

