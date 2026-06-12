---
title: "WMV audio codecs?"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by HittingSmoke on 2009-02-05
I've got a few data DVD's worth of Red vs Blue all in WMV format. Most of them work great, but a good handful of them wont play audio. VLC just plays the video without any error. Totem gives me a codec error and cant find a suitable one on a search.

In Windows I would have just used Gspot to find out what I'm missing. VLC's codec info screen doesn't seem to be very detailed though...

Anyone know why some WMV's would play audio and some not, and how I can check the audio codec of a WMV file?

---

### Post by rraj.be on 2009-02-05
You need Win32 Codes to be installed. 
 
 
Install it from Synaptic . . .

---

### Post by jerome1232 on 2009-02-05
Nautilus does a good job at showing the codecs, just right click the multimedia file and select the Audio/Video tab.

But yeah w32codecs (or w64codecs if your running 64 bit) should get you going.

---

### Post by HittingSmoke on 2009-02-05
> **rraj.be said:**
> You need Win32 Codes to be installed. 
 
 
Install it from Synaptic . . .

w32codecs is installed... As I said in my OP, most of these WMV files work, If I didn't have w32codecs installed, they wouldn't. And they of course wouldn't play the video without w32codecs either, which they do...

And I have no audio/video tab in my Nautilus file properties.

---

### Post by mc4man on 2009-02-05
Mediainfo works pretty well
for 8.10 here otherwise build the source

[http://www.getdeb.net/search.php?search_distro_id=11&keywords=mediainfo](http://www.getdeb.net/search.php?search_distro_id=11&keywords=mediainfo)

It has 2 dependencies, download/install them first from right to left

(after loading a file or folder additional info can sometimes be seen by changing the view to html

---

### Post by HittingSmoke on 2009-02-05
> **mc4man said:**
> Mediainfo works pretty well
for 8.10 here otherwise build the source

[http://www.getdeb.net/search.php?search_distro_id=11&keywords=mediainfo](http://www.getdeb.net/search.php?search_distro_id=11&keywords=mediainfo)

It has 2 dependencies, download/install them first from right to left

(after loading a file or folder additional info can sometimes be seen by changing the view to html

Thank you! This is exactly what I needed.

All of the clips that wont play audio are listed as WMV3 under the audio codec. All the ones that play the audio fine are the WMV2 audio codec.

Also, when I try to force VLC to play the audio track from these videos I get this error,

```
No suitable decoder module:
VLC does not support the audio or video format "wmap". Unfortunately there is no way for you to fix this.
```

Is there some update to w32codecs that I need to find? I can't seem to find any info on this problem.

---

### Post by mc4man on 2009-02-05
Vlc has some limitations in regards to WMV, particularly the audio.

I don't have any WMV files, but for instance vlc can't play .wma lossless

You may want to try mplayer and or a xine based player (for xine players install libxine1-ffmpeg

for mplayer I'd start by using a current version, your best bet if you don't want to build is to install the smplayer ppa as a software source and then install mplayer and smplayer from there.

May be to no avail in terms of the troublesome files but at least you'd have a very capable and current (s)mplayer

[https://launchpad.net/~rvm/+archive/ppa](https://launchpad.net/~rvm/+archive/ppa)

Just add the source lines one at a time in System -> Admin.. -> Software Sources -> Third Party -> add, then click 'reload'.
Then (s)mplayer will be available in synaptic or from sudo apt-get install

edit: smplayer is actively supported by the developer in this forum, any issues just start thread with smplayer.... in title (use the Multimedia and Video forum

---

### Post by HittingSmoke on 2009-02-05
I tried Totem with no luck, I'' give mplayer a shot if my next idea doesn't work.

How about just converting my entire collection with ffmpeg? I dont know they syntax very well but would it just be possible to put in a command with wild cards and let it run all day converting my music and video files that are in wmv or wma into more universal formats?

---

