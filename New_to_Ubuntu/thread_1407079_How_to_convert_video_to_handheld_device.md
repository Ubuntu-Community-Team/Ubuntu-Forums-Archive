---
title: "How to convert video to handheld device"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by gigaferz on 2010-02-14
OK!!!   so i use miksoft mmc to convert movies and videos to psp and cell phones.

  But i know there are some settings that will convert the video to be played in a psp and ipod.

  I was looking at the ********* and the videos in there can be played in those devices.

 I can only convert them for one device, then i have to convert them for the other.

  I just want to save time and space in my hd.

Setting that will work in both devices.

no problem if i have to go into the command line!!!

help me please!!!!

---

### Post by bwhite82 on 2010-02-14
Could you clarify your question please? Basically you need to convert your video files to .mp4 for portable devices. Did you need to know how to do that?

---

### Post by gordintoronto on 2010-02-14
ffmpeg is *the* program for converting video.  It's a command-line program, but there is a GUI "wrapper" for it called Video Converter.

---

### Post by gigaferz on 2010-02-14
ok, i already convert files to mp4.

I use miksoft mmc.

But the file i convert only plays in 1 device either psp or ipod.

Looking at the ********* there are video files that play in psp/ipod and zune.  

I want to convert a file so i can play it on those 3 devices.  I do not want to do it several times.


what are the settings so i can do 1 conversion to play in those handheld devices?

I do not want to do 2 or 3 conversions anymore.

If possible of course

---

### Post by thatguruguy on 2010-02-14
> **gigaferz said:**
> ok, i already convert files to mp4.

I use miksoft mmc.

But the file i convert only plays in 1 device either psp or ipod.

Looking at the ********* there are video files that play in psp/ipod and zune.  

I want to convert a file so i can play it on those 3 devices.  I do not want to do it several times.


what are the settings so i can do 1 conversion to play in those handheld devices?

I do not want to do 2 or 3 conversions anymore.

If possible of course

I don't know what you are looking at wherein there are video files that play in psp/ipod and zune. If you could be more explicit, maybe I can figure out how to help.

---

### Post by thatguruguy on 2010-02-14
I assume that the files on the place you've mentioned are in h.264 format.

You may want to try WinFF (which is just a front-end for ffmpeg) and try to encode for an iPod and see if it works on all 3 devices.

---

### Post by lijcam on 2010-02-15
Ok so I think your trying to ask "How do I encode a video to play on multiple devices that require different codecs, resolutions and bit rates etc... " Answer, sorry but this is not possible.

However device manufactures are finialy starting to see the craziness of this situation and are starting to standardise. For example the ipod touch, Iphone, Android Phones, Symbian Phones, etc all support 480p mp4 with aac or mp3 sound tracks.

I use handbrake for video encoding and use the Ipod touch/Iphone settings preset and it works on my HTC Magic (Android) and Sony Ericsson Satio (Symbian).

---

### Post by thatguruguy on 2010-02-15
> **lijcam said:**
> Ok so I think your trying to ask "How do I encode a video to play on multiple devices that require different codecs, resolutions and bit rates etc... " Answer, sorry but this is not possible.

However device manufactures are finialy starting to see the craziness of this situation and are starting to standardise. For example the ipod touch, Iphone, Android Phones, Symbian Phones, etc all support 480p mp4 with aac or mp3 sound tracks.

I use handbrake for video encoding and use the Ipod touch/Iphone settings preset and it works on my HTC Magic (Android) and Sony Ericsson Satio (Symbian).

That's why I suggested formatting for an iPod.

---

### Post by FakeOutdoorsman on 2010-02-15
> **thatguruguy said:**
> That's why I suggested formatting for an iPod.

Here's an example using FFmpeg with a file called *input.foo* as the input:
```
ffmpeg -i input.foo -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -vpre ipod320 -crf 26 -f ipod -threads 0 output.mp4
```

**Update:** You may need to enable some additional encoders to get this example to work:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg ](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by gsmanners on 2010-02-15
There's also the "Universal" (for 6G+) and "iPod" (for 5G) preset in HandBrake if you don't mind using that.

---

### Post by lavinog on 2010-02-15
+1 for handbrake

---

### Post by gigaferz on 2010-02-16
im sure handbrake can handle it, but still the one i got is cli based.

anyways, so ive been looking at fast video converter pro. It has the settings for good/best/excellent quality for many devices.

looks like what the iphone/ipod/psp/zune have in common is this:

video--    320:240 mpeg4
           800kbps
Audio--    96 kbps
           

Now in the hertz section psp /zune/ipod sshare the 44100hz setting when the iphone has different hz
the iphone is 32000hz
I guess once i can borrow the ipod ill find out for sure!

i cant wait to try it out!

---

