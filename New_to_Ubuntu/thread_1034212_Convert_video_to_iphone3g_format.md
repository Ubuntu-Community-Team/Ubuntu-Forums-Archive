---
title: "Convert video to iphone3g format"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by hermes0710 on 2009-01-08
Hi all.
  I want to convert avi files to h.264 format in order to upload them to my iphone3g. I tried many things but with no luck. 

Avidemux produces video that when played on the iphone I get only audio and a black picture.

Avidemux's version is the latest from the ubuntu repositories and what i do is the following:

I "open" the avi file, then I select "Auto>PSP>Ipod640*480" and I disable the CABAC option that is mentioned in other sites as a problematic setting for iphone3g.

Any suggestions???

---

### Post by nothingspecial on 2009-01-08
```
sudo apt-get install ffmpeg winff
```


> WinFF is probably the most user-friendly tool for converting videos and extracting audio from videos in GNU/Linux. Avidemux is a popular and useful video editing application, which makes it quite simple to cut and crop videos to your liking, and much more.

Tip: To make a video for a mobile phone in WinFF, select 3g2 as the type of video you want to make, but change the extension from ".3g2" to ".mp4" when the video is complete. To increase the audio quality of the video, click on "Options" within WinFF, and in the option labelled "Audio Bitrate", type "96000" (default is 64000, which is 64kbps). However, your phone may not play it properly with the audio at 96kbps, depends really. Test it yourself.

[COLOR="Magenta"]from Ubuntu-Freak`s excellent multimedia how-to (sticky  in the multimedia and video forum)[/COLOR]

---

### Post by Nerdriot on 2009-01-08
I highly recommend Avidemux. It converts every (that I've tested) format to any other format. I use it for PSP video, mainly, and it works perfectly.

---

### Post by hermes0710 on 2009-01-08
> **Nerdriot said:**
> I highly recommend Avidemux. It converts every (that I've tested) format to any other format. I use it for PSP video, mainly, and it works perfectly.

I tried that but on the phone i only got the audio. No video...

---

### Post by bumanie on 2009-01-08
+1 for winff. From what I have read, Iphone supports the same video format as ipod (H.264). Winff definitely converts to H.264 and has a very easy GUI to follow - just a couple of clicks does it.

---

### Post by binbash on 2009-01-08
you should try handbrake also

---

### Post by Nerdriot on 2009-01-09
> **hermes0710 said:**
> I tried that but on the phone i only got the audio. No video...

Ahh, my bad.. I read your first post too fast, and didn't see that you'd tried it already.

---

