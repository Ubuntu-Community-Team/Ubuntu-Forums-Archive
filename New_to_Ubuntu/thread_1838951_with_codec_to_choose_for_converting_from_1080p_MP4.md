---
title: "with codec to choose for converting from 1080p MP4"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by puntigamer on 2011-09-04
Hi,

I'm new to video editing in Linux, and I started to try out Pitivi. Our camera records 1080p MP4, witch looks terrible with Totem/VLC, so I would like to convert it to a smaller format, like AVI. I tried out some combination of codecs, but I couldn't find the right ones to compress MP4 into something enjoyable and editable format.
Please suggest some codecs to use or even an other video editor!

Thanks in advice!

---

### Post by TeoBigusGeekus on 2011-09-04
Try with ffmpeg:
```
ffmpeg -i /path/movie.mp4 -vcodec mpeg4 -b 2000k -vtag xvid -s 889x500 -acodec libmp3lame -ab 192k -ac 2 -ar 44100 movie.avi
```

---

### Post by bryanl on 2011-09-04
keep in mind that mp4 and avi are containers, not codecs.

The first problem to understand is why your camera file "looks terrible with Totem/VLC" - it shouldn't. (see [http://arstechnica.com/open-source/guides/2010/01/video-editing-in-linux-a-look-at-pitivi-and-kdenlive.ars](http://arstechnica.com/open-source/guides/2010/01/video-editing-in-linux-a-look-at-pitivi-and-kdenlive.ars) for some on this)

The editor should be able to import the mp4 file as is. You can then save it in another container format with your choice of audio and video codecs as supported by the editor.

Both the video and audio usually use lossy codecs. The fewer times you edit or convert them the less the quality loss. Transcoding video can take a long time as well.

ffmpeg is often the back end for many of these programs and it needs strong support in system codec library support to get best results.

---

### Post by andrew.46 on 2011-09-05
I note that TeoBigusGeekus suggested mpeg4 video, mp3 audio and an avi container which indeed should playback almost anywhere. Another option, and it depends on how you intend playing back these files, is h264 video, aac sound and an mp4 container. Mind you, as bryanl has suggested, the original video should be ok with vlc. Can your computer playback 1080 videos adequately or is it only those files sourced from your camera that fail?

---

### Post by puntigamer on 2011-09-06
> **andrew.46 said:**
> I note that TeoBigusGeekus suggested mpeg4 video, mp3 audio and an avi container which indeed should playback almost anywhere. Another option, and it depends on how you intend playing back these files, is h264 video, aac sound and an mp4 container. Mind you, as bryanl has suggested, the original video should be ok with vlc. Can your computer playback 1080 videos adequately or is it only those files sourced from your camera that fail?

Yes, I can playback 1080p videos without any problem! I will try out your suggestions, thank you very much!
I'm happy with Ubuntu since 1.5 years, but video editing on my own system was a dark hole for me :(
So only the MP4 videos from my cam fail. (I tried it out, and on W$ it's beautiful, so there is something wrong with my Ubuntu codecs or so...)

---

### Post by WasMeHere on 2011-09-14
I have had similar problems.

What speed 1080p does your camera make? My camera makes 1920x1080 50 Hz progressive (50p), which is more demanding than for example 25p or 30p. And what kind of 1080p can your computer play?

I use **OpenShot** to edit as well as convert my videos. 1280x720 30 Hz progressive (720/30p) is much easier to show on an old computer, and I think that the visual quality is quite satisfactory on a 1920x1080 screen. Furthermore, the file size is reduced. OpenShot is in the repositories.

I use **VLC 1.1** with GPU enabled and some tweaks to show HD movies.
[U][ubuntuforums.org/showthread.php?t=1830231&highlight=1080p#6](ubuntuforums.org/showthread.php?t=1830231&highlight=1080p#6)
[/U]
Have fun, and please let us know, when you have found your way to manage your videos!

---

