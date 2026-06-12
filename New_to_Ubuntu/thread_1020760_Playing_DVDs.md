---
title: "Playing DVDs"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by newto on 2008-12-24
I'm having trouble playing DVDs on my fresh Ubuntu install. The Movie Player just opens then crashes. I downloaded some codecs but it still behaves the same way. I downloaded VLC media player but that behaves the same way. 

Also with Bittorent, which movie types should I be downloading? Example .wmv, .avi if I can't get DVDs to work?

---

### Post by StOoZ on 2008-12-24
in terminal:
[PHP]sudo apt-get install ubuntu-restricted-extras[/PHP]

---

### Post by namdung on 2008-12-24
Is the issue with one particular DVD or all DVDs? 
Are you able to play other movie/audio formats like avi, mpeg, mp3, wav etc?
Which version of Ubuntu?

Downloading movies if illegal should not be encouraged in this forum.

---

### Post by newto on 2008-12-24
Thanks but it isn't working, is it possible Ubuntu isn't recognizing them as DVDs? or is there something else I'm doing wrong?

---

### Post by kansasnoob on 2008-12-24
> **newto said:**
> I'm having trouble playing DVDs on my fresh Ubuntu install. The Movie Player just opens then crashes. I downloaded some codecs but it still behaves the same way. I downloaded VLC media player but that behaves the same way. 

Also with Bittorent, which movie types should I be downloading? Example .wmv, .avi if I can't get DVDs to work?

Where you say it "crashes" I'm not sure this will be of any help, but I always install libdvdcss2. I used to install the whole Medibuntu repo but now I just install the separate libdvdcss2 and w32codecs packages:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by newto on 2008-12-24
> **namdung said:**
> Is the issue with one particular DVD or all DVDs? 
Are you able to play other movie/audio formats like avi, mpeg, mp3, wav etc?
Which version of Ubuntu?

Downloading movies if illegal should not be encouraged in this forum.

I just put in an Audio CD and it worked.

---

### Post by newto on 2008-12-24
Thanks all, I managed to get it working.

---

### Post by theozzlives on 2008-12-24
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by namdung on 2008-12-24
> **newto said:**
> Thanks all, I managed to get it working.

Glad to a see a happy Ubuntu user. Now pls mark the thread as SOLVED if you're satisfied.

---

