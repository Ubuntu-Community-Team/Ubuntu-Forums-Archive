---
title: "What are some good video converters for ubuntu?"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by guitarr7 on 2009-10-08
[SIZE=4]hey.

i need some good video converters to convert avi to mp4 to put on my creative zen.
a link would be good :)[/SIZE]

---

### Post by RichardLinx on 2009-10-08
You might like: [http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)
(Avidemux)
Edit: I almost forgot! FFmpeg will be fine for your needs to:[http://ffmpeg.org/](http://ffmpeg.org/)

---

### Post by mgranet on 2009-10-08
There seems to be a very simple converter (it's actually a frontend for ffmpeg) in the repos that should suit your needs.

In a terminal:
```
sudo apt-get install winff
```

---

### Post by RichardLinx on 2009-10-08
> **mgranet said:**
> There seems to be a very simple converter in the repos that should suit your needs.

In a terminal:
```
sudo apt-get install winff
```

I think that's just a GUI for FFmpeg. You may or may not need to install FFmpeg along side winff.
```
sudo apt-get install ffmpeg
```

---

### Post by mgranet on 2009-10-08
Correct. You will need to install ffmpeg, but it will be pulled as a dependency, and will not require you to manually install.

---

