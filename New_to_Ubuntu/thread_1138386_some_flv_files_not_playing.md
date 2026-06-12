---
title: "some flv files not playing"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by gkraju on 2009-04-26
hi i am having ubuntu 8.04 
in my system some .flv files(downloaded from youtube) not playing in both mplayer and in vlc 
mplayer shows 
**An error occurred Internal data stream error.**
in vlc no audio and no video 
help me please

---

### Post by andrew.46 on 2009-04-26
Hi gkraju,

It sounds like your files *may* be corrupt which is not completely unusual. What method did you use to download your files from youtube? If you can give a youtube address for one of these files as well this would make things a little easier to troubleshoot.

All the best,

Andrew

---

### Post by gkraju on 2009-04-30
> **andrew.46 said:**
> Hi gkraju,

It sounds like your files *may* be corrupt which is not completely unusual. What method did you use to download your files from youtube? If you can give a youtube address for one of these files as well this would make things a little easier to troubleshoot.

All the best,

Andrew

thanks for your reply 
i usually copy it from opera cache folder

---

### Post by andrew.46 on 2009-04-30
Hi gkraju,

> **gkraju said:**
> i usually copy it from opera cache folder

I have a sample flv file on my website, can you test it and see if you have an error? Download as follows:

```
wget http://andrews-corner.org/samples/linux.flv
```

It is only 450kbs and plays cleanly on my system with both vlc and MPlayer so it should be a decent test of your own system.

All the best,

Andrew

---

### Post by gkraju on 2009-04-30
> **andrew.46 said:**
> Hi gkraju,



I have a sample flv file on my website, can you test it and see if you have an error? Download as follows:

```
wget http://andrews-corner.org/samples/linux.flv
```

It is only 450kbs and plays cleanly on my system with both vlc and MPlayer so it should be a decent test of your own system.

All the best,

Andrew
it plays fine
but as i said already some files are playing some files are not playing

---

### Post by andrew.46 on 2009-04-30
Hi gkraju,

> **gkraju said:**
> it plays fine
but as i said already some files are playing some files are not playing

Which again leads me to suspect that the files that are not playing for you have been damaged. I note that across the forums several people have been reporting trouble recently with flvs retrieved from browser cache in this manner....

Perhaps you could retry downloading some of your files using an alternative method? One way that has been 100% troublefree for me has been:

Mini guide: Download high quality youtube vids suitable for your phone ...
[http://ubuntuforums.org/showthread.php?t=1037760](http://ubuntuforums.org/showthread.php?t=1037760)

And of course I wrote the guide as well :-). Give this a try and see if this brings an end to your trouble.

All the best,

Andrew

---

### Post by Niniel on 2009-04-30
I use Totem for both flv and mp4 videos; it even plays MP3s (after installing the gstreamer restricted codices).
It's easy to save You Tube videos with the Firefox extension [Video DownloadHelper]("https://addons.mozilla.org/en-US/firefox/addon/3006"). With that, you can usually pick if you want the flv or the mp4 (often called hdxx) version of a video (if available).
You said you were using Opera... so switch today! :)

---

### Post by meka4996 on 2009-05-23
try my solution...
[http://ubuntuforums.org/showthread.php?t=1103825](http://ubuntuforums.org/showthread.php?t=1103825)

---

