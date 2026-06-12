---
title: "How to extract audio (wma) from video (wmb)?"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by paker on 2010-10-24
I have a small (30 mb) wmv file. I want to extract the audio. According to Totem Movie Player, audio is wma version 8, 48 khZ, 130 kbps. Thanks.

PS: I searched and found several threads, but they were saving inmp3 format.

---

### Post by P4man on 2010-10-24
try this:

```
 ffmpeg -i yourmovie.wmv -vn -acodec copy youraudio.wma
```

Good tutorial on ffmpeg:

[http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)

---

### Post by Verbeck on 2010-10-24
also try installing _sound converter_

---

### Post by HermanAB on 2010-10-24
Give sox (sound exchange) a try.

---

### Post by tajiknomi on 2010-10-24
[SIZE=2]*try [SIZE=2]**winff**[/SIZE]...hope it can...*[/SIZE]

---

### Post by paker on 2010-10-25
ffmpeg command copied and pasted. Worked. Thanks. A very useful program indeed. I need to check it out.

---

