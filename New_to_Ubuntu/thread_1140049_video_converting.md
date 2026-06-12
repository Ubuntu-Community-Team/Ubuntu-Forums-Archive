---
title: "video converting"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by waldo_phill on 2009-04-27
All right here is what I am looking to do:

I am looking to take dvix/avi videos and convert them so my rock boxed iPod will play them. 

It is my understanding that rock box will read mpeg1/mpeg2 videos with mp3/mp2 encoded sound. Now for some reason I cannot get AVIDEMUX to work (I may be choosing the wrong settings or and just not doing it right). If anyone out there has done this or can guide me on how to get this working it would be greatly appreciated.

---

### Post by dLeon on 2009-04-27
I'm not using iPod so this suggestion might not work. Try to use Mencoder/Mplayer. It's command line tool though, but really powerful. Doesn't dissapoint me till this time. I make a lot of 'test make' with many container formats and all works.
One thing to notes, mpeg movie produced with Mencoder/Mplayer not really right, a.k.a I still can't figure out to make a proper mpeg movie with it.

---

### Post by waldo_phill on 2009-04-27
The manual for Mencoder states it encodes to mpeg-4 is there a way to do mpeg2/mpeg1?

---

### Post by andrew.46 on 2009-04-27
Hi waldo_phill,

> **waldo_phill said:**
> I am looking to take dvix/avi videos and convert them so my rock boxed iPod will play them. 

It is my understanding that rock box will read mpeg1/mpeg2 videos with mp3/mp2 encoded sound.

It believe iPods are a lot more capable than this and can actually play h264 video and aac sound natively. Is your device an actual iPod or perhaps a *similar* device with less capability?

All the best,

Andrew

---

### Post by t0p on 2009-04-27
**ffmpeg** is a pretty cool program for doing stuff to media files.  It's a command line tool, so if a lack of gui brings you out in a cold sweat it may not be the tool for you.  But I reckon it's worth learning.  Like most command-line tools, it's pretty powerful once you know what you're doing.  Check it out.

---

### Post by waldo_phill on 2009-04-28
> **andrew.46 said:**
> Hi waldo_phill,



It believe iPods are a lot more capable than this and can actually play h264 video and aac sound natively. Is your device an actual iPod or perhaps a *similar* device with less capability?

All the best,

Andrew

I've placed Rock box over the Ipod so it can play flac files and do a few other things. The downside is the video capability is more limited.

> **t0p said:**
> **ffmpeg** is a pretty cool program for doing stuff to media files.  It's a command line tool, so if a lack of gui brings you out in a cold sweat it may not be the tool for you.  But I reckon it's worth learning.  Like most command-line tools, it's pretty powerful once you know what you're doing.  Check it out.

Thank I'll see what FFMPEG can do.

---

### Post by _sAm_ on 2009-04-28
Hanbrake for sure. 
Homepage: [http://handbrake.fr/](http://handbrake.fr/)
Guide: [http://spareclockcycles.wordpress.com/2008/12/11/handbrake-for-dvd-ripping-on-ubuntu/](http://spareclockcycles.wordpress.com/2008/12/11/handbrake-for-dvd-ripping-on-ubuntu/)

---

### Post by NightwishFan on 2009-04-28
I second FFMPEG. I used it to convert a video dvd .vob file from mpeg2/5.1 ac3 to - no video and stereo 44.1 16-bit pcm, so I could seperate the songs (it was a band dvd) into individual .flac tracks using audacity.

Remember to use the unstripped codecs, etc, when using Ubuntu. I am not sure if you would have to use medibuntu to get them or not.

---

### Post by FakeOutdoorsman on 2009-04-28
> **NightwishFan said:**
> Remember to use the unstripped codecs, etc, when using Ubuntu. I am not sure if you would have to use medibuntu to get them or not.

Only Hardy Heron and earlier can benefit from Medibuntu because there are no FFmpeg binaries in that repository for later Ubuntu versions.  More info in the unstripped libraries and Medibuntu:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

As for Rockbox, it seems to only support MPEG-1 and MPEG-2 and they give a FFmpeg encoding example at [Rockbox MPEG Player](http://www.rockbox.org/twiki/bin/view/Main/PluginMpegplayer).

---

### Post by Cresho on 2009-04-28
install medibuntu and use winff.  not a problem.  when ffmpeg gets changed, it wont work, you need a working ffmpeg.

winff has tons of codes available for converting.

---

### Post by NightwishFan on 2009-04-29
Winff is harder to use than command line ffmpeg.

---

### Post by andrew.46 on 2009-04-30
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> As for Rockbox, it seems to only support MPEG-1 and MPEG-2 and they give a FFmpeg encoding example at [Rockbox MPEG Player](http://www.rockbox.org/twiki/bin/view/Main/PluginMpegplayer).

And I note an FFmpeg [conversion script]("http://www.rockbox.org/twiki/pub/Main/PluginMpegplayer/mkvid-ffmpeg.sh") on this page that at the very least should furnish a start. Examples as well for MEncoder and vlc. Now if I only had one of those devices .....

Andrew

---

