---
title: "Extract audio only from mkv file?"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by ricardisimo on 2010-01-21
I'm trying to rip the theme music from some of my son's favorite cartoons so that I can use it on some re-edited home movies. I was thinking that I could possibly just get one audio file (either mp3, ogg, wav or flac) for the whole episode, and then trim it to the parts I need with Audacity.

Would that be the way to do it? More importantly: how do I get that one audio file? What app and what procedure? I think I managed to do it once with VLC using the "Convert/Save" functions, but after toying around with it for a few hours I produced nothing usable. Thanks for any help.

---

### Post by s.fox on 2010-01-21
Hello,

I am not sure you can get audio directly from the mkv file.  I think it will have to be done in two steps.

Step 1:

```
ffmpeg -i film.mkv -acodec mp3 -vcodec mpeg4 -sameq film.avi
```

Step 2:

```
ffmpeg -i film.avi theaudio.mp3
```

Hope this helps you.  If you run into problems please post back

-Silver Fox

---

### Post by howefield on 2010-01-21
Try this page for info.

[http://manpages.ubuntu.com/manpages/karmic/man1/mkvextract.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/mkvextract.1.html)

There are pages for other Ubuntu versions if it isn't Karic that you are using.

---

### Post by chewearn on 2010-01-21
Avidemux can extract audio from mkv.

---

### Post by mc4man on 2010-01-21
Possibly it may depend on what's in the .mkv..?

for a small clip I have ffmpeg works fine (2 audio tracks - ac3, e-ac3 

>  Stream #0.1(eng): Audio: ac3, 48000 Hz, 2 channels, s16
    Stream #0.2(eng): Audio: eac3, 48000 Hz, 6 channels, s16

Then this worked fine, and plays back correctly ect.

```
ffmpeg -i '/home/doug/Desktop/1080p.mkv' -vn -acodec copy -map 0.2:0.0 1.eac3
```

Though I'd think mkvextract would work good

---

### Post by overdrank on 2013-01-23
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

