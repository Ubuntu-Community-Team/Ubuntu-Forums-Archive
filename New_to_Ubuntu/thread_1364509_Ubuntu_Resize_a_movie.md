---
title: "Ubuntu Resize a movie"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by travmanx on 2009-12-26
I have this movie I recorded in HD, the file size it pretty big, and I want to resize it down to 320x240 for my phone. Is there a **free** way on Ubuntu to do this?
Thanks

---

### Post by droadtrip on 2009-12-26
[FONT=Georgia][SIZE=3][COLOR=DarkRed]Have you tried Kdenlive?[/COLOR][/SIZE][/FONT]

---

### Post by sangi on 2009-12-26
try [WinFF]("http://winff.org"). Search for "Video Converter" from Synaptic

---

### Post by fibercode on 2009-12-26
You might want to resize and convert the video.

You mentioned that it is in HD so I assume it is in a DVD format.

Here is how to convert and resize the video so you can watch it on your phone:

[http://dimitar.me/?p=507](http://dimitar.me/?p=507)

---

### Post by steveneddy on 2009-12-26
I use Handbrake for tasks like these:

[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)

It has a preset for iPhone and small format devices that make it a perfect application for this very task.

---

### Post by wesleybailey on 2009-12-26
Have you thought about using ffmpeg to resize the video. You could try the follow generic command, which would attempt to copy the audio/video streams, and would change the video resolution to the 320x240.



```
ffmpeg -i hd.mts -vodec copy -acodec copy -s 320x240 output.avi
```

[Install and Convert Videos with FFmpeg]("http://wesleybailey.com/articles/ffmpeg-tutorial-convert-avchd-mts-m2ts")

---

### Post by FakeOutdoorsman on 2009-12-26
> **wesleybailey said:**
> Have you thought about using ffmpeg to resize the video. You could try the follow generic command, which would attempt to copy the audio/video streams, and would change the video resolution to the 320x240.



```
ffmpeg -i hd.mts -vodec copy -acodec copy -s 320x240 output.avi
```

[Install and Convert Videos with FFmpeg]("http://wesleybailey.com/articles/ffmpeg-tutorial-convert-avchd-mts-m2ts")

You can't change the frame size without re-encoding.  I believe your *-s 320x240* option will be ignored in favor of *-vcodec copy* in your example command.

---

