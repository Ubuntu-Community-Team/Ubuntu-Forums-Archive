---
title: "Motorola Droid &amp; Ubuntu"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-12-07
So, I purchased one but its very particular about the video formats that you can play. Is there an application which will allow me to adjust it for optimal playback on my droid?

---

### Post by Locke_99GS on 2009-12-07
ffmpeg

---

### Post by DGortze380 on 2009-12-07
> **LunaticHiatus said:**
> So, I purchased one but its very particular about the video formats that you can play. Is there an application which will allow me to adjust it for optimal playback on my droid?

What formats do you need?

ffmpeg will convert to almost anything you need, but it's not exactly user friendly.

---

### Post by Locke_99GS on 2009-12-07
> **DGortze380 said:**
> [...] it's not exactly user friendly.

WinFF front-end for ffmpeg. It's in the repo's.

```
sudo apt-get install winff
```

---

### Post by LeifAndersen on 2009-12-07
I'm willing to bet that based on the developer documentation, he needs the files to be in this format: [http://developer.android.com/guide/appendix/media-formats.html](http://developer.android.com/guide/appendix/media-formats.html)

---

### Post by Locke_99GS on 2009-12-07
Ohh, mp4. Yay...

ffmpeg can do that, though.

```
ffmpeg -formats
``` 

will let you know what ffmpeg is capable of doing, based on the libraries (codecs) available to it.

---

### Post by LunaticHiatus on 2009-12-08
ah, many thanks. sorry, just got back from work, so I didn't get to see the responses.

---

### Post by jayboe on 2011-03-02
man ffmpeg to see recognized formats i.e. vga, qvga...

ffmpeg -i <filename> -s qvga <filename>

When I first got my droid I started using the rockplayer app in the market and it will play many formats. I still use it now after converting my video files into avi and everything works well.
I Hope this helps.

---

