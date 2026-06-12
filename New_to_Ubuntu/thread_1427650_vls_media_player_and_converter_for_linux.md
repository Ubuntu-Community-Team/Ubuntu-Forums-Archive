---
title: "vls media player and converter for linux"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by potato_head on 2010-03-11
p, li { white-space: pre-wrap; }  [COLOR=#000000]VLC could not open the encoder.[/COLOR]
 [COLOR=#FF0000]Streaming / Transcoding failed:[/COLOR]
 [COLOR=#000000]It seems your FFMPEG (libavcodec) installation lacks the following encoder:[/COLOR]
 [COLOR=#000000]MPEG Audio layer 1/2/3.[/COLOR]
 [COLOR=#000000]If you don't know how to fix this, ask for support from your distribution.[/COLOR]
 [COLOR=#000000][/COLOR]
 [COLOR=#000000]This is not an error inside VLC media player.[/COLOR]
 [COLOR=#000000]Do not contact the VideoLAN project about this issue.[/COLOR]

[COLOR=#000000][/COLOR]
don't have the right stuff to convert to mpeg2 
how do i get this on my machine?!?!?:popcorn:
[COLOR=#000000][/COLOR]

---

### Post by Pascal11110 on 2010-03-11
What type of media file are you trying to play?

---

### Post by mc4man on 2010-03-11
Assuming you're running karmic (9.10) then,

```
sudo apt-get install libavcodec-extra-52
```

If you're running something else say so.

If you're on karmic and also wish aac encoding enabled then add  medibuntu as a source and install their extra version

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by potato_head on 2010-03-12
[COLOR=#ff0000]Streaming / Transcoding failed:[/COLOR]
 [COLOR=#000000]VLC could not open the encoder.[/COLOR]


[COLOR=#000000]that helped but didn't totally fix the problem:popcorn:
[/COLOR]

---

### Post by 2hot6ft2 on 2010-03-12
See if this fixes your problem
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by potato_head on 2010-03-12
now i am back to the same message

[COLOR=#000000]VLC could not open the encoder.[/COLOR]
 [COLOR=#ff0000]Streaming / Transcoding failed:[/COLOR]
 [COLOR=#000000]It seems your FFMPEG (libavcodec) installation lacks the following encoder:[/COLOR]
 [COLOR=#000000]MPEG Audio layer 1/2/3.[/COLOR]
 [COLOR=#000000]If you don't know how to fix this, ask for support from your distribution.[/COLOR]
 
 [COLOR=#000000]This is not an error inside VLC media player.[/COLOR]
 [COLOR=#000000]Do not contact the VideoLAN project about this issue.[/COLOR]

---

### Post by 2hot6ft2 on 2010-03-12
Ok, back to the [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

It should surely fix you up.

--PART 1/5, ESSENTIAL PACKAGES--
--PART 2/5, AUDIO & VIDEO STREAMING--
--PART 3/5, AUDIO & VIDEO CONVERSION--
--PART 4/5, DVD PLAYBACK/RIPPING/BURNING--
--PART 5/5, MISCELLANEOUS & TROUBLESHOOTING--

---

