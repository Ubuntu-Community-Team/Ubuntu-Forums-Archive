---
title: "Like to know what is the best video converter to use ?"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2009-07-05
Hi,

I'm looking for a video converter that is easy to use and can convert video files in to commonly used formats. I tried hand break but it doesn't support hardy on it's GUI I didn't try the CLI 'cos I'm not much familiar with it. So can any one help me out with this I like the function in handbreak if some one can tell is there something similar to that and easy to use.

---

### Post by 3rdalbum on 2009-07-05
Just answered in this thread:

[http://ubuntuforums.org/showthread.php?t=1204631]("http://ubuntuforums.org/showthread.php?t=1204631")

FFmpeg on the command-line is very useful and very powerful, too. And not difficult if you know what codecs you want to use.

---

### Post by credobyte on 2009-07-05
WinFF + ffmpeg :-\"

---

### Post by powel212 on 2009-07-05
Avidemux is in the repositories. I use it everyday. It is absolutely awesome. Eay to use GUI, uses ffmpg as back-end.

If you don't find it easy to use initially just check out a tutorial.

Powel

---

### Post by Abu_Dayya on 2009-07-05
I use Avidemux. Its a little hard to use as it gives you too many options for someone not as tichnical with multimedia formats as I am, but its very powerful

---

### Post by powel212 on 2009-07-05
Well I tried to convert flv in Avidemux and failed so I tried GOM in Wine and failed again.

So I tried Kdenlive and finally found success.


KdenLive is also in the repositories.

Powel

---

### Post by powel212 on 2009-07-05
after updating to Mobile Media Converter 1.4.3

Found success again

Powel

to install MMC on 64Bit ubuntu download the package and drop it in "root" /

then run

```
sudo dpkg --force-architecture -i /mmc_1.4.3_i386.deb
```

Powel

---

