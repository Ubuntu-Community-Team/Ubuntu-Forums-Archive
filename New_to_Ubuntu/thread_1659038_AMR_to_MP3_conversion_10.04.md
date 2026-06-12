---
title: "AMR to MP3 conversion 10.04"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by swaprava on 2011-01-03
I have tried all possible ways of converting amr (recorded on my mobile phone) to mp3 so that I can upload in myspace, with no luck. I was following this [post]("http://ubuntuforums.org/showthread.php?t=448627"), but both ffmpeg seems to be broken for ubuntu 10.04 and the other product by miksoft doesn't have the amr -> mp3 conversion option. Problem is myspace doesn't accept any format other than mp3, and I have only amr files. Did anybody face a similar problem? Please advise if you have found any way of doing the same.

---

### Post by Verbeck on 2011-01-03
try to do it from *soundconverter* (from software center/synaptic)

---

### Post by mc4man on 2011-01-03
If you add medibuntu as a source and then update your ffmpeg lib to it's 'extra' versions you'll get amr decoding/mp3 encoding thru ffmpeg 
(libavcodec-extra-52, libavformat-extra-52. ect.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by khelben1979 on 2011-01-05
I think the easiest way is if you convert it to WAV first, then use [Audacity]("http://audacity.sourceforge.net/") to convert that to the mp3 file format. Audacity will need LAME or similiar to do it and you got installation instructions [here]("http://wiki.audacityteam.org/wiki/Lame_Installation").

I've gotten information that Audacity can handle the AMR file format, but cannot really confirm if it works.

---

