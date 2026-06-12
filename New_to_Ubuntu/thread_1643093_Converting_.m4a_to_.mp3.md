---
title: "Converting .m4a to .mp3"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by PaleoNerd on 2010-12-11
Hi all, 

I'm in the process of switching over to Ubuntu from Mac OS X. As such all my music files are in .m4a format. As I have an extensive music format and don't really want to pirate all my music in .mp3 format is there any program for Linux that will convert .m4a to mp3?

Thanks

---

### Post by TeoBigusGeekus on 2010-12-11
Try with ffmpeg from command line:
```
ffmpeg -i filename.m4a -acodec libmp3lame -ab 320k filename.mp3
```
All the gui programs you'll find for this job are frontends to ffmpeg anyway.

---

### Post by AlphaLexman on 2010-12-11
I believe the cross-platform 'vlc' media player could do your request via: media -> conve_r_t/save (Ctrl-R).

---

### Post by papibe on 2010-12-11
> **TeoBigusGeekus said:**
> ...
All the gui programs you'll find for this job are frontends to ffmpeg anyway.

like WinFF which is nice and simple.

Regards.

---

### Post by HermanAB on 2010-12-11
even Mplayer has command line options for transcoding.

---

### Post by Jose Catre-Vandis on 2010-12-11
Here's a script for doing the conversion on a directory full of m4a files. You need to put the script inside the directory. Modify the bitrate from 192 if you want it higher.

```
#!/bin/bash

#convert m4a to mp3

FILES="*.m4a"

for F in $FILES

do
newname=`basename "$F" .m4a`
echo $newname
ffmpeg -i "$F" -acodec libmp3lame -ac 2 -ab 192k -ar 44100 "$newname.mp3"

done
```

---

### Post by slooksterpsv on 2010-12-11
XCFA is what I use, it's gui and it's simple. You just need to install XCFA and lame - yes the package is called lame (LAME) haha - just search software center for it and you'll find them.

---

### Post by nothingspecial on 2010-12-11
I`d just leave them as they are.

Well, actually I`d re-rip the lot to flac, assuming they are cds in the first place.

If they were bought from iTunes, I`d leave them.

One lossy format to another means more loss (so I`ve read).

---

### Post by Norm24 on 2010-12-11
Install Sound Converter.Its in the repos.

---

### Post by khelben1979 on 2010-12-11
I agree with TeoBigusGeekus in using [FFmpeg]("http://en.wikipedia.org/wiki/Ffmpeg") for this. It's powerful software and it's a good idea to spend some time with it.

---

### Post by wildmanne39 on 2012-11-14
Old thread closed.

---

