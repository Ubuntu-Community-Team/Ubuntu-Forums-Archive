---
title: "Need a program to convert audio files to .ogg"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Ewingo401 on 2009-12-31
Hi guys.  As the title suggests I need a program that will convert several different audio files (mp3, wma, etc) to .ogg.  I'm trying to make my system as "free" as possible and figured that eliminating the need for mp3 playback support would be a good place to start.  So does anyone know of a free and easy to use program that can get this done for me?  I'm not scared of the command line either, so there is no need to exclude CLI only programs.

---

### Post by adelphos on 2009-12-31
There is an easy drag-and-drop GUI program for such simple coversions called "soundconverter." I used it to convert a bunch of FLAC files to mp3, but it also supports Ogg Vorbis output.

---

### Post by e-Gee on 2009-12-31
WinFF

---

### Post by HappyFeet on 2009-12-31
> **e-Gee said:**
> WinFF

Winff is a video converter.

---

### Post by adelphos on 2009-12-31
I should also mention that you are going to experience a loss in quality by converting from mp3 to ogg. Whenever you move between compression formats, there is a loss. I assume that you already know that, and are willing to accept the loss for a gain in 'freedom', but I thought I'd mention it.

---

### Post by SuperSonic4 on 2009-12-31
> **adelphos said:**
> There is an easy drag-and-drop GUI program for such simple coversions called "soundconverter." I used it to convert a bunch of FLAC files to mp3, but it also supports Ogg Vorbis output.

GUI + Many conversions = CPU Kill

Not literally of course but unless you have lots of CPU and RAM it will render the PC unusable.

My choice would be [pacpl](http://pacpl.sourceforge.net/downloads.html) - you can still use the CLI interface

```
pacpl -t ogg -v -r -o mp3 -p -oggqual 5 . --outdir .
```

-o mp3 -- only convert mp3 files
-r     -- recursive
-p     -- keep directory structure
-oggqual 5 -- oggqual (I think 5 is about 192kbps?)
--outdir - where to put the files
.        - current dir

---

### Post by spcwingo on 2009-12-31
> **HappyFeet said:**
> Winff is a video converter.

It does audio too...see attached screenie.

---

