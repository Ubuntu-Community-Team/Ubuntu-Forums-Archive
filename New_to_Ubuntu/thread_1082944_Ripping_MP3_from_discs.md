---
title: "Ripping MP3 from discs"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by fishman78 on 2009-02-28
**Solved**

Hi All,

   I have run into a little problem with ripping my cd's to MP3's.  Every app. I install has the same results, there is no option for MP3's.  I can rip flac, ogg, etc, but no mp3.  Am I missing a package or something.  I have to use MP3 format.  I've tried GRIP and Audio CD Extractor, but when I go to preferences to change the format to MP3, it's not there.  Any ideas of what I'm doing wrong?  Thanks for the help!!

fishman78

---

### Post by anjilslaire on 2009-02-28
```

sudo apt-get install lame

```

then check for the mp3 codec in your ripping app.

---

### Post by fishman78 on 2009-02-28
> **anjilslaire said:**
> ```

sudo apt-get install lame

```

then check for the mp3 codec in your ripping app.

Thanks!  that seems to be working.  Now is there anyway to raise the bit rate from 128 to something a little higher?  Thanks again!

fishman78

Ahhh, nevermind, I found it!  Thanks again for your help!!

---

