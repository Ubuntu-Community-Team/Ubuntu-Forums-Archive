---
title: "how to copy  my dvds to hard drive"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by mystmaiden on 2010-10-04
I learned the hard way with my first copy of Avatar that making a backup is pretty important. Now I have a set of dvds that are in korean, so I'll need the subtitles as well. I downloaded dvd ripper but I think its way over my head. Is there a simpler way to copy these?

---

### Post by andrewthomas on 2010-10-04
[B]Comprehensive Multimedia & Video Howto

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[/B]

---

### Post by foxmulder881 on 2010-10-04
I just use k9copy.

---

### Post by oldos2er on 2010-10-04
Right-click on the disc, Copy Disc.

---

### Post by HermanAB on 2010-10-05
Acidrip is also simple.  Otherwise try handbrake.

---

### Post by k3lt01 on 2010-10-05
This list is what is available in Ubuntu Software Centre
Dvd::Rip
K3B
AcidRip
Brasero
GnomeBaker
K9Copy
Dvd95
DVD Encoder OGMRip
Thoggen DVD Ripper
DVD Movie Backup

---

### Post by Dustin2128 on 2010-10-05
> **HermanAB said:**
> Acidrip is also simple.  Otherwise try handbrake.
+1 to acidrip. Just make sure you go more than 2 passes for maximum video quality during action scenes. Ripped avatar the other day with it actually..

---

### Post by foxmulder881 on 2010-10-05
I ripped Avatar with vobcopy. Awesome uncompressed rip! :popcorn:

---

### Post by andrew.46 on 2010-10-05
Hi fox,

> **foxmulder881 said:**
> I ripped Avatar with vobcopy. Awesome uncompressed rip! :popcorn:

Indeed, the command:

```
vobcopy -m
```

will* mirror* the entire contents of your dvd to your hard drive. Transcoding or not becomes the next question :).

Andrew

---

### Post by mystmaiden on 2010-10-06
Thanks for the replies everyone. so far I did try dvd::rip    but it hangs up and doesn't complete the process so I'll have to try again - pretty safe to assume its operator error.

I've never used vob before but I may try it, though I don't really know anything about transcoding it after - yet anyway

---

### Post by mc4man on 2010-10-06
> getting libdvdcss2

If you have libdvdread4 installed (probably do) then run this in a terminal
```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

If not, or not sure then 
```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```

edit:
what is your intended purpose for the dvd rips (back up, backup to disk, or just for playback from a hdd. If just the later is space an issue

---

### Post by Paqman on 2010-10-06
> **foxmulder881 said:**
> I ripped Avatar with vobcopy. Awesome uncompressed rip! :popcorn:

vobcopy is cool. Another option is to create an ISO, which I find a bit tidier.

---

### Post by mystmaiden on 2010-10-12
I'm just now getting back to this project. 

mc4man - Thank you for the reply.  Right now I don't have a dvd burner so for now at least, I'm just wanting to make a backup in case something happens to my dvds, at least I can watch them on my computer. I would like to be able to burn them to dvd later. I have a 1 tb external to tuck them away in.  I checked and now have all the required dependencies, but when I try to use dvd::rip it rips the dvd but doesn't quite finish. The status bar gets just almost to the end and everything seems to stop. I have done a few searches and have yet to come up with either cause or solution.

edited to add: I just tried vobcopy and for this set of dvds at least, its definitely not the answer. Each dvd has 3 one hour tv shows on it. It did copy, but the subtitles only came out part of the time and even at that they are completely unreadable. So I took a peek at an acidrip howto.. 9 hours to copy a dvd - does that sound right?

---

### Post by andrew.46 on 2010-10-12
Hi mystmaiden,

I have just finished writing up a method of ripping and converting DVDs *manually* which may be of interest?

FFmpeg and 'Fist of Fury'
[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

This represents a very different approach to such semi-automated programs such as handbrake but still using similar tools, and of course it does not involve making an *exact copy* of the DVD.

Andrew

---

### Post by mystmaiden on 2010-10-13
Thanks, Andrew, I'll definitely check it out. 

I did figure out that the difficulty with the vobcopy was the way I was trying to watch it. I had opened the individual vid files inside it instead of just opening the whole file with movie player. It plays fine. I successfully made a copy with acidrip but you can see pixels in places here and there, not sure what causes that.

---

### Post by baddnady23 on 2010-10-13
To simply make an exact replica, I just right click on the dvd and select copy to disc and select the option to make an .iso.  That way if I ever did lose or break the dvd, I can make myself a new one and it will be exactly the same as the origional.

---

### Post by mystmaiden on 2010-10-13
In my attempt to get a good copy of the dvd I decided to try again. Using the instructions here [http://ubuntuforums.org/showthread.php?t=456035](http://ubuntuforums.org/showthread.php?t=456035) (glennph93's post) and a vobcopy I'd made of the dvd. Unfortunately, it stops immediately saying its complete or that mencoder was interupted by the user. Here is the acidrip log
```
AcidRip message - DVD read ok
AcidRip message - video_codec has been set to x264
AcidRip message - x264 - H.264 encoding
AcidRip message - crop_enable has been set to 0
AcidRip message - selected_audio changed to 1 - Channels 2 frequency 48000 quant. drc
AcidRip message - Selected_subp changed to -1
AcidRip message - Selected_subp changed to 1
AcidRip message - Pushed events onto queue
AcidRip message - Playlist contains 2 item(s)
AcidRip message - Running unlink frameno.avi 2> /dev/null
AcidRip message - Removing frameno.avi if it exists
AcidRip message - Running mencoder dvd://1 -dvd-device /home/mystmaiden/YB_DISC1  -aid 128 -sid 0  -info srcform="DVD ripped by acidrip.sf.net" -oac lavc -lavcopts acodec=mp3:abitrate=128  -ovc x264 -vf pp=de,scale=480:-2    -o "/home/mystmaiden/unknown.avi"
AcidRip message - Encoding film
MEncoder SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Couldn't find device name.
There are 1 titles on this DVD.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: ko aid: 128.
number of audio channels on disk: 1.
subtitle ( sid ): 1 language: en
number of subtitles on disk: 1
success: format: 2  data: 0x0 - 0xbb0e0800
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.970  ftime:=0.0334
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [scale w=480 h=-2]
Opening video filter: [pp=de]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
[PP] Using external postprocessing filter, max q = 6.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
Audio LAVC, couldn't find encoder for codec mp3.

Exiting...
AcidRip message - Playlist completed
AcidRip message - Mencoder interrupted by user
```

Not sure why the encoder for the mp3 would suddenly be missing...

---

