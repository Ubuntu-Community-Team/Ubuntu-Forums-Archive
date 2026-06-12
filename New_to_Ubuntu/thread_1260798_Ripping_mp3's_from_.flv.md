---
title: "Ripping mp3's from .flv"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by mysticaltopher on 2009-09-08
I'm having problems ripping the audio from .flv videos (ones downloaded from youtube).  I've searched for an answer but havn't found out what the deale-o is yet.
it keeps telling me: unsupported video codec or unsupported coded.
Is there a lib package that must be installed that i am missing?
thx.

btw, i have libmp3lame.so.0 already installed, i think i need this right?

oh, and im using winff

---

### Post by MelDJ on 2009-09-08
are you using a converter? or maybe just use fetchmp3.com

---

### Post by credobyte on 2009-09-08
```
sudo apt-get install ffmpeg
ffmpeg -i source.flv soundonly.mp3

```** ffmpeg command might need some tweaking ( bitrate, etc. )

---

### Post by ken_do_san on 2009-09-08
Give mobile media converter a try, always works for me, where .flv are concerned if you want to convert them :)

---

### Post by andrew.46 on 2009-09-08
Hi mysticaltopher,

> **mysticaltopher said:**
> I'm having problems ripping the audio from .flv videos (ones downloaded from youtube).  I've searched for an answer but havn't found out what the deale-o is yet.
it keeps telling me: unsupported video codec or unsupported coded.
Is there a lib package that must be installed that i am missing?

There are some special issues with FFmpeg and Ubuntu which probably means that your version of FFmpeg is missing a few vital codecs. For some details and a fix have a look at:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

I have little experience with WinFF but I know that what you are after can easily be done with FFmpeg itself from the commandline (and doubtless just as easily from the excellent WinFF!). If you can get your version of FFmpeg fitted out with all the codecs try running the following from the commandline:

```
ffmpeg -i **[COLOR="Red"]*my_file.flv*[/COLOR]**
```

and this will give an indication of the finer details required for the extraction of the mp3 audio alone, as credobyte has mentioned in his post. If you are happy with all of this could you post the terminal output here?

All the best,

Andrew

---

### Post by MrWES on 2009-09-08
I used this guide to compile ffmpeg and get a fully unlocked version to allow me transcoding on my mediatomb server:

It was a matter of copy and paste.

[http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

~Bill

---

### Post by scorp123 on 2009-09-08
> **mysticaltopher said:**
> I'm having problems ripping the audio from .flv videos (ones downloaded from youtube). I'd suggest you get the "ubuntu-restricted-extras" package if you don't have it already and then include the "Medibuntu" repository (tons and tons of codecs and what not):

[http://www.medibuntu.org/](http://www.medibuntu.org/)

From there you should get vlc, mplayer, mencoder, ffmpeg ... and those should pull in tons of other dependencies which should then have the result that multimedia-wise you will be able to play, watch, listen to and rip pretty much anything.

I myself use this simple shell command to get MP3 audio out from e.g. YouTube-like videos:
```
ffmpeg -i vid.flv -acodec copy output.mp3
```

Shamelessly copied from here:
[http://symbolik.wordpress.com/2007/10/10/extracting-an-mp3-from-a-youtube-flash-flv-download/](http://symbolik.wordpress.com/2007/10/10/extracting-an-mp3-from-a-youtube-flash-flv-download/)

---

### Post by andrew.46 on 2009-09-08
Hi,

A technique is available from MPlayer as well, although you will get better results with FFmpeg. If you *know *the audio is mp3 you can run:

```
mplayer input.flv -dumpaudio -dumpfile output.mp3
```

However if the audio is actually aac you will get a file called output.mp3 that is actually an aac file and probably unreadable...

Andrew

---

