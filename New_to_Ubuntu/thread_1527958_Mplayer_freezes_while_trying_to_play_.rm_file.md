---
title: "Mplayer freezes while trying to play .rm file"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by Mongoose088 on 2010-07-10
Hello all,

I'm facing a strange issue with video playback in Ubuntu 10.04, but certain .rm files make mplayer freeze. Here is the info I've gathered about the offending .rm files:

While trying to open the file from command line with gnome-mplayer, I get the following errors:
```

tom@tom-1320:~/Desktop$ gnome-mplayer 00101_all.rm 
GNOME MPlayer v0.9.9.2
vo = (null) ao = (null)
Running with GIO support
Master Playback is 1
Master Range is 0 to 65536 
Master Current Volume 34080, multiplier = 0.001526
Scaled Volume is 52.001953
Using volume of 52.00
opening 00101_all.rm
is block 0
is character 0
is reg 1
is dir 0
playlist 0
embedded in window id 0x0
opening playlist
playlist detection = 0
adding file:///home/tom/Desktop/00101_all.rm to playlist (cancel = 0)
getting file metadata for /home/tom/Desktop/00101_all.rm
Using match: type='signal',interface='com.gnome.mplayer'
Using match: type='signal',interface='org.gnome.SettingsDaemon'
Using match: type='signal',interface='org.gnome.SettingsDaemon.MediaKeys'
Proxy connections and Command connected
playing - file:///home/tom/Desktop/00101_all.rm
is playlist 0
media size = 0 x 0
current size = 0 x 0 
Changing window size to 320 x 240 visible = 1
media size = 320 x 240
mplayer -quiet -slave -identify -volume 52 -mixer-channel Master -framedrop -noconsolecontrols -noidle -osdlevel 0 -nomouseinput -cache 2000 -wid 0x500005b -ss 0 -*** -noembeddedfonts -***-font-scale 1.00 -***-color ffffff00 -channels 2 -vf-add screenshot -dvd-device /dev/dvd -af-add export=/tmp/mplayer-af_exportagpldi:512 /home/tom/Desktop/00101_all.rm 
current size = 372 x 1 
Changing window size to 320 x 240 visible = 1
Spawn succeeded for filename /home/tom/Desktop/00101_all.rm
media size = 320 x 240
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
ERROR: mplayer: could not connect to socket

ERROR: mplayer: No such file or directory
Playing /home/tom/Desktop/00101_all.rm.
ERROR: Failed to open LIRC support. You will not be able to use your remote control.
Cache fill:  0.00% (0 bytes)   
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
ID_AUDIO_ID=0
[real] Audio stream found, -aid 0
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
ID_VIDEO_ID=1
[real] Video stream found, -vid 1
Stream mimetype: logical-fileinfo
VIDEO:  [RV30]  320x240  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
ERROR: open: No such file or directory
 name: 00101
ERROR: [MGA] Couldn't open: /dev/mga_vid
ID_CLIP_INFO_NAME0=name
ERROR: open: No such file or directory
ID_CLIP_INFO_VALUE0=00101
ERROR: [MGA] Couldn't open: /dev/mga_vid
 author: 00
ERROR: [VO_TDFXFB] Can't open /dev/fb0: Permission denied.
ID_CLIP_INFO_NAME1=author
ERROR: [VO_3DFX] Unable to open /dev/3dfx.
ID_CLIP_INFO_VALUE1=00
 copyright: &#65533; 00 & 00
ID_CLIP_INFO_NAME2=copyright
ID_CLIP_INFO_VALUE2=&#65533; 00 & 00
ID_CLIP_INFO_N=3
ID_FILENAME=/home/tom/Desktop/00101_all.rm
ID_DEMUXER=real
ID_VIDEO_FORMAT=RV30
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=320
ID_VIDEO_HEIGHT=240
ID_VIDEO_FPS=15.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=sipr
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=16000
ID_AUDIO_NCH=1
ID_LENGTH=2690.00
ID_SEEKABLE=1
ID_CHAPTERS=0
[***] auto-open
Opening video filter: [screenshot]
[***] Init
[***] Updating font cache.
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
ERROR: Error loading dll
ERROR: ERROR: Could not open required DirectShow codec drvc.dll.
Win32 LoadLibrary failed to load: drvc.dll, /usr/lib/codecs/drvc.dll, /usr/lib/win32/drvc.dll, /usr/local/lib/win32/drvc.dll
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
ERROR: Error loading dll
ERROR: ERROR: Could not open required DirectShow codec drv33260.dll.
Win32 LoadLibrary failed to load: drv33260.dll, /usr/lib/codecs/drv33260.dll, /usr/lib/win32/drv33260.dll, /usr/local/lib/win32/drv33260.dll
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
ERROR: Error: /usr/lib/codecs/drvc.bundle/Contents/MacOS/drvc: cannot open shared object file: No such file or directory
ERROR: Error loading dll
ERROR: ERROR: Could not open required DirectShow codec drvc.bundle/Contents/MacOS/drvc.
Win32 LoadLibrary failed to load: drvc.bundle/Contents/MacOS/drvc, /usr/lib/codecs/drvc.bundle/Contents/MacOS/drvc, /usr/lib/win32/drvc.bundle/Contents/MacOS/drvc, /usr/local/lib/win32/drvc.bundle/Contents/MacOS/drvc
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
ERROR: Error: /usr/lib/codecs/drvc.so: cannot open shared object file: No such file or directory
ERROR: Error loading dll
ERROR: ERROR: Could not open required DirectShow codec drvc.so.
Win32 LoadLibrary failed to load: drvc.so, /usr/lib/codecs/drvc.so, /usr/lib/win32/drvc.so, /usr/local/lib/win32/drvc.so
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Selected video codec: [rv30] vfm: realvid (Linux RealPlayer 8 RV30)
==========================================================================
ID_VIDEO_CODEC=rv30
==========================================================================
Opening audio decoder: [realaud] RealAudio decoder
AUDIO: 16000 Hz, 1 ch, s16le, 16.0 kbit/6.25% (ratio: 2000->32000)
ID_AUDIO_BITRATE=16000
ID_AUDIO_RATE=16000
ID_AUDIO_NCH=1
Selected audio codec: [rasipr] afm: realaud (RealAudio Sipro)
==========================================================================
[export] Exporting to file: /tmp/mplayer-af_exportagpldi
[export] Memory mapped to file: /tmp/mplayer-af_exportagpldi (0xb7313000)
[export] Exporting to file: /tmp/mplayer-af_exportagpldi
[export] Memory mapped to file: /tmp/mplayer-af_exportagpldi (0xb7313000)
AO: [pulse] 16000Hz 1ch s16le (2 bytes per sample)
[export] Exporting to file: /tmp/mplayer-af_exportagpldi
[export] Memory mapped to file: /tmp/mplayer-af_exportagpldi (0xb7313000)
[export] Exporting to file: /tmp/mplayer-af_exportagpldi
[export] Memory mapped to file: /tmp/mplayer-af_exportagpldi (0xb7313000)
ID_AUDIO_CODEC=rasipr
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar I420)
VDec: using Planar I420 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.3333
ERROR: [swscaler @ 0xa44e8f0]No accelerated colorspace conversion found.
ERROR: [swscaler @ 0xa44e8f0]using unscaled yuv420p -> rgb24 special converter
VO: [xv] 320x240 => 320x240 Planar I420 
Resizing to 320 x 240
current size = 320 x 243 
old aspect is 1.316872 new aspect is 1.333333
ANS_switch_audio is invalid -1
ANS_switch_audio is invalid -1
ERROR: Failed to get value of property 'sub_demux'.

```

Then, mplayer just hangs, not showing any picture or sounds.
However, if I open it in VLC, I get video only, but no sound. I would really like both!

I need to find a way to play these files properly. If at all possible, I would like to avoid installing realplayer.


I don't know anything about video playback, so if you want some specific command outputs, please let me know. I will download any codecs, free or nonfree as necessary.

Thanks!

---

### Post by Zzl1xndd on 2010-07-10
I can't say for sure what the issue is. However I have noticed similar issues myself. In almost all causes the Audio format is Listed as sipr (Ones listed as Cook seem to work fine).

The only fix I have found is using Realplayer.

[http://www.real.com/realplayer/linux](http://www.real.com/realplayer/linux)

---

### Post by notmyidea on 2010-09-21
That drvc.so, realtime video codec, isn't installed anywhere.  I am running ubuntu 10.04, have the medibuntu repository, w32codecs installed, and for some reason, this isn't installed.  Have been looking around for a solution, but haven't found one yet.

---

### Post by andrew.46 on 2010-09-21
Hi notmyidea,

> **notmyidea said:**
> That drvc.so, realtime video codec, isn't installed anywhere.  I am running ubuntu 10.04, have the medibuntu repository, w32codecs installed, and for some reason, this isn't installed.  Have been looking around for a solution, but haven't found one yet.

This codec was excluded from the package by the Debian packagers. The [changelog]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20100303-0.0medibuntu1.changelog") has the details:

```

w32codecs (1:20071007-0.2) unstable; urgency=low

  * Because libstdc++5 has been removed in unstable, remove two codecs
    (drvc.so and cook.so) who depends on that package.

 -- Christian Marillat <marillat@debian.org>  Tue, 25 Aug 2009 23:09:45 +0200

```

I am not on Ubuntu at the moment to check if the new package from Medibuntu quietly slipped it back in but the following command should tell you:

```
sudo find /usr/lib/codecs -name drvc.so
```

Andrew

---

### Post by notmyidea on 2010-09-24
> **andrew.46 said:**
> Hi notmyidea,

This codec was excluded from the package by the Debian packagers. The [changelog]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20100303-0.0medibuntu1.changelog") has the details:

```

w32codecs (1:20071007-0.2) unstable; urgency=low

  * Because libstdc++5 has been removed in unstable, remove two codecs
    (drvc.so and cook.so) who depends on that package.

 -- Christian Marillat <marillat@debian.org>  Tue, 25 Aug 2009 23:09:45 +0200

```

Thanks for pointing this out.

```
sudo find /usr/lib/codecs -name drvc.so
```[/QUOTE]

Nope. Not there.  So much for using mplayer for .rm files =/

---

### Post by andrew.46 on 2010-09-24
Hi notmyidea,

> **notmyidea said:**
>  So much for using mplayer for .rm files =/

It is not quite that bad :). Have a look at this file:

```
wget 'http://samples.mplayerhq.hu/real/01 - Dbz Movie - Worlds Strongest.rm'
```

and you will see that MPlayer has native playback for this file:

```

andrew@skamandros~/Desktop$ mplayer '01 - Dbz Movie - Worlds Strongest.rm'
MPlayer SVN-r32342-4.3.3 (C) 2000-2010 MPlayer Team

Playing 01 - Dbz Movie - Worlds Strongest.rm.
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
**[COLOR="Red"][real] Audio stream found, -aid 0[/COLOR]**
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
**[COLOR="Red"][real] Video stream found, -vid 1[/COLOR]**
VIDEO:  [RV20]  352x240  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 title: Dbz Worlds Strongest Part1
 author: Snipe
 copyright: &#65533;1998 Snipe Productions
==========================================================================
**[COLOR="Red"]Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family[/COLOR]**
Selected video codec: [ffrv20] vfm: ffmpeg (FFmpeg RV20)
==========================================================================
==========================================================================
**[COLOR="Red"]Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders[/COLOR]**
AUDIO: 44100 Hz, 1 ch, s16le, 32.1 kbit/4.56% (ratio: 4018->88200)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio)
==========================================================================
AO: [oss] 44100Hz 1ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 352x240 => 352x240 Planar YV12 
A:  12.9 V:  12.9 A-V:  0.000 ct:  0.013 194/194  1%  0%  0.4% 0 0 

```

I am not sure though how many different types of real media files are covered by native playback...

Andrew

---

### Post by notmyidea on 2010-10-02
> **andrew.46 said:**
> 
I am not sure though how many different types of real media files are covered by native playback...

Andrew


Noticed the video is RV20.  I have some .rm files that RV20 and play fine.  The ones that don't are RV30.  Thanks for looking into this though :P

---

### Post by mc4man on 2010-10-02
Whether or not it helps don't know - don't have any samples atm for drvc.so

Anyway you are free to install libstdc++5 and add drvc.so to /usr/lib/codecs folder

For libstdc++5 go here, take your pick (notice it's been returned in maverick ), any will install in karmic or lucid
[http://packages.ubuntu.com/search?searchon=names&keywords=libstdc%2B%2B5](http://packages.ubuntu.com/search?searchon=names&keywords=libstdc%2B%2B5)

To add drvc.so go here, download the w32codec package and then extract to folder with archive manager. Browse to /usr/lib/codecs, copy drvc.so and place in your /usr/lib/codec folder.

[http://packages.medibuntu.org/hardy/w32codecs.html](http://packages.medibuntu.org/hardy/w32codecs.html)

...............

It's possible mplayer won't use - gstreamer does thru the pitfdll plugin, (in general the pitfdll plugin is  broken, can interfere with wmas decoding in gstreamer.

If you have a link to sample problem file that could be useful

---

### Post by notmyidea on 2010-10-02
That did it!  Thank you very much mc4man.  Much appreciated. \\:D/

---

### Post by andrew.46 on 2010-10-02
I see that mc4man has save the day again :). Sample RV30 files are available on the same site, this one I had a look at:

```
wget 'http://samples.mplayerhq.hu/real/VC-RV30/paula_abdul-crazy_cool.rm'
```

Looks like MPlayer can play RV30 files okay using *-vc ffrv30*, have you tried this? I attach a screenshot showing this in action...

Andrew

---

### Post by spurs21 on 2010-10-14
Thank you mc4man. I have a great series of lectures from CalBerkeley that are in .rm format and wouldn't play correctly under Lucid until I followed your hint. Frustrated the hell out of me since they were great in karmic, jaunty, and intrepid. Thanks again!

> **mc4man said:**
> 

To add drvc.so go here, download the w32codec package and then extract to folder with archive manager. Browse to /usr/lib/codecs, copy drvc.so and place in your /usr/lib/codec folder.

[http://packages.medibuntu.org/hardy/w32codecs.html](http://packages.medibuntu.org/hardy/w32codecs.html)


---

