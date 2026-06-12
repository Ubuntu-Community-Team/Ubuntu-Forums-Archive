---
title: "Split Flash File"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by spikoley on 2011-03-17
I have a few flash files I want to upload to youtube, but they are too long.  How can I split them?

---

### Post by TeoBigusGeekus on 2011-03-17
Let's say that your file (video.flv) is 15minutes long and you want to split it to 3 parts of 5minutes each.
```
ffmpeg -i video.flv -ss "00:00:00" -t "00:05:00" part1.flv
ffmpeg -i video.flv -ss "00:05:00" -t "00:05:00" part2.flv
ffmpeg -i video.flv -ss "00:10:00" part3.flv
```
The -ss switch controls the seek option and the -t switch controls the duration option.

---

### Post by FakeOutdoorsman on 2011-03-17
> **TeoBigusGeekus said:**
> Let's say that your file (video.flv) is 15minutes long and you want to split it to 3 parts of 5minutes each.
```
ffmpeg -i video.flv -ss "00:00:00" -t "00:05:00" part1.flv
ffmpeg -i video.flv -ss "00:05:00" -t "00:05:00" part2.flv
ffmpeg -i video.flv -ss "00:10:00" part3.flv
```
The -ss switch controls the seek option and the -t switch controls the duration option.

You should add a few additional options so FFmpeg will copy the video and audio instead of re-encoding it:
```
ffmpeg -i video.flv -t 00:05:00 -vcodec copy -acodec copy part1.flv
ffmpeg -i video.flv -ss 00:05:00 -t 0:05:00 -vcodec copy -acodec copy part2.flv
ffmpeg -i video.flv -ss 00:10:00 -vcodec copy -acodec copy part3.flv
```

---

### Post by spikoley on 2011-03-18
> **FakeOutdoorsman said:**
> You should add a few additional options so FFmpeg will copy the video and audio instead of re-encoding it:
```
ffmpeg -i video.flv -t 00:05:00 -vcodec copy -acodec copy part1.flv
ffmpeg -i video.flv -ss 00:05:00 -t 0:05:00 -vcodec copy -acodec copy part2.flv
ffmpeg -i video.flv -ss 00:10:00 -vcodec copy -acodec copy part3.flv
```

Thanks to the both of you for the help.  It worked and it was quick.  Check out the [videos]("http://www.youtube.com/user/FAIsurgery") I uploaded.  Part 5 is the best.  Since its for youtube I just cut the 20 minute video in half with the commands below.

```
ffmpeg -i IMAGE001.flv -t 00:10:00 -vcodec copy -acodec copy FAIpart1.flv
```

```
ffmpeg -i IMAGE001.flv -ss 00:10:00 -t 0:20:00 -vcodec copy -acodec copy FAIpart2.flv
```

---

