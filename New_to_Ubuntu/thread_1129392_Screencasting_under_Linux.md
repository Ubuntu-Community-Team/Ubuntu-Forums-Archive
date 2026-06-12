---
title: "Screencasting under Linux"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by sanubie on 2009-04-18
I want to make screencasts. Unfortunately Linux is huge. There are so many ways to do everything. I'm having trouble creating screencasts and retaining quality. 

I use recordMyDesktop and it works perfectly. Awesome quality. However, since I am having trouble editing videos in Linux, I have to boot into Windows and use Movie Maker to edit them. That creates a few problems. For one I have to convert ogv to avi. I found a command and used 

```
ffmpeg -i input.ogv output.avi 
```

It converted okay, a lot of the quality was lost, but not too much. Then I moved into Windows and Movie Make would only play sound from the video -- no video showed up. Must be a missing codec or something. So then I converted the avi to wmv and it worked. However, it lost a lot of quality after that. You couldn't see anything I was typing. 

I also tried the command 
```
mencoder -idx linux6.ogv -ovc lavc -oac mp3lame -o linux6.avi
```

About the same. Movie Maker still could not display video. Online sound. After converting to wmv quality did not hold up, especially once posted on Youtube. 

Does someone know any command tweaks to improve wmv conversion? I figure, instead of first converting to avi and then wmv, just use ffmpeg to convert straight to wmv. But how can I retain the best quality when converting to wmv? Or do you have a better idea all together? Movie Maker usually recognizes avi, but for some reason it doesn't play video of avi's converted in ffmpeg or mencoder. 

Any advice would be greatly appreciated.

---

### Post by xarquid on 2009-04-18
Can you just use AVI or must you use WMV? This will help with the quality issues. Every time you convert you are going to degrade the quality.

Can you be more specific on where you are screencasting to? I am just trying to figure out the specific requirements.

Have you tried [WinFF]("http://code.google.com/p/winff/")?

Also, FFMpeg with the proprietary w32 codecs should do the trick for what you are trying to accomplish. Do you have these codecs installed?

VLC can also handle conversions with plug-in packs.

There is also a [Multimedia Production]("http://ubuntuforums.org/forumdisplay.php?f=335") forum where they might have very specific answers, however keep the responses going in this thread. I'm pretty familiar with the technologies surrounding this. I'm just interesting in your requirements.

---

### Post by sanubie on 2009-04-18
I was posting them to Youtube. So the quality is going to be bad. Maybe I should find another place to host my videos.

Anyway, I tried converting it to wmv with ffmpeg. It converted the file, but Windows Media Player won't play it. It says its missing an audio codec. It won't even import into Movie Maker. 

I tried avi the first time. It converted fine and played in Media Player. But when I try to import into Movie Maker only sound from the video plays. So it doesn't appear to work no matter what I try. I had to first convert to avi and then convert that in Windows to wmv for it to even work with WMM. I must be missing a codec because it's a new computer. But I have no idea what codec I need.

---

### Post by stoogiebuncho on 2009-04-18
Just curious, but have you tried kdenlive for editing videos?  I find it easy to use and similar to the general feel of programs like Windows Movie Maker and iMovie.

I also use cinelerra, but that's a little less user-friendly.

Windows Movie Maker works well, but I find it to be one of the pickiest video editing programs when it comes to what types of files it will accept.

Sorry but I don't have any advice about converting for Windows MM.

---

### Post by xarquid on 2009-04-18
I really like cinelerra and kdenlive. Kino is not bad either.

You might want to check out this post:

[http://wiki.showmedo.com/index.php/Video_editing_Ubuntu](http://wiki.showmedo.com/index.php/Video_editing_Ubuntu)

I still recommend asking this question on the Multimedia Forums. Perhaps post a link, as well, to this post on there so they can see our responses thus far (at the end of your post). That might at least help them see what has been said thus far.

---

### Post by JK3mp on 2009-04-18
Yeah always a pain having to install codecs :-( .

---

### Post by xarquid on 2009-04-18
To install most codecs you can take a look at this guide:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

The most important thing is enabling the "restricted" repositories (if you haven't already) in System > Administration > Sources.

After this you can type this on the command-line:

```
sudo apt-get install ubuntu-restricted-extras
```

This should install most of them.

Another thing you should check out are the Medibuntu repositories. Many people find these very helpful:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

After adding the Medibuntu's repostory lines and running:

```
sudo apt-get update
```

Just run:

```
sudo apt-get install w32codecs
```

You should have most, if not all, of the codecs you need for quite a while.

Cheers!

---

### Post by benerivo on 2009-04-18
> **sanubie said:**
> ...Does someone know any command tweaks to improve wmv conversion? I figure, instead of first converting to avi and then wmv, just use ffmpeg to convert straight to wmv. But how can I retain the best quality when converting to wmv?...

You could try ```
ffmpeg -i input.ogv -sameq output.wmv
```which attempts to keep the same audio/video quality. Without an argument, it defaults to certain set parameters for the chosen output format.

---

### Post by andrew.46 on 2009-04-19
Hi sanubie,

> **sanubie said:**
> Does someone know any command tweaks to improve wmv conversion? I figure, instead of first converting to avi and then wmv, just use ffmpeg to convert straight to wmv. But how can I retain the best quality when converting to wmv? 

I see you have a fair bit of advice headed your way so I thought perhaps a practical example might help you out. I downloaded an ogg media file:

```
wget http://samples.mplayerhq.hu/V-codecs/Theora/Yeager_supersonic_flight_1947.ogg
```

which FFmpeg identifies as follows:

```

Duration: 00:03:04.16, start: 0.000000, bitrate: 306 kb/s
Stream #0.0: Video: theora, yuv420p, 384x288, 25 tbr, 25 tbn, 25 tbc
Stream #0.1: Audio: vorbis, 44100 Hz, stereo, s16, 79 kb/s

```

which I suspect may be very close to the ogv file you are generating from recordmyDesktop. Now if you want to turn this into a 'wmv' file you might be best to convert to wma sound and wmv video in an asf container, which I did to my sample with the following command:

```

 ffmpeg -i Yeager_supersonic_flight_1947.ogg -acodec wmav2 -vcodec wmv2 test.asf

```

Quality was actually pretty decent without specifying any bitrates so I have left it there. I run XP on a VM so I fired it up and imported the asf file into MovieMaker successfully as well as played the file in Media Player with both sound and video. I attach a screenshot of Chuck Yeager's asf in MovieMaker :-).

So it can be done with FFmpeg quite easily without any extra steps.

All the best,

Andrew

---

