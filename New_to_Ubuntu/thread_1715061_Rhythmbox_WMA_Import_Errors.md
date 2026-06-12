---
title: "Rhythmbox WMA Import Errors"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by Mr Stoozer on 2011-03-26
Hello to all,
Total newbie here trying to get Rhythmbox to import my WMA audio files.
The error states "Additional GStreamer plugins are required to play this file: Windows Media Audio decoder"
I have w32codecs installed, restricted extras, medibuntu non-free-codecs and have had a look through Synaptic to find any relevant packages to no avail.

Here's the ouput of ```
gst-inspect | grep wma
```

[B]ffmpeg:  ffenc_wmav1: FFmpeg Windows Media Audio 1 encoder
ffmpeg:  ffenc_wmav2: FFmpeg Windows Media Audio 2 encoder
ffmpeg:  ffdec_wmapro: FFmpeg Windows Media Audio 9 Professional decoder
ffmpeg:  ffdec_wmav1: FFmpeg Windows Media Audio 1 decoder
ffmpeg:  ffdec_wmav2: FFmpeg Windows Media Audio 2 decoder
ffmpeg:  ffdec_wmavoice: FFmpeg Windows Media Audio Voice decoder
typefindfunctions: video/x-ms-asf: wmv, wma, wm, asf
[/B]

Anyone have any ideas as to which plugins i need to install?
Here's a screeny of Synaptic filtered with GStreamer if it's any help.

[ATTACH]187164[/ATTACH]
----------------
Ubuntu 10.10 x86

---

### Post by acreech on 2011-03-26
Have you tried to do this?


```
sudo apt-get install ubuntu-restricted-extras
```

I set up my multimedia following this guide. It is old, but still seems to work. 

```
http://ubuntuforums.org/showthread.php?t=766683
```

You may consider converting all the files to mp3 so you don't have to continually deal with the windows restrictions. 


Good luck.

---

### Post by Mr Stoozer on 2011-03-26
> **acreech said:**
> Have you tried to do this?
 
 
```
sudo apt-get install ubuntu-restricted-extras
```
 
I set up my multimedia following this guide. It is old, but still seems to work. 
 
```
http://ubuntuforums.org/showthread.php?t=766683
```
 
You may consider converting all the files to mp3 so you don't have to continually deal with the windows restrictions. 
 
 
Good luck.
 
Hi, yes i have the resticted extras installed.  I'd also like to pass on converting if possible.  I'll check out the link you posted. Thanks for your input.

---

