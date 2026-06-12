---
title: "youtube-dl help"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-10-19
can anyone help  me out? I can normally download videos and all but some movies need confirmation. How do i download videos when it needs password and username?

---

### Post by martrn on 2009-10-19
[http://www.susegeek.com/multimedia/youtube-dl-download-videos-from-youtube/]("http://www.susegeek.com/multimedia/youtube-dl-download-videos-from-youtube/")

See half-way ~(50%) down the page.

---

### Post by Excedio on 2009-10-19
You could always just go to the Youtube site of the video...wait for it to finish loading...then go to your /tmp folder. The video will be there.

---

### Post by super kim on 2009-10-19
i use firefox, with download helper, it's the bees knees for downloading youtube

---

### Post by andrew.46 on 2009-10-20
Hi 289531.EXE,

I see your question has already been answered but you might want to think about updating the rather ancient copy of youtube-dl that ships from Ubuntu by doing something like the following:

```
$ sudo apt-get remove youtube-dl
$ wget http://bitbucket.org/rg3/youtube-dl/raw/2009.09.13/youtube-dl -O /usr/local/bin/youtube-dl
$ sudo chmod +x /usr/local/bin/youtube-dl
```

and just have a bit of caution with downloading these videos as the terms of usage seem to indicate that You-Tube would prefer them to be only viewed online.

Andrew

---

### Post by 289531.EXE on 2009-10-24
thanks!

---

