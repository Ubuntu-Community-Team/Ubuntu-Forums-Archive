---
title: "uploading videos to youtube"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by dragon1111 on 2011-02-14
Hi i'm using ubuntu 10.10...I made a video using PiTiVi Video Editor and it turned out really good that i uploaded it to Youtube immediately.The audio seemed fine on Youtube but the images were horribly scrambled that i had to take it off.Is there anyway i can sort this out? Here's some details on the video:

Type: Ogg Theora video (video/x-theora+ogg)
Duration - 3 mins 28 sec

Video:
Dimension - 720x576
Codec - Theora
Framerate - 25 frames per second
Bitrate - N/A

Audio:
Codec - Vorbis
Channels - Stereo
Sample Rate - 44100 Hz
Bitrate - 112 kbps

---

### Post by mastablasta on 2011-02-14
try a different codec type or use some software like handbrake to save it into propper codec that will give you a better picture.

---

### Post by dragon1111 on 2011-02-14
The video turned out really good...Its only on Youtube that the images appear scrambled

---

### Post by ron999 on 2011-02-14
> **dragon1111 said:**
> ...Its only on Youtube that the images appear scrambled


Hi
Yes, YouTube doesn't like the theora content.
These two methods worked for me:-

```
ffmpeg -i foo.ogv -vcodec libx264 -vpre medium -crf 24 -threads 0 -acodec copy foo.mkv
```


```
mencoder foo.ogv -o foo.avi -ovc lavc -oac mp3lame
```

---

### Post by dragon1111 on 2011-02-14
thanks....will try that

---

### Post by dragon1111 on 2011-02-15
The terminal says foo.ogv not found..Here are the screenshots for both the commands respectively:

---

### Post by ron999 on 2011-02-15
> **dragon1111 said:**
> The terminal says foo.ogv not found..
Use your own filename!

---

### Post by dragon1111 on 2011-02-15
My filename is 'teamind'...Now the terminal says teamind.ogv not found :(

---

### Post by Paqman on 2011-02-15
Or just install Arista Transcoder. It's a really good simple video transcoding app that has a preset for Youtube. Couple of clicks and you're done. It's in the repos.

---

### Post by dragon1111 on 2011-02-15
thanks it worked :)

---

