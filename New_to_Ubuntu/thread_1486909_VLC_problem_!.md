---
title: "VLC problem !"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-05-18
hello every buddy there..
although vlc runs almost all kind of formats, but when playing an avi file in some cases i hear only the sound but no picture.
all codecs are already installed 

what's going on?

---

### Post by Ozymandias_117 on 2010-05-18
Try opening the .avi through a terminal using verbose mode, eg. ```
vlc -v ./myfile.avi
``` and see if it throws any errors.

---

### Post by MBG1987 on 2010-05-18
> **Ozymandias_117 said:**
> Try opening the .avi through a terminal using verbose mode, eg. ```
vlc -v ./myfile.avi
``` and see if it throws any errors.

this is the output when i attempt to open avi file using vlc:

[PHP]test@mbg-desktop:/media/$ vlc -v ./optimizing.avi 
VLC media player 1.0.5 Goldeneye
[0x97ac1e0] main demux warning: no access_demux module matching "file" could be loaded
[0x9713140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9a47310] avi stream warning: unknown chunk (not loaded)
[0x9a53df0] pulse audio output: No. of Audio Channels: 1
swScaler: Palette is not supported as output pixel format
[0x9a69c18] swscale scale error: could not init SwScaler and/or allocate memory
[0x9a65498] main video output error: unknown chroma type 0x00000000 (    )
[0x9a65498] xvideo video output error: never heard of chroma 0x00000000 (    )
[0x9a65498] main video output error: plugin was unable to allocate at least one direct buffer
[0x9a65498] main video output error: video output creation failed
[0x9a4e138] scaletempo audio filter warning: bad input or output format
[0x9a4e138] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
QPainter::begin: Paint device returned engine == 0, type: 1
[0xb740dde0] main decoder error: failed to create video output
[0xb740dde0] main decoder warning: can't get output picture
[0x9a53df0] main audio output warning: PTS is out of range (83), dropping buffer
[0x9a53df0] main audio output warning: PTS is out of range (-24851), dropping buffer
[0x9a53df0] main audio output warning: output date isn't PTS date, requesting resampling (136935)
[0x9a53df0] main audio output warning: audio drift is too big (136935), dropping buffer
[0x9a53df0] main audio output warning: buffer is 72935 late, triggering upsampling
[0x9a53df0] main audio output warning: output date isn't PTS date, requesting resampling (42667)
[0x9a53df0] main audio output warning: timing screwed, stopping resampling
[0x9a53df0] main audio output warning: buffer is 115539 late, triggering upsampling
[0x9a47310] avi stream warning: unknown chunk (not unloaded)
test@mbg-desktop:/media/$ 
[/PHP]

---

### Post by Ozymandias_117 on 2010-05-18
Try going to Tools > Preferences and on the Interface tab, uncheck "Embed video in interface" exit and then try to open your video.

---

### Post by MBG1987 on 2010-05-19
it works after upgrading to lucid lynx, yet i don't know what cause this problem!
thank you

---

