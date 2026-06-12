---
title: "Turn sideways video upright"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-03-01
I made a couple of videos in portrait mode, so they're on their side.

I thought I'd find it easy to rotate them upright, but despite lots of Googling and experimenting, I still have problems.

I'm using Avidemux. I've managed to turn the picture upright, but two problems happen:

[LIST=1]
[*]The picture is jerky, as though a number of frames have been cut out.
[*]Avidemux adds its own subtitle to the front; as the clip is only a few seconds long, it interferes with what's being shown.
[/LIST]
I wonder if someone can tell me how to simply turn the picture upright (90 degrees) without changing the frame rate or quality, and without adding any subtitles?

My videos were recorded as MP4 (mpeg-4).

I'd prefer to use a GUI, if possible, but I'll use a command line if necessary.

My system: Hardy 8.04
Avidemux version 2.4.1

---

### Post by gsmanners on 2010-03-01
Unless you need to reencode, you can just simply play back with mplayer. Add the following option to your command line:

-vf rotate=1

Or use rotate=2 if you want counterclockwise.

---

### Post by Paddy Landau on 2010-03-02
Thanks for the suggestion.

I need to send the videos to a friend (they were from his wedding), so I need to turn them upright.

I suspect that the defaults on Avidemux are causing the problem, but I'm no expert in video settings, so I don't even know what to look for.

---

### Post by gsmanners on 2010-03-02
[Avidemux]("https://launchpad.net/avidemux") has a lot of codecs built in, and because you're using an older version, there's really no telling if it has what you need.

I think you may need to upgrade to Karmic if you want to try the latest version. The latest Avidemux with all its dependencies will not likely compile on Hardy.

---

### Post by Jose Catre-Vandis on 2010-03-02
Here is a command that will rotate but will also re-encode ( I don't think you are going to get rotation without encoding....
```
mencoder -vf rotate=1 -o OUTPUT.AVI -oac copy -ovc lavc INPUT.AVI
```
That said you could play with quality setting (e.g. make a "bigger" output file to preserve quality)

---

### Post by Paddy Landau on 2010-03-02
Thanks for the idea. I used your command and got an error message:
[FONT=Courier New]Audio format 0x6134706d is incompatible with '-oac copy', please try '-oac pcm' instead or use '-fafmttag' to override it.[/FONT]

So I used [FONT=Courier New]-oac pcm[/FONT] and it worked...

But the two files went form 553Kb and 1.8Mb to an astonishing 2.3Mb and 7.4Mb respectively!

But at least the quality was kept, thank you.

Why does the file grow more than four times as large just to rotate the picture? Surely it can figure it out better than that?

---

### Post by gsmanners on 2010-03-02
The size increase is probably from switching audio from AAC to PCM (from around 100 to 200 kbit/s to 1411 kbit/s). PCM really isn't suitable for video. I would reencode into Vorbis, which would keep the quality reasonable and keep the bitrate low.

---

### Post by Paddy Landau on 2010-03-02
> **gsmanners said:**
> The size increase is probably from switching audio from AAC to PCM (from around 100 to 200 kbit/s to 1411 kbit/s). PCM really isn't suitable for video. I would reencode into Vorbis, which would keep the quality reasonable and keep the bitrate low.
Thank you for the explanation. Following on from your logic, I tried again with mp3lame, and this time it merely doubled the size.

I don't know how to reencode into Vorbis (I know next-to-nothing about videos and codecs and stuff like that).

Why isn't it possible to just copy the audio, not reencode it?

---

### Post by gsmanners on 2010-03-02
I think the problem is that there is no "standard" way to copy (or encode for that matter) AAC into an AVI file. If you want that audio track in a proper reencode, it really should be mp4 (or mkv if you don't need to worry about hardware players).

---

### Post by Paddy Landau on 2010-03-02
> **gsmanners said:**
> I think the problem is that there is no "standard" way to copy (or encode for that matter) AAC into an AVI file. If you want that audio track in a proper reencode, it really should be mp4 (or mkv if you don't need to worry about hardware players).
The input file and the output file are both mp4. I didn't want to convert anything; I simply want to turn the video 90 degrees clockwise. I wish there were an easy way without significantly increasing the size!

---

### Post by gsmanners on 2010-03-02
I guess mencoder doesn't mux everything. Well, you could try this:

mencoder -vf rotate=1 -o output.mp4 -nosound -ovc lavc input.mp4
mplayer input.mp4 -dumpaudio -dumpfile audio.aac
ffmpeg -i output.mp4 -i audio.aac -vcodec copy -acodec copy output2.mp4

---

### Post by fatality_uk on 2010-03-02
Give openshot a go.
It has "apparently" a rotate function.

[http://www.openshotvideo.com/](http://www.openshotvideo.com/)

---

### Post by Paddy Landau on 2010-03-02
Thank you; it looked good, but sadly the final result had no sound (with VLC) or gave an error (with Movie Player).

Thanks so much for your help. I'll just have to live with double the size, no big problem, unless you have any clever ideas.

---

### Post by Paddy Landau on 2010-03-02
> **fatality_uk said:**
> Give openshot a go.
I'll try tomorrow (it's getting really late here) and post the results.

---

### Post by Jose Catre-Vandis on 2010-03-02
> **Paddy Landau said:**
> The input file and the output file are both mp4. I didn't want to convert anything; I simply want to turn the video 90 degrees clockwise. I wish there were an easy way without significantly increasing the size!

It can be done but takes a bit of work to start off with. See [here]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-quicktime-7.html") and scroll down to 11.7.8 for how to do it properly

---

### Post by Paddy Landau on 2010-03-02
> **fatality_uk said:**
> Give openshot a go.
It looks awesome. Unfortunately, on my machine, the help doesn't work (luckily there is on-line help), and the moment I try to save, OpenShot crashes. :( I'll have to wait until I upgrade to Lucid.

---

### Post by Paddy Landau on 2010-03-02
> **Jose Catre-Vandis said:**
> It can be done but takes a bit of work to start off with. See [here]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-quicktime-7.html") and scroll down to 11.7.8 for how to do it properly
Thanks for the link.

That's getting more complicated than I have time for (I am not a video expert!), so I'll leave it as I've managed now; I'll live with double the size.

Thanks again to all for your help.

---

### Post by OrangeCrate on 2010-03-02
When I saw the "**SOLVED**", I couldn't click on this thread fast enough...

There's been an ongoing problem with Totem over the same issue, but alas no solution yet:

> there's no support for rotate videos on totem yet, there's an upstream bug created about that, you can track it here: [http://bugzilla.gnome.org/show_bug.cgi?id=589399](http://bugzilla.gnome.org/show_bug.cgi?id=589399)

[https://bugs.launchpad.net/totem/+bug/421537](https://bugs.launchpad.net/totem/+bug/421537)

Oh well, interesting thread. Thanks.

---

### Post by Paddy Landau on 2010-03-02
> **OrangeCrate said:**
> There's been an ongoing problem with Totem over the same issue, but alas no solution yet:
Ah, right, this thread was intended to be about changing the video, not just its playback.

But as gsmanners said in [Post 2]("http://ubuntuforums.org/showthread.php?p=8901771#post8901771"), you can use mplayer.

---

### Post by OrangeCrate on 2010-03-02
> **Paddy Landau said:**
> Ah, right, this thread was intended to be about changing the video, not just its playback.

But as gsmanners said in [Post 2]("http://ubuntuforums.org/showthread.php?p=8901771#post8901771"), **you can use mplayer**.

Even as you were typing this, I was looking at the documentation on mplayer. Thanks to you and gsmanners for the tip.

---

### Post by Paddy Landau on 2011-04-03
> **gsmanners said:**
> I guess mencoder doesn't mux everything. Well, you could try this:

mencoder -vf rotate=1 -o output.mp4 -nosound -ovc lavc input.mp4
mplayer input.mp4 -dumpaudio -dumpfile audio.aac
ffmpeg -i output.mp4 -i audio.aac -vcodec copy -acodec copy output2.mp4
I have been rereading this thread, because I have another video that I need to rotate. Somehow, the first time around it seems I had missed this post by gsmanners.

I have tried it. On the last command (ffmpeg), I get the error:
```
 audio.aac: could not find codec parameters
```Looking at audio.aac, I see that it lacks any information about codecs. Indeed, Movie Player and VLC are unable to play it.
I tried the following command but had the same error:
```
ffmpeg -i output.mp4 -i audio.aac -vcodec copy -acodec **aac** output2.mp4
```Any ideas?

---

### Post by Paddy Landau on 2011-04-03
I found a way without expanding the resulting video. I don't pretend to understand the settings, but this is what I did:

[LIST]
[*]Open the file in Avidemux.
[*]Set the Video type to MPEG-4 ASP (lavc).
[*]Use the Filters to transform (rotate) the video.
[*]In the Configure section, I set User Interface > Encoding mode > Single pass - same as qz input, and Quantization > Quantization type > MPEG.
[*]Save with the extension .mp4.
[/LIST]
I hope that helps someone having a similar problem.

---

