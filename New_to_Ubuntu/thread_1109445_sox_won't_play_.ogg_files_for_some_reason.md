---
title: "sox won't play .ogg files for some reason"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by davidstri on 2009-03-28
I tried playing an .ogg file with sox, e.g ```
play whatever.ogg
```, but I get this error "play soxio: Can't open input file `david.ogg': unknown file type `ogg'". I then tried playing a .wav file which worked. Anyone know how to fix this problem?

---

### Post by logos34 on 2009-03-28
are you sure it's actually an .ogg?

file whatever.ogg

or

ogginfo whatever.ogg

ogg vorbis support is enabled by default in both the source pkg and ubuntu deb, so I can't see how that would be the issue

sox -h 

(--> 'Supported file formats')

---

### Post by ad_267 on 2009-03-28
```
sudo apt-get install libsox-fmt-ogg
```
or
```
sudo apt-get install libsox-fmt-all
```

---

### Post by davidstri on 2009-03-28
I entered sox -h and this is what I got: SUPPORTED FILE FORMATS: 8svx aif aifc aiff aiffc al alsa au auto avr cdda cdr cvs cvsd dat dvms fssd hcom ima ircam la lpc lpc10 lu m3u maud nist nul null pls prc raw s1 s2 s3 s4 sb sf sl smp snd sndt sou sph sw txw u1 u2 u3 u4 ub ul uw vms voc vox wav wavpcm wve xa....the .wav format is there, but .ogg is missing. Maybe I need to re-install sox?

---

### Post by davidstri on 2009-03-28
Yes! ```
sudo apt-get install libsox-fmt-all
``` worked. Thanks.

---

### Post by logos34 on 2009-03-28
> **davidstri said:**
> I entered sox -h and this is what I got: SUPPORTED FILE FORMATS: 8svx aif aifc aiff aiffc al alsa au auto avr cdda cdr cvs cvsd dat dvms fssd hcom ima ircam la lpc lpc10 lu m3u maud nist nul null pls prc raw s1 s2 s3 s4 sb sf sl smp snd sndt sou sph sw txw u1 u2 u3 u4 ub ul uw vms voc vox wav wavpcm wve xa....the .wav format is there, but .ogg is missing. Maybe I need to re-install sox?

so, you installed sox from the repos?  That's strange, no ogg or vorbis listed...

It should sth look like this:

> $ sox -h

SUPPORTED FILE FORMATS: 8svx aif aifc aiff aiffc al alsa au auto avr caf cdda cdr cvs cvsd dat dvms fap fssd gsm hcom ima ircam la lu mat mat4 mat5 maud mp2 mp3 nist nul null **ogg** ossdsp paf prc pvf raw s3 sb sd2 sds sf sl smp snd sndfile sndt sou sph sw txw u3 u4 ub ul uw vms voc **vorbis** vox w64 wav wve xa xi

> $ play -h 

SUPPORTED FILE FORMATS: 8svx aif aifc aiff aiffc al alsa ao au auto avi avr caf cdda cdr cvs cvsd dat dvms fap ffmpeg flac fssd gsm hcom ima ircam la lpc lpc10 lu m3u m4a mat mat4 mat5 maud mp2 mp3 mp4 mpg nist nul null **ogg** oss ossdsp paf pls prc pvf raw s1 s2 s3 s4 sb sd2 sds sf sl smp snd sndfile sndt sou sph sw txw u1 u2 u3 u4 ub ul uw vms voc **vorbis** vox w64 wav wmv wve xa xi

---

### Post by andrew.46 on 2009-03-29
Hi,

You might be interested in all *possible* formats and effects of the *latest* version:

[http://sox.sourceforge.net/Docs/Features](http://sox.sourceforge.net/Docs/Features)

Andrew

---

### Post by logos34 on 2009-03-29
> **ad_267 said:**
> ```
sudo apt-get install libsox-fmt-ogg
```
or
```
sudo apt-get install libsox-fmt-all
```

I guess ogg vorbis support is NOT default, as I stated earlier (I must have installed in my customary way to include recommended  stuff also).  We are using FOSS OS, folks, so why I is this a "SUGGESTED" PKG (metapackage actually):

> Package: libsox-fmt-all
Priority: optional
Section: universe/sound
Installed-Size: 48
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Pascal Giard <pascal@debian.org>
Architecture: amd64
Source: sox
Version: 14.0.0-5
Depends: libsox-fmt-base, libsox-fmt-ffmpeg, libsox-fmt-flac, libsox-fmt-gsm, libsox-fmt-mp3, **[COLOR="Red"]libsox-fmt-ogg[/COLOR]**, libsox-fmt-sndfile, libsox-fmt-alsa, libsox-fmt-ao, libsox-fmt-oss


> 
Package: sox
Priority: optional
Section: universe/sound
Installed-Size: 184
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Pascal Giard <pascal@debian.org>
Architecture: amd64
Version: 14.0.0-5
Depends: libc6 (>= 2.6.1-1), libltdl3 (>= 1.5.2-2), libsamplerate0, libsox0
Recommends: libsox-fmt-base, libsox-fmt-alsa | libsox-fmt-ao | libsox-fmt-oss
**[COLOR="Red"]Suggests: libsox-fmt-all[/COLOR]**

To get vorbis, flac, etc. support you have to add suggested libsox-fmt-all, which drags in libsox-fmt-ogg, -flac, etc.).

Just about everywhere else in ubuntu (like gstreamer) ogg is included in base setup--it's only mp3 and other proprietary codecs you have to manually enable/fetch (like from Medibuntu).  Doesn't make sense to me.

---

