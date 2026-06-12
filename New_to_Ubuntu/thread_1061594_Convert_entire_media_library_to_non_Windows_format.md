---
title: "Convert entire media library to non Windows formats?"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by HittingSmoke on 2009-02-05
I have a lot of video saved from over the years and just recently ran into my first problem getting something to play in Ubuntu.

VLC wont seem to play some of my Red vs Blue collection. Everyone seems to say that VLC isn't good with WMV. The specifics are they then wont play audio in WMV files where the audio is encoded in the WMV3 audio codec.

I like VLC and don't want to install a bunch of new players (or even one for that matter) to accommodate my file types.

So, to my question. Can I use ffmpeg to do one mass conversion of my media collection using wildcards? i.e. run a command to turn all *.WMV files to *.mpeg or whatever is the most common video format on Linux?

I also used to save space on Windows by ripping my CD's in WMA so I would like to convert those to MP3 in the same manner if possible.

---

### Post by jerome1232 on 2009-02-06
[http://ubuntuforums.org/showthread.php?t=1023231](http://ubuntuforums.org/showthread.php?t=1023231)

post number two was a great script. It simply converts every file of a specified extension to another. You'll have to modify to suite your needs exactly but it worked perfect for converting a bunch of .flv videos to .avi for me.

so it's end up being something like

```
for f in *.wmv
do ffmpeg -i "$f" "${f%.wmv}.avi"
done
```

---

### Post by HittingSmoke on 2009-02-06
> **jerome1232 said:**
> [http://ubuntuforums.org/showthread.php?t=1023231](http://ubuntuforums.org/showthread.php?t=1023231)

post number three was a great script. It simply converts every file of a specified extension to another. You'll have to modify to suite your needs exactly but it worked perfect for converting a bunch of .flv videos to .avi for me.

so it's end up being something like

```
for f in *.wmv
do ffmpeg -i "$f" "${f%.flac}.avi"
done
```

This sounds like exactly what I want, but it's a little beyond my grasp. I copied what you posted here into a script and ran it and I get the following output,

> chris@chris-desktop:~/Music$ ./convert
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, asf, from 'RvB_Episode47.wmv':
  Duration: 00:05:34.9, start: 3.000000, bitrate: 1374 kb/s
    Stream #0.0: Audio: 0x0162, 48000 Hz, stereo, 348 kb/s
    Stream #0.1: Video: wmv3, yuv420p, 640x480 [PAR 0:1 DAR 0:1], 1000 kb/s, 29.97 tb(r)
Output #0, avi, to 'RvB_Episode47.wmv.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 0:1 DAR 0:1], q=2-31, 200 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: mp2, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Unsupported codec (id=0) for input stream #0.0


I tried this with a working WMV file in the directory as well and it converted to AVI perfectly fine. The major difference here seems to be the WMV3 vs the WMV2 codec. The video runs fine on both, but WMV3 encoded videos wont play audio, and ffmpeg doesn't seem to like it either. Mplayer is the only player I can find that will play the WMV3 videos with audio. I would much prefer to stick with VLC.

Any ideas on what I can do to get this codec supported?

---

### Post by jerome1232 on 2009-02-06
Whoops I made a small typo in my original post but I don't think it was something that would affect functionality, just the way files are getting renamed. (changed the .flac to .wmv)

Dang, I was hoping that would work unfortunately I'm not an ffmpeg guru I think we have need of somebody that really knows ffmpeg and their codecs to help out here.

So it works correctly on the wmv2 but not the wmv3 correct (the wmv3 are the ones that are giving you hell right?)

---

### Post by HittingSmoke on 2009-02-06
> **jerome1232 said:**
> Whoops I made a small typo in my original post but I don't think it was something that would affect functionality, just the way files are getting renamed. (changed the .flac to .wmv)

Dang, I was hoping that would work unfortunately I'm not an ffmpeg guru I think we have need of somebody that really knows ffmpeg and their codecs to help out here.

So it works correctly on the wmv2 but not the wmv3 correct (the wmv3 are the ones that are giving you hell right?)

Right, they're all .wmv extensions, but after doing some digging I used the Mediainfo package to get specific codec info on each file. All of the ones that play list WMV2 as the audio codec while all of the ones that wont play audio list the WMV3 codec.

Also, in my output,
> Duration: 00:05:34.9, start: 3.000000, bitrate: 1374 kb/s
Stream #0.0: Audio: 0x0162, 48000 Hz, stereo, 348 kb/s
Stream #0.1: Video: wmv3, yuv420p, 640x480 [PAR 0:1 DAR 0:1], 1000 kb/s, 29.97 tb(r)
Output #0, avi, to 'RvB_Episode47.wmv.avi':
Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 0:1 DAR 0:1], q=2-31, 200 kb/s, 29.97 tb(c)
Stream #0.1: Audio: mp2, 48000 Hz, stereo, 64 kb/s
Stream mapping:
Stream #0.1 -> #0.0
Stream #0.0 -> #0.1
Unsupported codec (id=0) for input stream #0.0 
you can see that the error listed is input stream #0.0, which is audio.

Is this just a new codec that only Mplayer supports? I really hate the Mplayer interface and don't want to be forced to use it.

*EDIT* but if there was a typo it didnt effect your script, it works perfectly on the WMV2 audio codec videos.

---

### Post by jerome1232 on 2009-02-06
Okay, I think Mencoder supports wmav3 (doing some searching that's what the audio codec is)

[http://www.linuxlinks.com/article/20080714101747615/MEncoder.html](http://www.linuxlinks.com/article/20080714101747615/MEncoder.html)

I have to look at mencoders man page to figure out how it's usage goes. So far it's not as easy as ffmpeg is.

```
man mencoder
``` to have a look yourself.


-edit- progress actually
it seems to be something like this

```
mencoder input.wmv -o output.avi -oac mp3lame -ovc lavc
```

Which slipped into that script should be like this (I think)

```
for f in *.wmv
do mencoder "$f" -o "${$f%.wmv}.avi" -oac mp3lame -ovc lavc
done
```

---

### Post by HittingSmoke on 2009-02-06
> **jerome1232 said:**
> Okay, I think Mencoder supports wmav3 (doing some searching that's what the audio codec is)

[http://www.linuxlinks.com/article/20080714101747615/MEncoder.html](http://www.linuxlinks.com/article/20080714101747615/MEncoder.html)

I have to look at mencoders man page to figure out how it's usage goes. So far it's not as easy as ffmpeg is.

```
man mencoder
``` to have a look yourself.


-edit- progress actually
it seems to be something like this

```
mencoder input.wmv -o output.avi -oac mp3lame -ovc lavc
```

Which slipped into that script should be like this (I think)

```
for f in *.wmv
do mencoder "$f" -o "${$f%.wmv}.avi" -oac mp3lame -ovc lavc
done
```

I tried your script and got this output,
```
./convert2: line 2: ${$f%.wmv}.avi: bad substitution

```

I checked out the mencoder man page and it looked more like a man page for mplayer than an encoder. Almost all the commands were mplayer related and not related to converting codecs. Did I miss something there?

---

### Post by jerome1232 on 2009-02-06
No you have to search for it just type "/mencoder" enter and keep hitting "n" (for next) to find relavent sections

or to look at certain options (like -oac) just hit "/oac" then hit enter and start hitting "n" to get to the right sections.

It is a massive man page because it explains mplayer and mencoder (annoying if you ask me)

What about just doing it on one file with the basic syntax, get the one line command working before tackling the script. ;) Remember this is unfamiliar ground for me too.

```
mencoder input.wmv -o output.avi -oac mp3lame -ovc lavc
```


--edit--

and I think I threw in an extra dollar sign
```
for f in *.wmv
do mencoder "$f" -o "${f%.wmv}.avi" -oac mp3lame -ovc lavc
done
```

---

### Post by HittingSmoke on 2009-02-06
> **jerome1232 said:**
> No you have to search for it just type "/mencoder" enter and keep hitting "n" (for next) to find relavent sections

or to look at certain options (like -oac) just hit "/oac" then hit enter and start hitting "n" to get to the right sections.

It is a massive man page because it explains mplayer and mencoder (annoying if you ask me)

What about just doing it on one file with the basic syntax, get the one line command working before tackling the script. ;) Remember this is unfamiliar ground for me too.

```
mencoder input.wmv -o output.avi -oac mp3lame -ovc lavc
```


--edit--

and I think I threw in an extra dollar sign
```
for f in *.wmv
do mencoder "$f" -o "${f%.wmv}.avi" -oac mp3lame -ovc lavc
done
```

Ok! We've got progress. That fixed script converts the WMV into an AVI that will play properly in VLC, but there is a HUGE loss in video quality, were talking at least a 50% loss in resolution. I'm gonna toy with options in the man pages tomorrow if I get a chance. It's my b-day and I'm geting forcibly dragged out so I may not get to report any progress until after the weekend.

Thanks for sticking with me on this! I'm really optimistic that we can have a solution for people switching from Windows with a large collection of unfriendly encoded media. More to come :)

---

### Post by jerome1232 on 2009-02-06
Okay so I was bored today and I think I'm starting to figure out mencoder, If you want to I think we can just copy the video and transcode the audio to wmav2 which works in all your media players, this envolves the least amount of transcoding which is always good (transcoding always loses quality). Although I think I've figured out how to mess with the video quality settings as well.

So. To just copy video and transcode audio (leaving files wmv files but audio is encoded using wmav2)

```
for f in *.wmv
do mencoder "$f" -o "${f%.wmv}.copy.wmv" -ovc copy -oac lavc acodec:wmav2
done
```

and if you want to migrate from wmv entirely I would go with mpeg4 video (uses divx)

```
for f in *.wmv
do mencoder "$f" -o "${f%.wmv}.avi \
-ovc lavc vcodec:mpeg4 vbitrate=12000 \
-oac mp3lame
done
```

let me know if this helps any, in the manpage searchign for lavc should get you to the sections I'm using to figure this out.

---

