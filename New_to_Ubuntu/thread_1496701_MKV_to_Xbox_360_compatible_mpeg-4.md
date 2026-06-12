---
title: "MKV to Xbox 360 compatible mpeg-4"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by Stigmata13 on 2010-05-29
Okay, here's my problem. I have several video files, they are in mkv format. I've looked at hundreds of pages trying to figure out how I can convert them to a 360 compatable format, but I still can't manage to figure it out. I'm using Ubuntu 8.10, and I have been able to this thus far:
Extract the video to mp4. It worked decent, but was a little stuttery. I tried to use Avidemux but upon loading the mkv file I got a warning about it being h.264 and something about b-frames.
I converted the audio just fine.
Alternatively, what I want to be able to do:
Convert the video successfully without random stuttering, etc.
Convert the sound (shouldn't be a problem)
_Extract the subtitles_ = this is something I've been having a lot of trouble doing. All the guides recommend mkvextract but no matter how hard I try i can't seem to get it installed.

Also, the videos are 1024x576 and 1280x720. I would like to be able to downscale them to dvd quality, as I don't have an HDTV so the added quality wouldn't be of much use and would just cause more problems in the end.
Both videos are in the MKV container. As for what particular codecs, I'm not exactly sure.

---

### Post by ron999 on 2010-05-29
Hi
Use **MediaInfo** to analyze the mkv files to find out what's inside.
**mediainfo-gui** is in Ubuntu's repo.
You may not need to 'convert' them, maybe just change the container.
For example, put them in an mp4 container using **MP4Box**.

I use **MKVExtractGUI-2 v1.0.10.0** with WINE because I haven't found a gui version of mkvextract for Linux.

---

### Post by Stigmata13 on 2010-05-29
Thanks for the advice.
Running sudo apt-get install mediainfo-gui returns as E: Couldn't find Package mediainfo-gui
I have also tried both add/remove and synaptic package manager
I'm running 8.10 which has been upgraded from 8.04 LTS btw
I suppose I'll try that program under windows. I would have preffered to do it solely in linux but at this point I don't mind trying anything, lol

---

### Post by ron999 on 2010-05-29
OK, get a deb for **mediainfo** from the website here:-[http://mediainfo.sourceforge.net/en/Download/Ubuntu#9.10.i386]("http://mediainfo.sourceforge.net/en/Download/Ubuntu#9.10.i386")

You can use mkvextract with Linux, it's part of the package **mkvtoolnix**, but there's no gui.

---

### Post by PocketDog on 2010-05-29
I've used Devede to convert MKV to AVI, then put it on memory stick and watched it from that. As long as your 360 is hooked up to the net to download the necessary codecs (which it'll do automatically) it's as easy as that. All GUI too.

---

### Post by Stigmata13 on 2010-05-29
> **PocketDog said:**
> I've used Devede to convert MKV to AVI, then put it on memory stick and watched it from that. As long as your 360 is hooked up to the net to download the necessary codecs (which it'll do automatically) it's as easy as that. All GUI too.
I tried DeVeDe but it wouldn't work, probably because my version is the version that shipped with 8.04
Anyway, I tried to install mediainfo-gui from that link you gave me but the deb needed a dependancy that likewise I couldn't find, I'm starting to think my software sources may be a little screwed.
But i did manage to install the latest versions of mkvtoolnix and mkvextractgui under wine, and it successfully extracted 6 files.
1. a .h264 video file
2. a .aac audio file
3. a .*** subtitle file
4. a .txt chapter file
5. a .idx (index?) file
6. a .otf font file

Edit: Managed to get mediainfo for windows and got the following output:
Video: English, 1280*720 (16:9), at 23.976 fps, AVC (Container profile=Unknown@4.0)(High@L4.0) (CABAC/8 Ref Frames)
Audio: Japanese, 48.0 KHz, 2 channels, AAC (Version 4)(LC)
Text Stream=English, ***

---

### Post by ron999 on 2010-05-29
OK, I got this information from the web:-
> Xbox 360 video format - H.264

Xbox 360 supports the following for Xbox 360 video format H.264:

File Extensions: .mp4, .m4v, mp4v, .mov
Containers: MPEG-4, QuickTime
Video Profiles: Baseline, main, and high (up to Level 4.1) profiles.
Video Bitrate: 10 Mbps with resolutions of 1920 x 1080 at 30fps.
Audio Profiles: 2 channel AAC low complexity (LC)


So your h264 and aac files will probably be OK without converting.

You need to wrap them in an mp4 container. Just those two files, none of the other stuff.
To do this you use a command-line program called **MP4Box**.
Your command will be something like this:-
```
MP4Box -add whatever.h264 -add whatever.aac output.m4v
```

Good luck.:guitar:

Edit
I've just read your edit.
Are you going to listen to it in Japanese?

---

### Post by Stigmata13 on 2010-05-29
> **ron999 said:**
> OK, I got this information from the web:-


So your h264 and aac files will probably be OK without converting.

You need to wrap them in an mp4 container. Just those two files, none of the other stuff.
To do this you use a command-line program called **MP4Box**.
Your command will be something like this:-
```
MP4Box -add whatever.h264 -add whatever.aac output.m4v
```Good luck.:guitar:

Edit
I've just read your edit.
Are you going to listen to it in Japanese?
;)  Of course.
It's an anime, japanese only with subtitles ;)
I'll give that a shot though. is there any way afterwards I could put the subtitles in, or perhaps would I be able to toss them in at the same time as the other files?

---

### Post by ron999 on 2010-05-29
> **Stigmata13 said:**
> ;)  Of course.
It's an anime, japanese only with subtitles ;)

Ok
I'm pretty confident that you can make your mp4 file, but I don't know what the heck to do with the subtitles.

---

### Post by Stigmata13 on 2010-05-29
> **ron999 said:**
> Ok
I'm pretty confident that you can make your mp4 file, but I don't know what the heck to do with the subtitles.
Alright, thanks for the help :)
I'll mess around with Avidemux afterwards and see what I can do, lol.

Edit: Hmm wow now that's strange....
After running just that line, it looks like it put the subtitles in there for me because their still there, hah.
Certainly makes things much easier ^^
Edit again, lol: Grrr... or not... it played with the subtitles but when I moved the m4v out of the same directory as the subtitle files, the subs in the video disappeared O_o

---

### Post by ron999 on 2010-05-29
Hi
Maybe you can just toss the subtitles in with the mix.
I have no experience with this though.
Perhaps do a dummy run with just the video and audio tracks to _prove your method_.
Then experiment with subtitles later or ask for advice on the forum.

---

