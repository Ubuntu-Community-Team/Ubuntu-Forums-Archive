---
title: "Adjust Bit Rates as Can Be Done in iTunes"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by lhb1142 on 2009-01-15
When I used Windows, I used iTunes to extract CDs. Within iTunes there were many options to adjust the bit rates in the individual formats chosen.

For example, I could choose mp3 @ 128 kbps stereo - but, if I were extracting an audio book, I could adjust this to 64 kbps mono and obtain the same sound quality in half the space.

This can be done with any of the formats iTunes supports.

Currently, I am using Ubuntu Linux and, when extracting a CD, I use Audio CD Extractor (Sound Juicer). This program offers several choices of formats, but no option to change the bit rates within a given format, at least that I can find.

Does anyone know of a program that works similarly to Audio CD Extractor (Sound Juicer) but, like iTunes, offers the ability to adjust the bit rates within a chosen format?

---

### Post by logos34 on 2009-01-15
> **lhb1142 said:**
> I use Audio CD Extractor (Sound Juicer). This program offers several choices of formats, but no option to change the bit rates within a given format, at least that I can find.

Edit>Preferences>Format output>Edit>gstreamer pipeline

[https://help.ubuntu.com/community/CDRipping#MP3%20Encoding](https://help.ubuntu.com/community/CDRipping#MP3%20Encoding)

add: 

for mono (64k cbr) try:

'> audio/x-raw-int,rate=44100,channels=2  !  lame name=enc mode=3 vbr=0 bitrate=64 ! xingmux ! id3v2mux

for stereo:

> audio/x-raw-int,rate=44100,channels=2  !  lame name=enc mode=4 vbr=4 vbr-quality=5 ! xingmux ! id3v2mux

'mode=4' --> 'auto' (or set it manually to mode=1 for joint-stereo)

'vbr=4' --> 'new'

'vbr-quality=5' --> ~128kbps 

(note:  i just noticed the id tags aren't coming out right--you'll have to adjust that)

info on lame gst options, run this in terminal:
[B]
gst-inspect-0.10 lame [/B]

make sure you have gstreamer0.10-plugins-ugly and ubuntu-restricted-extras installed.  might as well get these too:

sudo apt-get install gstreamer0.10-ffmpeg, gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse liblame0

---

### Post by lhb1142 on 2009-01-16
Thanks. That solves the problem.

---

### Post by logos34 on 2009-01-16
tell me, though, is nautilus>file properties>audio tab reading the tags ok?  Because I haven't been able to solve this.  I never use sound-juicer to rip, but now that I've been fiddling with it I cannot seem to come up with a pipeline command to get the id3 correct.  (When I start problem solving sth, I'm like a pitbull until I hit on the solution).

One problem seems to be id3v2mux tags using the id3 2.4 version, whereas gnome apps and desktop seems to only recognize 2.3 version.

hmm...

---

