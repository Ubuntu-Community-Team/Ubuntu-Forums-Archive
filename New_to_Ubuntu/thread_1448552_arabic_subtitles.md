---
title: "arabic subtitles"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by afoda on 2010-04-06
hi all 
i just wanna ask about
**Getting Arabic subtitles working in Ubuntu** ??
i installed Arabic and Hebrew from language support but when i play a movie with Arabic ** subtitles on VLC player i get only **[B] symbols , i wanna know how to support arabic subtitles to VLC ? and btw i am a new ubuntu user totally beginner xD 
thanks all in advance 
[/B]

---

### Post by Shpongle on 2010-04-06
did you try in vlc to go to video -> subtitle track ?, have you tried more than one movie if its not a dvd ?, its possible the subtitle files can become corrupted.

---

### Post by loell on 2010-04-06
in vlc, set the default character to utf8, then install **libfribidi0**

you can install it, by invoking this command in the terminal.

```
sudo apt-get install libfribidi0
```

---

