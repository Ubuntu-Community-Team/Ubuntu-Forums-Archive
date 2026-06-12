---
title: "Saving You Tube videos"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by richg on 2009-01-23
I have been trying to figure out how to save You Tube videos and searched the forums coming up with what looks like a solution but I still have questions. I use Ubuntu 8.04 with all updates and Adobe Flash Player 9.
-----------------------------------------------------------------------------------------
 Re: Saving youtube videos.
Quote:
Originally Posted by ellalan View Post
Hi
Could someone tell me how can I save youtube videos in my hard disc please.
My OS is Hardy Heron 8.04. TIA.
I've got a better solution that any in this thread.

Provided you're using Firefox and have the Greasemonkey add-on installed (which you should) just install this script into Greasemonkey. [http://userscripts.org/scripts/show/13333](http://userscripts.org/scripts/show/13333)

It not only allows you to download, but lets you select different formats, resize video, choose higher quality if its available and really cleans up the video viewing page to make it more enjoyable.

All of this, right from your Youtube page, no encumbering download managers to install. Every Youtube user should be running this script.
__________________
Firefox + Noscript, the Trojan condom of browsing.
Last edited by HittingSmoke; September 28th, 2008 at 11:26 AM..
HittingSmoke is offline   	Reply With Quote
-----------------------------------------------------------------------------------------

I installed Grease Monkey which is easy but the script thing is not straight forward. Is there an easier way to do the script thing?
Please no links. Links usually lead to other links with no clear solution sometimes. Thanks.

Rich

---

### Post by billgoldberg on 2009-01-23
Here you go:

[http://www.getdeb.net/app/PyTube](http://www.getdeb.net/app/PyTube)

Besides downloading the youtube videos, you can just rip the sound and save them as .mp3 (handy for downloading music). Or save the video as .avi and other stuff.

And it has some other features as well (adding sound to a video, trimming a video, ...).

-- 
[I]
Note that sometimes you have to try two or more times before it will actually start downloading. Small glitch.[/I]

---

### Post by bailbath on 2009-01-23
I just use Downloadhelper add on in firefox which is just easy I use different programs to change or convert videos.
[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

---

### Post by russu52 on 2009-01-23
i have added video download helper to firefox, which enables to save any flv or video file on you tube etc. then i watch them on vlc media player

---

### Post by khelben1979 on 2009-01-23
Yes, there's a better way in my opinion.
There's a firefox plugin which is called Media Converter. [Look at this webpage]("http://www.mediaconverter.org/").

---

### Post by richg on 2009-01-23
Hello All

I used Download Helper and it works just fine. I entered Solved in the Subject line as I again cannot find the Solved Icon.

I did Uninstall Greasy Monkey.

Thanks to all.:D

Rich:D

---

### Post by iKonaK on 2009-01-23
Why not just go to /tmp and copy the flash after is loaded ?

---

### Post by nothingspecial on 2009-01-23
> **iKonaK said:**
> Why not just go to /tmp and copy the flash after is loaded ?

That`s what I do. Watch the video then as soon as the little status bar thingy at the bottom of the video is full it will be in /tmp untill you navigate away from the page. Just drag n drop.

---

### Post by richg on 2009-01-23
> **iKonaK said:**
> Why not just go to /tmp and copy the flash after is loaded ?

Because I was not aware of that. I am now. If that option was mentioned in the messages, I must have missed it. Where is Obvious Man when you need him?
That option is definitely the easiest, at least for me. 

Though I have been using Linux for five years, I am still only a user as I do not like messing with the OS. Retired on fixed income, I need free, trouble free, relatively secure software.

Rich

---

### Post by lukjad on 2009-01-23
The best way I know for saving youtube videos is youtube-dl.

Go to the terminal (*Application->Accessories->Terminal*) and type the link to the video. For example:
```
youtube-dl http://www.youtube.com/watch?v=PbUtL_0vAJk
```

This will download Martin Luther King's "I have a dream" speech with the name ***PbUtL_0vAJk*** and put it in your home folder. From that point, you can change the name to something more readable. Hope this helps! :D

---

### Post by andrew.46 on 2009-01-23
Hi lukjad007,

> **lukjad007 said:**
> The best way I know for saving youtube videos is youtube-dl.

You might be interested in a few extra options introduced by the newer version of youtube-dl:

[http://ubuntuforums.org/showthread.php?t=1037760](http://ubuntuforums.org/showthread.php?t=1037760)

This does little for older clips such as the one you link to but makes a spectacular difference with others.

Andrew

---

### Post by Garyhans on 2009-01-23
Just go to home folder .. press ctrl H.. then.. .mozilla.. the cache. then.. drag and drop.. the flash file to your liking.. simple really.

---

### Post by spcwingo on 2009-01-23
I can't believe that nobody has mentioned the easiest way of all.  You can download the videos natively in Firefox.  In the Firefox toolbar press tools>page info.  That will pop-up another window.  Press Media and in that window just select the address that ends with .swf.  Now press Save As and select where to save to.

---

### Post by Garyhans on 2009-01-23
But if you watch the Video... I fail to see the point.. it's in your cache.. it's quite simple to move a file..  and requires no addons.. which we all know Firefox 3.0 isn't a pleasant one for this.

---

### Post by fakeollie on 2009-02-18
Lately, simply moving the flv files from /tmp isnt working anymore for YouTube videos. 

Maybe they've changed anything. Anyone experiencing this? Know any workarounds?

---

### Post by desm on 2009-02-18
Sometimes If the video is still open in the broswer then the video is in firefox's temp, not ubuntu's. Maybe you should try that?

---

### Post by tombott on 2009-02-18
> **fakeollie said:**
> Lately, simply moving the flv files from /tmp isnt working anymore for YouTube videos. 

Maybe they've changed anything. Anyone experiencing this? Know any workarounds?

Working fine here. Running Ubuntu 8.10, FF 3.0.6

---

### Post by aktiwers on 2009-02-18
Or write pwn infront of the url.

Like this:

Before:
```
http://www.youtube.com/watch?v=PbUtL_0vAJk
```

After:
```
http://www.[COLOR=Red]pwn[/COLOR]youtube.com/watch?v=PbUtL_0vAJk
```

---

### Post by dannyboy79 on 2009-02-18
> **lukjad007 said:**
> The best way I know for saving youtube videos is youtube-dl.

Go to the terminal (*Application->Accessories->Terminal*) and type the link to the video. For example:
```
youtube-dl http://www.youtube.com/watch?v=PbUtL_0vAJk
```

This will download Martin Luther King's "I have a dream" speech with the name ***PbUtL_0vAJk*** and put it in your home folder. From that point, you can change the name to something more readable. Hope this helps! :D
this is how I do it.

---

### Post by fakeollie on 2009-03-05
> **tombott said:**
> Working fine here. Running Ubuntu 8.10, FF 3.0.6

Yeah, only... it's not. 

Refer to: [http://ubuntuforums.org/showthread.php?t=1061606](http://ubuntuforums.org/showthread.php?t=1061606)

And several other info around the web.

---

### Post by andrew.46 on 2009-03-05
Hi fakeollie,

> **fakeollie said:**
> Yeah, only... it's not. 

Refer to: [http://ubuntuforums.org/showthread.php?t=1061606](http://ubuntuforums.org/showthread.php?t=1061606)

And several other info around the web.

Do you have a link for one of the difficult ones?

Andrew

---

### Post by fakeollie on 2009-03-05
> **andrew.46 said:**
> Hi fakeollie,
Do you have a link for one of the difficult ones?
Andrew

Sure thing. I just loaded these two:

[http://www.youtube.com/watch?v=HRfRLPHk44w](http://www.youtube.com/watch?v=HRfRLPHk44w)

and

[http://www.youtube.com/watch?v=XnMDrv8Mx3E](http://www.youtube.com/watch?v=XnMDrv8Mx3E)

They are both stored in /tmp (Nautilus even generates their thumbnails correctly). But you can't open them. Neither VLC (0.9.4, intrepid) nor Totem understand YouTube's new messed up FLV format. Handbrake loads the FLVs, but once you start to convert them, it crashes.

---

### Post by xpod on 2009-03-05
First one works fine from /tmp here although it is version 0.9.8a of vlc in 9.04 i`m using.

---

### Post by andrew.46 on 2009-03-05
Hi,

And the second one works fine with vlc as well. I will admit I downloaded it with youtube-dl :-).

Andrew

---

### Post by Kat of Zion on 2009-03-06
I too am having a problem.with YouTube vids.  Im using VLC and Mplayer but none will play the flv for me.  Converting it to mp3 like I usally did through mplayer was a bust too.  Conversion turned it into an mp3 that sounded like mush.

Did YT recently change the overall codec?

Error: 
[00000420] main decoder error: no suitable decoder module for fourcc `undf'.
VLC probably does not support this sound or video format.
[00000459] main decoder error: no suitable decoder module for fourcc `undf'.
VLC probably does not support this sound or video format.

---

### Post by andrew.46 on 2009-03-06
Hi Kat,

> **Kat of Zion said:**
> I too am having a problem.with YouTube vids.  Im using VLC and Mplayer but none will play the flv for me.  Converting it to mp3 like I usally did through mplayer was a bust too.  Conversion turned it into an mp3 that sounded like mush.

Did YT recently change the overall codec?

There has been an ongoing change to h264 video encoding with aac sound. Also there are increasing numbers of these high quality clips coming in mp4 containers.

Andrew

---

### Post by tombott on 2009-03-06
> **fakeollie said:**
> Yeah, only... it's not. 

Refer to: [http://ubuntuforums.org/showthread.php?t=1061606](http://ubuntuforums.org/showthread.php?t=1061606)

And several other info around the web.

Yeah always helps when you provide a little more information.

The method does still work, only not with YouTube's newest video's which I was unaware of until now.

---

### Post by andrew.46 on 2009-03-06
Hi tombott,

> **tombott said:**
> The method does still work, only not with YouTube's newest video's which I was unaware of until now.

This might be a good time for me to pimp my guide which demonstrates how to download these high quality youtube videos:

Mini guide: Download high quality youtube vids suitable for your phone ...
[http://ubuntuforums.org/showthread.php?t=1037760](http://ubuntuforums.org/showthread.php?t=1037760)

It still puzzles me that this guide does not get more traffic although I suspect it could be the commandline thing :-).

All the best,

Andrew

---

### Post by dannyboy79 on 2009-03-06
more newbies should become familar with using the command line and they shouldn't be scared of it. I know once I was became more familar with it, I was able to start doing more stuff due to there being guides out there that use the cli so much. again, great  script and guide for those high quality videos.

---

### Post by Kat of Zion on 2009-03-06
> **andrew.46 said:**
> Hi Kat,



There has been an ongoing change to h264 video encoding with aac sound. Also there are increasing numbers of these high quality clips coming in mp4 containers.

Andrew

Yeah.  YouTube has been doing alot of changes lately.  So do I just need to take the files I ripped out of the tmp folder and change them to .mp4 or something.  What can I do to get those vids to play on my local machine and/or create a file (mp3) that plays the audio track?

---

### Post by andrew.46 on 2009-03-06
Hi Kat,

> **Kat of Zion said:**
> Yeah.  YouTube has been doing alot of changes lately.  So do I just need to take the files I ripped out of the tmp folder and change them to .mp4 or something.  What can I do to get those vids to play on my local machine and/or create a file (mp3) that plays the audio track?

No, you need to download the higher quality videos themselves rather than convert the lower quality ones. The guide I wrote deals with this using youtube-dl but I am sure there would be other, perhaps gui, ways of doing this. Then if you need only the sound you would be better to simply copy the aac sound rather than convert to another format.

All the best,

Andrew

---

### Post by Kat of Zion on 2009-03-07
> **andrew.46 said:**
> Hi Kat,



No, you need to download the higher quality videos themselves rather than convert the lower quality ones. The guide I wrote deals with this using youtube-dl but I am sure there would be other, perhaps gui, ways of doing this. Then if you need only the sound you would be better to simply copy the aac sound rather than convert to another format.

All the best,

Andrew

Oh, I did probably download the high quality video which is why I cant play it.  Maybe I didnt phrase my question in a communicative manner.

What Im asking is how to rip the sound from it.  I usually do that with things I find on YouTube that aer musical.  Normally I used Mencoder to do "dumping" of the video part and just taking the audio out of the FLVs and making it to a mp3.  However since some vids are being done with this h264 encoding that is where I am trying to find the answer.  How would I use mencoder to do this with the appropriate codec?  

Kat

---

### Post by andrew.46 on 2009-03-07
Hi Kat,

> **Kat of Zion said:**
> What Im asking is how to rip the sound from it.  I usually do that with things I find on YouTube that aer musical.  Normally I used Mencoder to do "dumping" of the video part and just taking the audio out of the FLVs and making it to a mp3.  However since some vids are being done with this h264 encoding that is where I am trying to find the answer.  How would I use mencoder to do this with the appropriate codec? 

Well to answer your question a little to the side: I would use FFmpeg myself. For example here are the specs for one such file:

```
Duration: 00:01:11.30, start: 0.000000, bitrate: 622 kb/s
Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
Stream #0.1(und): Video: h264, yuv420p, 480x360, 29.97 tbr, 29.97 tbn, 29.97 tbc
```

And to convert to sound only to mp3:

```

andrew@skamandros~/Desktop$ ffmpeg -i sample.mp4 -vn -alang eng -acodec libmp3lame -ab 128k output.mp3
FFmpeg version SVN-r17653, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug --enable-shared --disable-static --enable-postproc --enable-avfilter --enable-pthreads --enable-libtheora --enable-libvorbis --enable-swscale --enable-x11grab --enable-libmp3lame --enable-libx264 --enable-libschroedinger --enable-libfaac --enable-libfaad --enable-libamr-wb --enable-libamr-nb --enable-libgsm --enable-nonfree --enable-gpl
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.30. 1 / 52.30. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Feb 28 2009 18:07:36, gcc: 4.2.4
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'sample.mp4':
  Duration: 00:01:11.30, start: 0.000000, bitrate: 622 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x360, 29.97 tbr, 29.97 tbn, 29.97 tbc
Output #0, mp3, to 'output.mp3':
    [COLOR="Red"]**Stream #0.0(eng): Audio: libmp3lame, 44100 Hz, stereo, s16, 128 kb/s**[/COLOR]
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    1111kB time=71.11 bitrate= 128.0kbits/s    
video:0kB audio:1111kB global headers:0kB muxing overhead 0.002813%

```

And this leaves an mp3 file as follows:

```
Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 128 kb/s
```

If you are after a decent copy of FFmpeg the best place on these forums is [the FakeOutdoorsman's guide]("http://ubuntuforums.org/showthread.php?t=786095").

All the best,

Andrew

---

### Post by Kat of Zion on 2009-03-07
> **andrew.46 said:**
> Hi Kat,



Well to answer your question a little to the side: I would use FFmpeg myself. For example here are the specs for one such file:

```
Duration: 00:01:11.30, start: 0.000000, bitrate: 622 kb/s
Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
Stream #0.1(und): Video: h264, yuv420p, 480x360, 29.97 tbr, 29.97 tbn, 29.97 tbc
```

And to convert to sound only to mp3:

```

andrew@skamandros~/Desktop$ ffmpeg -i sample.mp4 -vn -alang eng -acodec libmp3lame -ab 128k output.mp3
FFmpeg version SVN-r17653, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug --enable-shared --disable-static --enable-postproc --enable-avfilter --enable-pthreads --enable-libtheora --enable-libvorbis --enable-swscale --enable-x11grab --enable-libmp3lame --enable-libx264 --enable-libschroedinger --enable-libfaac --enable-libfaad --enable-libamr-wb --enable-libamr-nb --enable-libgsm --enable-nonfree --enable-gpl
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.30. 1 / 52.30. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Feb 28 2009 18:07:36, gcc: 4.2.4
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'sample.mp4':
  Duration: 00:01:11.30, start: 0.000000, bitrate: 622 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x360, 29.97 tbr, 29.97 tbn, 29.97 tbc
Output #0, mp3, to 'output.mp3':
    [COLOR="Red"]**Stream #0.0(eng): Audio: libmp3lame, 44100 Hz, stereo, s16, 128 kb/s**[/COLOR]
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    1111kB time=71.11 bitrate= 128.0kbits/s    
video:0kB audio:1111kB global headers:0kB muxing overhead 0.002813%

```

And this leaves an mp3 file as follows:

```
Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 128 kb/s
```

If you are after a decent copy of FFmpeg the best place on these forums is [the FakeOutdoorsman's guide]("http://ubuntuforums.org/showthread.php?t=786095").

All the best,

Andrew

I already had ffmpeg installed out of the repositories.  Any chance that there might be an extra part to it that Im missing? I take it that since you used a .mp4 as an example, than I need to change those youtube files from .flv to .mp4 instead, right?

---

### Post by andrew.46 on 2009-03-07
Hi Kat,

> **Kat of Zion said:**
> I already had ffmpeg installed out of the repositories.  Any chance that there might be an extra part to it that Im missing? I take it that since you used a .mp4 as an example, than I need to change those youtube files from .flv to .mp4 instead, right?

I think your original need was to strip the sound from a youtube .flv file though, and to have the resulting file in mp3 format? I have perhaps clouded the issue by mentioning the new, high quality files available on youtube :-).

Can you examine one of these files that have given you trouble in the following way and post the full commandline and terminal results:

```
ffmpeg -i myfile.flv
```

Which distro are you using BTW? There are limitations imposed on Ubuntu users by the stock FFmpeg in all variants of Ubuntu which the FakeOutdoorsman has an encyclopaedic knowledge of :-).

Andrew

---

### Post by Kat of Zion on 2009-03-07
> **andrew.46 said:**
> Hi Kat,

Can you examine one of these files that have given you trouble in the following way and post the full commandline and terminal results:


```
[flv @ 0xb7f31110]Unsupported video codec (7)
```
(note that this repeated for 50+ lines)

then...

```
Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 20.00 (20/1)
Input #0, flv, from 'judgejuleswithoutlove.flv':
  Duration: 00:06:49.5, start: 0.000000, bitrate: N/A
  Stream #0.0: Video: 0x0007, 20.00 fps(r)
  Stream #0.1: Audio: 0x000a, 44100 Hz, stereo
Must supply at least one output file
Press any key to continue...   
```

Kat

---

### Post by RedRat on 2009-03-07
If you want to use PyTube download the latest version from
[http://www.marcosrodriguez.me/pytube/](http://www.marcosrodriguez.me/pytube/)

It has some bugs fixed.

Flash downloader works for me in Firefox. You might want to try PyTube but it takes a bit of playing with to get it to work. The interface is not that intuitive so be patient, it took me several tries to get a video. It does have a nice feature in that it can convert the flv format to other more common ones.

---

### Post by Kat of Zion on 2009-03-07
> **RedRat said:**
> If you want to use PyTube download the latest version from
[http://www.marcosrodriguez.me/pytube/](http://www.marcosrodriguez.me/pytube/)

It has some bugs fixed.

Thanks!

Youtube-dl probably would stil work too.  I just was curious if mencoder could still of been the way we did it.  For flvs ripped off of places like imeem, we do find with mencoder so it would be nice if it could still work with Youtube. :)

---

### Post by andrew.46 on 2009-03-07
Hi Kat,

> **Kat of Zion said:**
> 
```

  Stream #0.0: Video: 0x0007, 20.00 fps(r)
  Stream #0.1: Audio: 0x000a, 44100 Hz, stereo

```

There seems a bit of oddness about the Video and Audio ids which give weird codec identification when I search them out. Can you give a youtube address for this file? The vids I saw with this title were flv video and mp3 sound. BTW are you using Feisty?

Sorry this is dragging out for so long :-).

Andrew

---

### Post by Kat of Zion on 2009-03-07
> **andrew.46 said:**
> Hi Kat,

Sorry this is dragging out for so long :-).

Andrew

I am using Hardy Heron.

[http://www.youtube.com/watch?v=ykP2KwWDQMw](http://www.youtube.com/watch?v=ykP2KwWDQMw)

Dont worry about it dragging out. True I had to go to my modeling shoot with no new music but thats the least of my worries. :)

---

### Post by andrew.46 on 2009-03-07
Hi Kat,

> **Kat of Zion said:**
> I am using Hardy Heron.

[http://www.youtube.com/watch?v=ykP2KwWDQMw](http://www.youtube.com/watch?v=ykP2KwWDQMw)

Dont worry about it dragging out. True I had to go to my modeling shoot with no new music but thats the least of my worries. :)

I downloaded this one with youtube-dl and it reports:

```
Input #0, flv, from 'ykP2KwWDQMw.flv':
Duration: 00:06:49.50, start: 0.000000, bitrate: 94 kb/s
Stream #0.0: Video: flv, yuv420p, 208x160, 30 kb/s, 20 tbr, 1k tbn, 1k tbc
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s
```

which is pretty low quality all round but easy enough to extract sound from:

```
ffmpeg -i ykP2KwWDQMw.flv -acodec copy output.mp3
```

If your copy of FFmpeg reports this differently you might be best to enable the Medibuntu repository and try their copy instead. Details of how to do this can be seen here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Hopefully this puts you on the right path?

Andrew

---

### Post by Piraja on 2009-03-07
I browsed through this thread very quickly and searched it for "clive" &#8212; was surprised it wasn't mentioned. I use Clive, a command-line downloader which is extremely simple:

```
clive http://www.youtube.com/watch?v=PbUtL_0vAJk
```

This will download Martin Luther King's "I Have a Dream" speech, mentioned above. It's not just that I'm too lazy to think of an example myself and just copied it, but I did not realize such a video was available and decided to download it myself; estimated 11:20 to go, atm.

Clive sets the file name and type automatically, in this case it will be MartinLutherKingIHaveADream.mp4.

---

### Post by Piraja on 2009-03-07
> **lukjad007 said:**
> The best way I know for saving youtube videos is youtube-dl.

Go to the terminal (*Application->Accessories->Terminal*) and type the link to the video. For example:
```
youtube-dl http://www.youtube.com/watch?v=PbUtL_0vAJk
```

This will download Martin Luther King's "I have a dream" speech with the name ***PbUtL_0vAJk*** and put it in your home folder. From that point, you can change the name to something more readable. Hope this helps! :D
Well, Clive even saves you from the great deal of trouble in renaming the file... Now all I have to do is
```
mplayer Martin*.mp4
```
and I can view the downloaded video right away...

---

### Post by Kat of Zion on 2009-03-07
> **andrew.46 said:**
> Hi Kat,

```
ffmpeg -i ykP2KwWDQMw.flv -acodec copy output.mp3
```



```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
thespacebrothersshineblakejarrell.flv: I/O error occured
Usually that means that input file is truncated and/or corru
```

Yeah. Honestly I would rather have one way that works for both my YouTube stuff (which is where the problem is due to them adding some codecs) or Imeem (which is just fine).  If Mencoder cant do it, than I will have to try ffmpeg from another repository.

---

### Post by andrew.46 on 2009-03-07
Hi Kat,

> **Kat of Zion said:**
> If Mencoder cant do it, than I will have to try ffmpeg from another repository.

Can I ask what your MEncoder syntax was? I am a little curious as MEncoder does not normally extract audio *directly* from a video without some commandline gymnastics. BTW I have posted the mp3 generated by FFmpeg on my site and you can download as follows:

```
wget http://www.andrews-corner.org/output.mp3
```

if you want to have a look and this file is important to you?

Andrew

---

### Post by Kat of Zion on 2009-03-07
> **andrew.46 said:**
> Hi Kat,



Can I ask what your MEncoder syntax was? I am a little curious as MEncoder does not normally extract audio *directly* from a video without some commandline gymnastics. BTW I have posted the mp3 generated by FFmpeg on my site and you can download as follows:

```
wget http://www.andrews-corner.org/output.mp3
```

if you want to have a look and this file is important to you?

Andrew

What I normally used was: 
mplayer -dumpaudio file.flv -dumpfile file.mp3

I did try using ffmpeg from mediaubuntu (apparently I already had it installed) and that didnt do me any good.  I got about 3 more files to deal with that are like this so finding a solution would be best rather than relying on someone to do it for me.

Kat

---

### Post by metallicamike on 2009-03-07
just use kiss youtube like do:
[http://www.youtube.com/watch?v=PbUtL_0vAJk](http://www.youtube.com/watch?v=PbUtL_0vAJk) then change it to:
[http://www.kissyoutube.com/watch?v=PbUtL_0vAJk](http://www.kissyoutube.com/watch?v=PbUtL_0vAJk) and it will  bring you to a page to prompt if you have java and hit the download button.

---

### Post by arsmith on 2009-03-07
Have you looked into the Totem plugin for youtube?

[http://tombuntu.com/index.php/2008/04/04/play-youtube-videos-from-the-totem-movie-player/](http://tombuntu.com/index.php/2008/04/04/play-youtube-videos-from-the-totem-movie-player/)

---

### Post by andrew.46 on 2009-03-08
Hi Kat,

> **Kat of Zion said:**
>  I got about 3 more files to deal with that are like this so finding a solution would be best rather than relying on someone to do it for me.

Fair enough. Sounds like the flvs you have on your computer might be a little suspect. I will butt out now as you have advice flying in from all corners but with the Medibuntu FFmpeg you should be able to easily do the following:

```
$ sudo apt-get install youtube-dl
$ cd $HOME/Desktop
$ youtube-dl 'http://www.youtube.com/watch?v=ykP2KwWDQMw'
$ ffmpeg -i ykP2KwWDQMw.flv -vn -acodec copy mysong.mp3
```

All the best,

Andrew

---

### Post by Kat of Zion on 2009-03-08
> **andrew.46 said:**
> Hi Kat,



Fair enough. Sounds like the flvs you have on your computer might be a little suspect. 

Suspect how?  Like, I need to grab them all over again?

---

### Post by ashwinhgtx on 2009-03-08
There is a much easier way to do this.
Just type pwn in front of the youtube url.

eg. if the url of your video is 
[http://www.youtube.com/watch?v=pv5zWaTEVkI&feature=channel_page](http://www.youtube.com/watch?v=pv5zWaTEVkI&feature=channel_page)

change it to
[http://www.pwnyoutube.com/watch?v=pv5zWaTEVkI&feature=channel_page](http://www.pwnyoutube.com/watch?v=pv5zWaTEVkI&feature=channel_page)

and hit enter.

THIS IS NOT A JOKE. Try it. Seriously.

You will get an option to download the video in standard quality(FLV) or high quality(MP4).

Cheers
GTX

---

### Post by aktiwers on 2009-03-08
> **ashwinhgtx said:**
> There is a much easier way to do this.
Just type pwn in front of the youtube url.

eg. if the url of your video is 
[http://www.youtube.com/watch?v=pv5zWaTEVkI&feature=channel_page](http://www.youtube.com/watch?v=pv5zWaTEVkI&feature=channel_page)

change it to
[http://www.pwnyoutube.com/watch?v=pv5zWaTEVkI&feature=channel_page](http://www.pwnyoutube.com/watch?v=pv5zWaTEVkI&feature=channel_page)

and hit enter.

THIS IS NOT A JOKE. Try it. Seriously.

You will get an option to download the video in standard quality(FLV) or high quality(MP4).

Cheers
GTX

Like i wrote in post #18 ;)

---

### Post by Kat of Zion on 2009-03-08
YOutube-dl will have to do for now.  I sure liked hte one stop shopping since the mencoder method did it no matter if I got it from Imeem, Google Video, Youtube, etc.  

So what does youtube-dl have that mencoder does not?  The script does not suggest it uses ffmpeg (not that it would be logical since the ffmpeg on my machine is the mediabuntu version which didnt work for any previous attempts to get mencoder to continue to do this for me).

Kat

---

### Post by ashwinhgtx on 2009-03-09
> **aktiwers said:**
> Like i wrote in post #18 ;)

Sorry, I missed that...:(

---

### Post by andrew.46 on 2009-03-09
Hi Kat,

> **Kat of Zion said:**
>  So what does youtube-dl have that mencoder does not?  The script does not suggest it uses ffmpeg (not that it would be logical since the ffmpeg on my machine is the mediabuntu version which didnt work for any previous attempts to get mencoder to continue to do this for me).

youtube-dl simply downloads the you-tube video, it does not do any transcoding. You can use whatever software you want to to extract audio or transcode it. IMHO FFmpeg is the best tool for this, but if you can get MEncoder to work go for it :-).

Andrew

---

### Post by Kat of Zion on 2009-03-09
> **andrew.46 said:**
> Hi Kat,



youtube-dl simply downloads the you-tube video, it does not do any transcoding. You can use whatever software you want to to extract audio or transcode it. IMHO FFmpeg is the best tool for this, but if you can get MEncoder to work go for it :-).

Andrew

Well thats the thing that Im confused about.  The videos that I have successfully pulled from youtube-dl were the same ones that I tried to pull from /tmp (cache).  The ones grabbed from cache (/tmp) couldnt play at all through via VLC, Mplayer, etc....  However those same vids using youtube-dl, I could play perfectly.  I did notice that youtube-dl gave me these files in a large file size (4 to 5 MB).  I know I upload vids all the time to youtube and it tends to dumb the quality down a bit after youtube processes it and puts it live.  Is that why youtube-dl gives me vids I can actually play?

---

### Post by andrew.46 on 2009-03-10
Hi Kat,

> **Kat of Zion said:**
> Well thats the thing that Im confused about.  The videos that I have successfully pulled from youtube-dl were the same ones that I tried to pull from /tmp (cache).  The ones grabbed from cache (/tmp) couldnt play at all through via VLC, Mplayer, etc....  However those same vids using youtube-dl, I could play perfectly.  I did notice that youtube-dl gave me these files in a large file size (4 to 5 MB).  

I suspect that something about the method you have used previously has resulted in youtube videos that are a little damaged in some way. Not sure what has happened there. youtube-dl has never caused me trouble though and it is my own preferred method.


> I know I upload vids all the time to youtube and it tends to dumb the quality down a bit after youtube processes it and puts it live.  Is that why youtube-dl gives me vids I can actually play?

Nobody really knows how youtube processes videos although there is a suspicion that they use FFmpeg to process the files. If you have a google around you will see some people's ideas on the best formats to present video clips to youtube. As for downloading youtube will give you what you ask for. There is a raft of options to youtube-dl that you can use if you want:

```

andrew@skamandros~$ youtube-dl --help
Usage: youtube-dl [options] url...

Options:
  -h, --help            print this help text and exit
  -v, --version         print program version and exit
  -u UN, --username=UN  account username
  -p PW, --password=PW  account password
  -o TPL, --output=TPL  output filename template
  -q, --quiet           activates quiet mode
  -s, --simulate        do not download video
  -t, --title           use title in file name
  -l, --literal         use literal title in file name
  -n, --netrc           use .netrc authentication data
  -g, --get-url         simulate, quiet but print URL
  -e, --get-title       simulate, quiet but print title
  -f FMT, --format=FMT  video format code
  -b, --best-quality    alias for -f 18
  -m, --mobile-version  alias for -f 17
  -i, --ignore-errors   continue on download errors
  -r L, --rate-limit=L  download rate limit (e.g. 50k or 44.6m)
  -a F, --batch-file=F  file containing URLs to download
  -w, --no-overwrites   do not overwrite files

```

The magic download is with --best-quality :-).

Andrew

---

### Post by pewterbot9 on 2009-04-19
> **lukjad007 said:**
> The best way I know for saving youtube videos is youtube-dl.

Very nice, thanks. I just tried this method on a flash video that wouldn't play (using VLC media player) after downloading via Firefox extension "download helper"...and it works like a charm! The video in question (in case anyone wants to test it out) is here:

[http://www.youtube.com/watch?v=8_tf25lx_3o](http://www.youtube.com/watch?v=8_tf25lx_3o)

It's another conspiracy video re. world trade towers. :P  

You don't have to accept the $HOME default location, or have to move/rename it afterwards...you can take care of all that in the command line. Example:

youtube-dl [http://www.youtube.com/watch?v=8_tf25lx_3o](http://www.youtube.com/watch?v=8_tf25lx_3o) --output=$HOME/downloads/thermite.flv

I created a generic command line to copy and paste into the terminal, which you then edit appropriately:

youtube-dl *[youtube path]* --output=$HOME/downloads/*[give it a name]*.flv

(Replace *[youtube path]* with the video's URL. Replace *[give it a name]* with the desired file name. If you don't use the same path for your downloads as I do, edit accordingly.)

Another method works (I just discovered), on *.flv files already downloaded: simply convert them with "OggConvert", which is listed in Synaptic. For whatever reason, the converted *.flv now works...even though I didn't change formats!

---

### Post by Ampersand. on 2009-04-30
It seems like whenever i download a video from the web, no matter what program or method, the sound does not play unless i use Avidemux.
The whole point of me downloading the video is usually to put it in a presentation for uni and if there is no sound this is useless.

Anybody got any ideas?

---

### Post by perspectoff on 2009-05-02
I can't believe how many complex solutions have been posted here.

No one reads Ubuntu guide?

there are great tips for doing this there which are very simple.

Ubuntu guide (ubuntuguide.org) at [http://ubuntuguide.org](http://ubuntuguide.org)

In brief:

Use the Video Download Helper plugin from Firefox. A single click saves the YouTube Flash video for you (as well as from hundreds of other sites).

Easy.

You can then watch the video with VLC or MPlayer.

You can also convert flash videos easily (using FFMPEG) to MPEG-2 videos, which will play on all DVD players.

Again, the details (which are quite simple) are outlined at Ubuntuguide.org.

In short:

```
ffmpeg -i savedvideo.flv -target ntsc-dvd outputvideo.mpg
```

Write the resulting MPEG-2 video to disc and play it in your dvd player.

If you have multiple MPEG-2 segments you wish to combine into one long video:

```
 cat video1.mpg video2.mpg video3.mpg > video123.mpg
```

How easy is that?

---

### Post by badrra on 2010-01-03
This is by far the best way to watch youtube videos using VLC, totem or mplayer. No need to navigate your way to /tmp. Just watch it on youtube. Try this link

[http://badrra.wordpress.com/2009/12/03/watch-youtube-using-vlc-mozilla-plugin/](http://badrra.wordpress.com/2009/12/03/watch-youtube-using-vlc-mozilla-plugin/)

have fun

---

### Post by timzak on 2010-06-13
Search Ubuntu Software Center for "download youtube" and the first entry is FatRat, a GUI app that does this.  Just another option...

---

### Post by KEE on 2010-09-05
> **iKonaK said:**
> Why not just go to /tmp and copy the flash after is loaded ?

lol,  so youtube-dl +url is no more? sigh...

---

### Post by d3v1150m471c on 2010-09-06
honestly, try the firefox addon "unplug". go to the youtube page and right click. select "unplug" and give it a couple seconds. you'll have your youtube video in no time at all. also, if you want to extract the sound from a video just:
```

ffmpeg -i youtubevideo.flv -sameq output.mp3

```

happy hunting.

---

### Post by KEE on 2010-09-06
> **d3v1150m471c said:**
> honestly, try the firefox addon "unplug". go to the youtube page and right click. select "unplug" and give it a couple seconds. you'll have your youtube video in no time at all. also, if you want to extract the sound from a video just:
```

ffmpeg -i youtubevideo.flv -sameq output.mp3

```

happy hunting.

how would you use that with other web-video sites? ```
ffmpeg -i http://www.gamaniak.com/video-3019-rodney-carrington-show-them-to-me.html -sameq output.mp3

```

---

### Post by KEE on 2010-09-06
> **d3v1150m471c said:**
> honestly, try the firefox addon "unplug". go to the youtube page and right click. select "unplug" and give it a couple seconds. you'll have your youtube video in no time at all. also, if you want to extract the sound from a video just:
```

ffmpeg -i youtubevideo.flv -sameq output.mp3

```

happy hunting.how do you use that? where is the url inserted?

---

### Post by KEE on 2010-09-06
lol nvm im tired just got it

---

### Post by dannyboy79 on 2010-09-06
the easist way is to merely watch the video and then in your /tmp/ folder there is the flash video you just watched. copy it out of /tmp/ and your golden

---

### Post by scorp123 on 2010-09-06
> **KEE said:**
> lol,  so youtube-dl +url is no more? sigh... You have to get the newest release from their homepage. The release which is available in the repos is outdated and doesn't work any more.

YouTube-DL Homepage:
[http://bitbucket.org/rg3/youtube-dl/wiki/Home](http://bitbucket.org/rg3/youtube-dl/wiki/Home)

(... Go down to the "Download it ... " part ...)

---

