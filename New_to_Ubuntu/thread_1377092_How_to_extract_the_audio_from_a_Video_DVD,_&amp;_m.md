---
title: "How to extract the audio from a Video DVD, &amp; make an mp3 file?"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by swarup on 2010-01-09
I've been researching this on the web, and found a [site]("http://linux.byexamples.com/archives/229/extract-audio-from-video-or-online-stream/") where it is explained one can "extract audio from video files such as avi, mpg, even flv! into mp3 using mplayer" in the following command:

```
mplayer -dumpaudio nodame_theme.flv -dumpfile nodame_theme.mp3  
```

But on a video DVD, the video is not in any of the above formats. The video is in a VIDEO_TS folder, and the file is of type .VOB.

So I guess I need to extract the .VOB files off the Video DVD, and perhaps convert them to avi in order to use the above command?

Or does anyone know a better/easier way? Is there a gui application that will do this?

---

### Post by nerdy_kid on 2010-01-09
i think KdenLive will do it...

---

### Post by swarup on 2010-01-09
> **nerdy_kid said:**
> i think KdenLive will do it...

I just installed it. Can you give me a little guidance how to move ahead with it? I tried to open the DVD Video_TS folder, with the thought that I would use the programs "split audio" command. But it will not even allow me to see the .VOB files in the Video_TS folder of the DVD. The program is looking only for files of type "Kdenlive video project document".

---

### Post by nerdy_kid on 2010-01-10
[edit]
install k9copy and you are set to go! (for real this time LOL)

---

### Post by swarup on 2010-03-23
> **nerdy_kid said:**
> [edit]
install k9copy and you are set to go! (for real this time LOL)

I installed k9copy, and it looks like it should do the job. But ultimately it just gave me an error message. 

Here is what I did, followed by a detailed report of the error message that came:


There is a wizard in the software, which allows you to select "extract audio". I opted for that, with the source set to "DVD drive" and the destination set to a folder in my home directory. There are four tracks on the DVD (two "titles", each with two "chapters"). Of these four tracks, I selected the first one track (chapter 1, 00:26:55, 532.97 MB) to be extracted. It then asks you to "Select the streams you want to keep". It gave me two options-- "Title 1, 1- unknown pcm 2 ch" or "Title 2, 1- unknown pcm 2 ch". I opted for the first one i.e. Title 1. It then shows the default settings for the encoder ("ffmpeg"), and the codec ("mp3 [ffmpeg]") which I accepted (there were actually no other options in the drop-down menu). Bitrate default set to 128, and gain to 7.

When I then select "finish", most of the time it immediately gives an error message with the following output:

> An error occured while encoding the audio stream

FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
configuration: --enable-gpl --enable-postproc --enable-swscale --eneable-xllgrab --extra-version=svn17737+3.0-svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgrm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static

[there follow settings for libavutil, libavcodec, libavformat, libavdevice, libavfilter, libswscale, libpostproc]

built on Apr 10 200923:20:33, gcc: 4.3.3

Input  #0, mpeg, from '/dev/stdin':
 Duration: N/A, start: 0.246467, bitrate 1536 kb/s
  Stream #0.0[0xa0]: Audio: pcm_s16be, 48000 Hz, stere0, s16, 1536 kb/s
Unable to find a suitable output format for "/home/swarup/Documents/RSS 41-44/title1-part1-audio1-Unknown-.mp3"


I tried it about five times, each time immediately giving the above error. Once, it actually went ahead and seemed like it was going to do the job. It give the info that the job would take ~7 minutes, and started to work-- showing a "transcoding" window displaying static views of the video as it did its work. But ultimately, about half way through the process it stopped and gave some error message that it could not output to the selected format (which was the only format available from the wizard).

---

### Post by 3rdalbum on 2010-03-23
I think everyone has a different way of doing it. For K9Copy you will probably need the "lame" and "libmp3lame" packages - check that you have them.

The way I do it is to rip the video from the DVD first, and then feed the video file into Audacity. Hey, I'm going to have to edit it anyway...

To rip the DVD, I use Acidrip, but I make sure that the filename has spaces in it. This way it will only decrypt and copy the raw DVD video file (and then complain of an error, which you can ignore). The file will be dumped into /tmp, so you can just move it out of there and import it into Audacity.

---

### Post by swarup on 2010-03-23
> **3rdalbum said:**
> I think everyone has a different way of doing it. For K9Copy you will probably need the "lame" and "libmp3lame" packages - check that you have them.

The way I do it is to rip the video from the DVD first, and then feed the video file into Audacity. Hey, I'm going to have to edit it anyway...

To rip the DVD, I use Acidrip, but I make sure that the filename has spaces in it. This way it will only decrypt and copy the raw DVD video file (and then complain of an error, which you can ignore). The file will be dumped into /tmp, so you can just move it out of there and import it into Audacity.

Thanks for the tip.

1. I just installed acidrip. Could you give a bit more detail as to what one has to set in acidrip to rip the DVD? And then when you say you feed the video file into audacity, doesn't audacity only deal with audio files?

2. I have tried another DVD with K9Copy. It is a DVD which has only one, fairly large, video on it. K9Copy accepted the job, and has been doing it for the last hour and 40 minutes. The DVD is spinning, and scenes are showing in the transcoding window. But I am getting suspicious that perhaps nothing is happening, for wouldn't you expect that the job would be finished by now? In the beginning it seemed to indicate that the job would take 8 minutes, and the progress bar moved across ultimately reaching to the 99% mark within that time-- but never got to 100%. This program is looking more and more like a dud.

---

### Post by 3rdalbum on 2010-03-23
> **swarup said:**
> Thanks for the tip.

1. I just installed acidrip. Could you give a bit more detail as to what one has to set in acidrip to rip the DVD? And then when you say you feed the video file into audacity, doesn't audacity only deal with audio files?

Most of the settings are just for transcoding the DVD, but if you put a name with spaces into the "Track Title" field it will interrupt the process before transcoding happens. So just choose anything for audio codec and video codec.

Under the Settings tab choose "Cache DVD" and "Precache Video" (all other options are fine too). You might as well set the "Cache" field to somewhere in your home directory.

Insert your DVD and click Load, put in a track title with spaces in the name such as "music dvd", and then choose what track you want to rip and click Queue and then Start.

When it reaches 50%, the process will "stop with an error". You will have the temporary file in your home directory or wherever the "Cache" is set to go.

You can tell Audacity to **import** this file. It will transparently use FFMPEG to get just the audio part of it.

Note you also need the *libmp3lame0* package to create MP3s from Audacity, and the *libdvdcss2* package from Medibuntu in order to rip DVDs.

---

### Post by swarup on 2010-03-23
Thanks a lot! I'll try this out. :)

I'm still waiting for the day when there will be a program which will do all this work with one click, and output the audio for you in mp3 format. (When you have two hundred files to do from a variety of DVD's, the multiple-step method takes a lot of time.)

---

### Post by Soul-Sing on 2010-03-23
this site is great: [http://www.ubuntugeek.com/how-to-rip-dvd-audio-to-mp3-or-ogg.html](http://www.ubuntugeek.com/how-to-rip-dvd-audio-to-mp3-or-ogg.html)

---

### Post by swarup on 2010-03-23
> **leoquant said:**
> this site is great: [http://www.ubuntugeek.com/how-to-rip-dvd-audio-to-mp3-or-ogg.html](http://www.ubuntugeek.com/how-to-rip-dvd-audio-to-mp3-or-ogg.html)

Have you ever tried it? The reason I ask is the the comments written in by others at the bottom of that page suggest there may be significant problems with the technique given. I do get a bit nervous by seeing all the fancy terminal code, followed by comments by people who have had difficulty with it and could not get it to work.

---

