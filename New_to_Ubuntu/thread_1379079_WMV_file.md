---
title: "WMV file"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by dunbrokin on 2010-01-12
Both my computer and my wife's computer are running 9.10. Both have restricted codecs and Medibuntu installed. I can get the wmv file to play both video and audio on my PC. She can only get it to play the audio on hers...I have tried it on her machine with both VLC and Movie Player...but neither can get the video to work. What am I doing wrong.

---

### Post by HiImTye on 2010-01-12
try executing it from a shell and see what the output is
```
vlc /path/to/file
```
I believe would be the command to use, I don't have vlc installed, myself

I know 'movie player' would be
```
totem /path/to/file
```

---

### Post by kenox on 2010-01-12
as mentioned try ```
vlc /path/to/file
```
and check for errors

Also in vlc under tools -> preference checkout the video settings 
Change the value of output to "Default", X11,OpenGL, etc save and try again!!

---

### Post by dunbrokin on 2010-01-12
Thanks....changing ghe setting in VLC to X11 worked.

---

