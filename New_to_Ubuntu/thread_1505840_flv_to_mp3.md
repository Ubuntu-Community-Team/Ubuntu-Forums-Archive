---
title: "flv to mp3"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by DarinB on 2010-06-09
i use karmic build of LM 8..
I used to use ffmpeg to convert flv to mp3 
but now i can not fine a gui for it????? .
afterwards i would edit with audacity. 
i wouldn't mind editing the flv but avidmux says i am missing an audio decoder for flv???

---

### Post by TeoBigusGeekus on 2010-06-09
[Mobile Media Converter]("http://www.miksoft.net/mobileMediaConverter.htm")

---

### Post by DarinB on 2010-06-09
what is the gui for ffmpeg i used to have one for earlier distros

---

### Post by dtfinch on 2010-06-09
This ought to work without any loss of quality:
ffmpeg -i in.flv -vn -acodec copy out.mp3

---

### Post by ron999 on 2010-06-09
> **DarinB said:**
> what is the gui for ffmpeg i used to have one for earlier distros

To install WinFF gui you have to follow the instructions on the website here:-[http://code.google.com/p/winff/wiki/UbuntuInstallation]("http://code.google.com/p/winff/wiki/UbuntuInstallation")

---

### Post by DarinB on 2010-06-09
thanks i added the codes from the link above and everything works great now

---

