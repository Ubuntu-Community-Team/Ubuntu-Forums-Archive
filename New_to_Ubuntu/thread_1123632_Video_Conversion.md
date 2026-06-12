---
title: "Video Conversion"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by clive littlewood on 2009-04-12
Hi All

I've just installed pytube to convert flv files to Mp4 (ipod)

The app runs and i can input a file for conversion then when i press convert nothing happens.   :mad:

Any thoughts or suggestions for an alternative app.

Regards

Clive

---

### Post by t0p on 2009-04-12
**ffmpeg** is good.  It's available through synaptic, or in a terminal type
```
sudo apt-get install ffmpeg
```

---

### Post by lolol i r linux noob on 2009-04-12
why dont you use media-convert
its online and it has pretty much every video/music/file format you need

---

### Post by kamitsukai on 2009-04-12
Handbrake is by far the best ([http://handbrake.fr/]("http://handbrake.fr/"))

---

### Post by clive littlewood on 2009-04-12
Hi

Thanks for the input.

I've just installed Winff from synaptic which uses ffmpeg and have just converted my 1st file.    :p

Regards

Clive

---

### Post by bumanie on 2009-04-12
I've used winff which is a gui front end for ffmpeg - it seems to work well. Get the .deb from [here]("http://www.biggmatt.com/category/winff/")

---

### Post by perspectoff on 2009-05-02
> **bumanie said:**
> I've used winff which is a gui front end for ffmpeg - it seems to work well. Get the .deb from [here]("http://www.biggmatt.com/category/winff/")

WinFF is in the Jaunty repositories and is indeed the easiest way to convert video files.

The command line method to convert Flash to mp4 is:

```
ffmpeg -i samplevideo.flv outputfile.mp4
```

Pretty easy, really.

---

