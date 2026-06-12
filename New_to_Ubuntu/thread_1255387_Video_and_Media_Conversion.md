---
title: "Video and Media Conversion"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by mikko3024 on 2009-09-01
I'm trying to migrate from Windows to Ubuntu and there are still things on Windows that I need to find a good (or better equivalent) on Ubuntu.

Are there any applications for Jaunty that can do functions and features like in Any Video Converter Professional. <snip>

I used it in Windows Vista/Windows 7 for converting videos to different formats.

But most often, I use Any Video Converter Professional to change a video's compression [Codec], bit rate, resolution, frame rate, audio bit rate, sample rate etc.

The converted media are usually played on mobile phones (supporting .avi containers and divx or xvid compression) and other portable devices/

I tried installing the above thru WINE ( 1.1.28 ) but it won't work.

---

### Post by LowSky on 2009-09-01
Handbrake is one of the best I have seen, and it works on Windows/ Mac, and Linux.

[http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)

---

### Post by isparkes on 2009-09-01
I use Avidemux. It's a little hard to get going with, but it can do most things. (I use it to reformat video for the iPhone).

---

### Post by mikko3024 on 2009-09-01
Thanks! I'll try them out.

---

### Post by andrew.46 on 2009-09-02
Hi mikko,

> **mikko3024 said:**
> Any Video Converter Professional. <snip>

I have taken the trouble to download this product and have a look at it. Are you aware that this software contains binaries of FFmpeg, MPlayer, MEncoder amongst others and violates the required license for distributing such programs? I have also searched the documentation that comes with the program as well as scoured the website and I can see no reference to FFmpeg, MPlayer or Mencoder.

My apologies to yourself if you were not aware of these facts but IMHO this is not a program that one can recommend.

Andrew

---

### Post by hovzio on 2009-09-02
> **isparkes said:**
> I use Avidemux. It's a little hard to get going with, but it can do most things. (I use it to reformat video for the iPhone).

hi, i have tried to do this with avidmux... without a proper result. (iphone mp4 conversion) do you mind shareing your configuration of avidmux. I for one would be very greatful. ;)

---

### Post by 3rdalbum on 2009-09-02
Go right to the source, and use ffmpeg on the command-line. It's not difficult, and you get as much control as you'd ever want. You can also write scripts to batch-encode files, and run multiple instances with different files to use multiple cores.

---

### Post by bumanie on 2009-09-02
You could also try winff which is a GUI for ffmpeg. As stated by andrew.46, any video converter is basically using all linux binaries 'under the hood' - what it can do, can be done in linux. I have not delved into the licence agreement, but suspect andrew.46 is likely correct in his assessment.

---

### Post by mikechant on 2009-09-02
The DVD creating software DeVeDe is great for creating simple DVDs but is also a very simple way to convert miscellaneous video files to mpeg.

---

### Post by keiichidono on 2009-09-02
Handbrake or Avidemux will both do what you want, use whichever you prefer.

---

### Post by aeiah on 2009-09-02
if you're converting with the same quality each time then using a ffmpeg or mencoder command might be worth the initial effort. once you've nailed the settings you can use nautilus-actions to use it in your context menu. so, you can just select a video, right-click and select 'encode for mobile device' or whatever you choose to call it.

---

