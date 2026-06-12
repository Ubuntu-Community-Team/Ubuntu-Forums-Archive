---
title: "Where is a streaming audio/video file is stored to take it?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Ubunser on 2010-05-01
Here is a link [http://global.g12life.net/modules/mod_rar_radio/tmpl/player/player.php?radio=http://radio.g12life.net:8000/live.mp3&url=http://radio.g12life.net/&ancho=330&stream=0&logo=/modules/mod_rar_radio/tmpl/imagenes/logo.jpg&alt=Radio%20Transformation%20Center](http://global.g12life.net/modules/mod_rar_radio/tmpl/player/player.php?radio=http://radio.g12life.net:8000/live.mp3&url=http://radio.g12life.net/&ancho=330&stream=0&logo=/modules/mod_rar_radio/tmpl/imagenes/logo.jpg&alt=Radio%20Transformation%20Center)

And I need to do with it what I usually do with embedded flash files - I take them in tmp folder. But I didn't find streaming items there. So help:confused:

---

### Post by karthick87 on 2010-05-01
Try these bash script to download streaming videos.

---

### Post by Ubunser on 2010-05-01
> **getyourkarthick said:**
> Try these bash script to download streaming videos.

WHAT SHOULD i DO WHITH IT?

---

### Post by cariboo on 2010-05-01
You could use streamtuner/streamripper to save the file. Streamtuner is in the repositories,  it automagically installs streamripper and audacious. Once installed, all you have to do is click the record button.

---

### Post by mc4man on 2010-05-01
If you can't get it(rippers) working then you should be able to find any number of ways using the stream url (you could even simply wget it or set up a cron job

```
http://radio.g12life.net:8000/live.mp3
```

As far as firefox the stream is cached in ~/.mozilla/firefox/<whatever>.default/Cache
here it's the one highlighted in screen - if you were to copy that file and rename whatever_you_wish.mp3 then it's playable in any player

---

### Post by karthick87 on 2010-05-01
> **Ubunser said:**
> WHAT SHOULD i DO WHITH IT?


Just go to the site and execute the bash script..

---

