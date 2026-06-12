---
title: "Merging mpg Files"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by 42Wired on 2010-03-23
Does anyone know of a good program to join a series of mpg files end to end? Either that, or is there a setting in k9copy I'm missing that would do it for me (ripping from a DVD)?

---

### Post by sandyd on 2010-03-23
> **42Wired said:**
> Does anyone know of a good program to join a series of mpg files end to end? Either that, or is there a setting in k9copy I'm missing that would do it for me (ripping from a DVD)?

avidemux

---

### Post by NightwishFan on 2010-03-23
If you like command line ffmpeg might help you.

---

### Post by 42Wired on 2010-03-23
avidemux seems to make the audio choppy and out of sync, and doesn't like to append all of them when it asks me. I'll try manually appending them sometime when I have two hours to watch the movie to make sure they're in the correct order.

I didn't find any commands to join mpg files on the man page for ffmpeg. Is there something I'm missing?

---

### Post by FakeOutdoorsman on 2010-03-24
You can try using cat.  The mpg format is usually cat friendly:
```
cat video1.mpg video2.mpg video3.mpg > joined.mpg
```
If it doesn't play back very well you can use FFmpeg to place the video and audio into a new container:
```
ffmpeg -i all.mpg -acodec copy -vcodec copy joineded.mpg
```
Neither of these commands will re-encode your video and audio and therefore will preserve the quality.

---

### Post by 42Wired on 2010-03-25
> **FakeOutdoorsman said:**
> You can try using cat.  The mpg format is usually cat friendly:
```
cat video1.mpg video2.mpg video3.mpg > joined.mpg
```
If it doesn't play back very well you can use FFmpeg to place the video and audio into a new container:
```
ffmpeg -i all.mpg -acodec copy -vcodec copy joineded.mpg
```
Neither of these commands will re-encode your video and audio and therefore will preserve the quality.

cat is exactly what I was looking for. Thanks!

---

