---
title: "Sound but no video"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by doug piston on 2010-12-29
I am semi-new to Ubuntu. We will just say I know enough to be dangerous. I have spent months trying to get the video to play but have come to the end of my rope and come here for help.

No video output from running either the terminal or Applications>Sound and Video

I get this from terminal
```

jarvis@jarvis:~/Downloads$ mplayer vids.mpg
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vids.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  640x352  (aspect 1)  23.976 fps  1600.0 kbps (200.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 640 x 352 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmpeg1] vfm: ffmpeg (FFmpeg MPEG-1)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 96.0 kbit/6.25% (ratio: 12000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.82:1 - prescaling to correct movie aspect.
VO: [xv] 640x352 => 640x352 Planar YV12 
A:   3.1 V:   3.1 A-V: -0.002 ct: -0.087  65/ 65  4%  0%  0.3% 0 0 
Exiting... (Quit)
```

Any ideas and thanks for looking. Have a good New Year):P

---

### Post by SuaSwe on 2010-12-30
Having had a look round this looks to be a driver issue. You could try looking for proprietary drivers under System > Administration > Hardware Drivers, though this doesn't seem to help those I've read about!

Also, this seems to work for some:

```

mplayer -vo gl vids.mpeg

```

... though for the life of me I can't find any info on what this does exactly! It does look to be related to output driver use though.

---

### Post by doug piston on 2010-12-30
> **SuaSwe said:**
> Having had a look round this looks to be a driver issue. You could try looking for proprietary drivers under System > Administration > Hardware Drivers, though this doesn't seem to help those I've read about!

Also, this seems to work for some:

```

mplayer -vo gl vids.mpeg

```... though for the life of me I can't find any info on what this does exactly! It does look to be related to output driver use though.


I tried your suggestion, it didn't work but seems to have given more info on the error.

```

jarvis@jarvis:~/Downloads$ mplayer -vo gl vids.mpg
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vids.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  640x352  (aspect 1)  23.976 fps  1600.0 kbps (200.0 kbyte/s)
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 640 x 352 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmpeg1] vfm: ffmpeg (FFmpeg MPEG-1)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 96.0 kbit/6.25% (ratio: 12000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 352 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.82:1 - prescaling to correct movie aspect.
[swscaler @ 0xb5f1e900]using unscaled yuv420p -> rgb32 special converter
VO: [gl] 640x352 => 640x352 BGRA 


MPlayer interrupted by signal 11 in module: decode_video
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]
```

---

### Post by SuaSwe on 2010-12-31
Anyone else have any suggestions? I take it the "-vo gl" forces mplayer to look for a certain output driver, though I'm not sure how to check which one you'd want to use. 

Have you tried finding and reinstalling the drivers for your video card? "lspci" in Terminal should list it, and from there Google and the forums can be of help for instructions. :)

Has this ever worked, by the way?

---

### Post by doug piston on 2010-12-31
Nope. Has never worked. But I will take your suggestion and go with it. Thanks for the help.

---

### Post by qyot27 on 2010-12-31
Have you installed ubuntu-restricted-extras?  I don't know if the repo version of mplayer is affected by lack of that package or not.  Since mplayer's decoders are provided by libavcodec, I'm not entirely sure it wouldn't be affected (rather, I'm not sure if the repo version uses shared or static libraries - if shared, then you probably need to install the restricted extras; if static, there's something else wrong happening).



In any case, check that the file is correct.  Download the packages for mediainfo (CLI), libmediainfo0, and libzen0 from MediaInfo's Sourceforge page ([http://mediainfo.sourceforge.net/en/Download/Ubuntu](http://mediainfo.sourceforge.net/en/Download/Ubuntu)), and install them as usual*.

*double-clicking should bring up Software Center's install process (for 10.10; you didn't mention which version you're using).  If you have gdebi you could use that, or if you'd rather install through the Terminal then that's *dpkg -i packagename.deb*

Once those are installed, run the following command:
*mediainfo -f vids.mpg*

This should tell you more information about the file itself.  Some of the error messages from the -vo gl attempt make me wonder if the file is misnamed or somehow damaged.

---

### Post by doug piston on 2010-12-31
> **qyot27 said:**
> Have you installed ubuntu-restricted-extras?  I don't know if the repo version of mplayer is affected by lack of that package or not.  Since mplayer's decoders are provided by libavcodec, I'm not entirely sure it wouldn't be affected (rather, I'm not sure if the repo version uses shared or static libraries - if shared, then you probably need to install the restricted extras; if static, there's something else wrong happening).



In any case, check that the file is correct.  Download the packages for mediainfo (CLI), libmediainfo0, and libzen0 from MediaInfo's Sourceforge page ([http://mediainfo.sourceforge.net/en/Download/Ubuntu](http://mediainfo.sourceforge.net/en/Download/Ubuntu)), and install them as usual*.

*double-clicking should bring up Software Center's install process (for 10.10; you didn't mention which version you're using).  If you have gdebi you could use that, or if you'd rather install through the Terminal then that's *dpkg -i packagename.deb*

Once those are installed, run the following command:
*mediainfo -f vids.mpg*

This should tell you more information about the file itself.  Some of the error messages from the -vo gl attempt make me wonder if the file is misnamed or somehow damaged.


The "ubuntu-restricted-extras" are already installed and apologize for not mentioning it but I am on 10.04.  

I installed the CIL, libmediainfo0, and libzen0 and still have the same results. There is no video but sound on files I try to play not just this one. (Maybe I misread but I think you were getting at a possible issue with this certain video) Regardless thank you for the input

---

### Post by doug piston on 2010-12-31
> **doug piston said:**
> The "ubuntu-restricted-extras" are already installed and apologize for not mentioning it but I am on 10.04.  

I installed the CIL, libmediainfo0, and libzen0 and still have the same results. There is no video but sound on files I try to play not just this one. (Maybe I misread but I think you were getting at a possible issue with this certain video) Regardless thank you for the input


Actually I take that back. A simple restart(oops) with your tip seems to have done the trick. Thank you very much to both of you for the help.

Edit: Stop working again. Ugh.

Edit#2: Ok, so after restarting the PC i can play all videos from terminal. Yay! Once I try and double click on one to play in mplayer it goes back to the black screen and running from terminal no longer works. At least this is progress.

---

### Post by qyot27 on 2010-12-31
mediainfo's output lists information about the media file.  If something is wrong with the file, then the readout can help to troubleshoot it.

Anyway, it does actually sound like a driver issue now.  From what was described, it seems like the configuration used for the instance of mplayer(?) that comes up when double-clicking a file is overriding the driver being used by the system, which is why the Terminal ceases to work after attempting to launch the video with a double-click.





After checking the mplayer documentation, MGA seems to be the video driver for Matrox framebuffering.

> mga_vid is a combination of a video output driver and a Linux kernel module that utilizes the Matrox G200/G400/G450/G550 video scaler/overlay unit to perform YUV->RGB colorspace conversion and arbitrary video scaling. mga_vid has hardware VSYNC support with triple buffering. It works on both a framebuffer console and under X, but only with Linux 2.4.x.

For a Linux 2.6.x version of this driver check out [http://attila.kinali.ch/mga/](http://attila.kinali.ch/mga/) or have a look at the external Subversion repository of mga_vid which can be checked out via ...
I fear that what could be happening is that the system detects the hardware, attempts to use it when invoking mplayer through the GUI, but fails (or succeeds, but the driver doesn't do what is required correctly), and this causes further attempts to fail.  In such a case you might have to recompile mplayer to get it working right.

In the Hardware Drivers installation dialog, do you see an entry for Matrox video hardware?  Scoping out packages.ubuntu.com, you might be able to get the right stuff installed by doing:
*sudo apt-get install mga-vid-common xserver-xorg-video-mga*

If those packages aren't already installed, anyway.

---

### Post by doug piston on 2011-01-01
So to update, I un-installed Mplayer and then reinstalled. Though this time the GUI still does not work but I found that I could right click the video and it gives the option to "open with". I select custom command typed in mplayer and now can click on a video and watch it. Might not be the correct fix but for now it works. :) Thank you again for your time and insight.

---

