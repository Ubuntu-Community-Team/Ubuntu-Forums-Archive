---
title: "VLC doesnt play video since Karmic Upgrade"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by 11010110 on 2009-10-31
Hi all,

I just upgraded to Karmic this morning and now every time I try to play any sort of video in VLC none of them work (all of them worked prior to the upgrade). I always receive the same error (or small variations of):

No suitable decoder module:
VLC does not support the audio or video format "XVID". Unfortunately there is no way for you to fix this.

Any ideas are welcome. Thanks to all in advance.

---

### Post by LewRockwell on 2009-10-31
you aren't alone

here at the tech bench we are going to recommend that BEFORE anyone moves to 9.10 they should proceed very cautiously

Download and slow-burn the LiveCD/LiveUSB and see what does and doesn't work
(if you experience any difficulties the first thing to do after it boots up is to turn off compiz)

Once you're satisfied enough with it that you think you'd like to run it "natively"(from your hard drive)...INSTALL IT TO A SEPARATE PARTITION!

do not crash your current running version of ubuntu by "upgrading" to 9.10

again, we cannot recommend this cautious approach/experimentation/procedure ENOUGH!

and...goes without saying...you've done very recent back-ups/clones...

right?

right!

as always, your mileage may vary, buyer beware, and buyer be aware!

let the fun continue...

{{sigh}}

we now return you to your regularily scheduled programming

.

---

### Post by gintor on 2009-10-31
Hi, Ubunto virgin here.  I installed 9.10 last night 2 mins after installing the last version from a live CD.  If i try to run a video on VLC i get all kinds of flicker and stuff.  I am currently running a Dell XPS M1330 with a P9033 CPU and a Nvidia 8400GS GPU.  I have 4 gig of RAM.  I am hopeing to move permantly to Ubunto but bad video is a major off put.  Is it that this version is so new and should i try an older version ?.  Please help as i am keen to try a move over to Linux, but i am getting frustrated with bad video.  Oh and to add i did use the device driver option to install the so called latest Nvidia drivers after it scanned my hardware, no change to video. So at present i am back to Windows

---

### Post by 11010110 on 2009-10-31
I have tried a restart as well as a complete removal/reinstall and nothing I have found in any other posts has worked as of yet.

I upgraded from Jaunty thru the GUI so there was no live CD involved and there aint no goin back. There have been a lot of improvements I have found so far in Karmic but this is one MAJOR flaw. Im surprised they let something this huge slip by before launching. 

Hope they fix it soon eh?

---

### Post by mc4man on 2009-10-31
> No suitable decoder module:
VLC does not support the audio or video format "XVID". Unfortunately there is no way for you to fix this.


Don't really get that. Even with the relatively crappy vlc build and stock ffmpeg libs for karmic, vlc should be able to play most formats including xvid.

Maybe run this and try again

```
vlc --reset-config --reset-plugins-cache
```

---

### Post by 11010110 on 2009-10-31
Thanks for the input. I tried:

vlc --reset-config --reset-plugins-cach

and the terminal output:

~$ vlc --reset-config --reset-plugins-cach
VLC media player 1.0.2 Goldeneye
[0x9331680] main interface error: no interface module matched "globalhotkeys,none"
[0x9331680] main interface error: no suitable interface module
[0x923b140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x923b140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

(<unknown>:14090): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

VLC opened and there is still no improvement. This happens on ALL video formats even flash thru VLC. Flash works online in opera and firefox so I have no idea where to go form there.

Thanks again I appreciate the help so far everyone!

---

### Post by wilee-nilee on 2009-10-31
Did you install the restricted extras and the medibuntu pack, not do so. If stuff is still not working purge vlc and remove any vlc files and reinstall it. Also you might consider gxine amd the Mlpayer and smplayer set they all work very well. I have found Totem to play more types of in Karmic then ever before as well. Also when you all say videos are we talking about DVD's or downloaded video I saw one format mentioned but the description should be more comprehensive to get good answers. ;)

---

### Post by 11010110 on 2009-10-31
Hey 

I do have the restricted extras installed (I tried reinstalling them just in case to no avail). I have tried this with every video format I have on my computer and none of them work (I have not tried DVDs and they are all downloaded). It just gives the same error (but with a different filetype depending on the video type). I have tried videoplayer and totem and neither of them work and all give similar errors. 

I think it may be a problem with the new version of VLC. As far as I know Jaunty came with 0.9.9 so I was wondering if there was a way I could revert back to the Jaunty version of VLC. I have the source but I am having a tough time building and configuring it (I am used to .deb). If anyone knows where I could find a .deb of VLC 0.9.9 that would be greatly appreciated. If not could someone run me thru how to compile it?

Thanks again

---

### Post by juil on 2009-10-31
Well, I'm completely new to ubuntu. I installed 9.10 yesterday and installed VLC as well. 
It seems to run fine but when i minimize the VLC window and restore it, it loses the video (black screen) while the audio continues to play.

---

### Post by wilee-nilee on 2009-10-31
You can download vlc from its site. [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by clhsharky on 2009-10-31
HI 

VLC 1.0.2 works for me in Ubuntu 9.10 64-bit with wm avi flash.            I do not have any other media to try.

---

### Post by 11010110 on 2009-11-01
all they have at the videolan site is the current version. I'm trying to get the old jaunty version to see if maybe that will help

---

### Post by ikt on 2009-11-01
> **juil said:**
> Well, I'm completely new to ubuntu. I installed 9.10 yesterday and installed VLC as well. 
It seems to run fine but when i minimize the VLC window and restore it, it loses the video (black screen) while the audio continues to play.

If you run vlc from the terminal, and proceed with what you do to make the loss of video while the audio continues to play, do you get any extra error messages?

---

### Post by 11010110 on 2009-11-01
when I play a video when VLC is open in terminal I get this output:

~$ vlc
VLC media player 1.0.2 Goldeneye
[0x93e6490] main interface error: no interface module matched "globalhotkeys,none"
[0x93e6490] main interface error: no suitable interface module
[0x93e6140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x93e6140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

(<unknown>:2211): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat /home/xxxxxx/Downloads/FileName.flv
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[0x96e2918] access_file access error: cannot open file /home/xxxxxx/Downloads/FileName.flv (No such file or directory)
[0x96e2808] main input error: open of `/home/xxxxxx/Download/FileName.flv' failed: no suitable access module


Now the strange thing is that it says something about trying to play a DVD file yet this is a downloaded .flv file...

---

### Post by ikt on 2009-11-01
> **11010110 said:**
> when I play a video when VLC is open in terminal I get this output:

~$ vlc
VLC media player 1.0.2 Goldeneye
[0x93e6490] main interface error: no interface module matched "globalhotkeys,none"
[0x93e6490] main interface error: no suitable interface module
[0x93e6140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x93e6140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

(<unknown>:2211): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat /home/xxxxxx/Downloads/FileName.flv
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[0x96e2918] access_file access error: cannot open file /home/xxxxxx/Downloads/FileName.flv (No such file or directory)
[0x96e2808] main input error: open of `/home/xxxxxx/Download/FileName.flv' failed: no suitable access module


Now the strange thing is that it says something about trying to play a DVD file yet this is a downloaded .flv file...

and it appears it just can't read the file. (which is obviously not the issue)

Just for future reference for anyone looking at vlc issues,

```
vlc -vvv
```

Gives a lot more information.

---

### Post by enque on 2009-11-01
After upgrade to Karmic VLC crashed every time I tried to play a movie. Doing the following allowed me to play videos again:
```
vlc --reset-config --reset-plugins-cache
```

Now I've fixed almost every issue I got after upgrading. Now I just have to figure out what's wrong with my boot screen resolution, and I'm going to have a fully functioning Karmic Koala installation... yay...... sigh...... it shouldn't be THIS much trouble with a so called 'stable version'.

It appears to me that Karmic was much to prematurely released to the public.

---

### Post by 11010110 on 2009-11-01
Ok, I used vlc -vvv to gather more information. Maybe someone can make heads or tails of all of this. This is when I open vlc with vlc -vvv and open and play one video file (in this case .avi).

```
~$ vlc -vvv
VLC media player 1.0.2 Goldeneye
[0x9696140] main libvlc debug: VLC media player - version 1.0.2 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x9696140] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--disable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1ubuntu2' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=xulrunner-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-x264' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--disable-fluidsynth' '--disable-kate' '--disable-mtp' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x9696140] main libvlc debug: translation test: code is "C"
[0x9696140] main libvlc debug: checking plugin modules
[0x9696140] main libvlc debug: loading plugins cache file /home/eric/.cache/vlc/plugins-04041e.dat
[0x9696140] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x9696140] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libavcodec_plugin.so' (libx264.so.67: cannot open shared object file: No such file or directory)
[0x9696140] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libx264_plugin.so' (libx264.so.67: cannot open shared object file: No such file or directory)
[0x9696140] main libvlc warning: cannot load module `/usr/lib/vlc/demux/libavformat_plugin.so' (libx264.so.67: cannot open shared object file: No such file or directory)
[0x9696140] main libvlc debug: module bank initialized (369 modules)
[0x9696140] main libvlc debug: opening config file (/home/eric/.config/vlc/vlcrc)
[0x9696140] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT FPU 
[0x9696140] main libvlc debug: looking for memcpy module: 3 candidates
[0x9696140] main libvlc debug: using memcpy module "memcpymmxext"
[0x9722820] main input debug: Creating an input for 'Media Library'
[0x9722820] main input debug: Input is a meta file: disabling unneeded options
[0x9722820] main input debug: using timeshift granularity of 50 MBytes
[0x9722820] main input debug: using timeshift path '/tmp'
[0x9722820] main input debug: `file/xspf-open:///home/eric/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/eric/.local/share/vlc/ml.xspf'
[0x9722820] main input debug: creating demux: access='file' demux='xspf-open' path='/home/eric/.local/share/vlc/ml.xspf'
[0x9729208] main demux debug: looking for access_demux module: 1 candidate
[0x9729208] main demux warning: no access_demux module matching "file" could be loaded
[0x9729208] main demux debug: TIMER module_need() : 0.643 ms - Total 0.643 ms / 1 intvls (Avg 0.643 ms)
[0x9722820] main input debug: creating access 'file' path='/home/eric/.local/share/vlc/ml.xspf'
[0x972b140] main access debug: looking for access module: 3 candidates
[0x972b140] access_file access debug: opening file `/home/eric/.local/share/vlc/ml.xspf'
[0x972b140] main access debug: using access module "access_file"
[0x972b140] main access debug: TIMER module_need() : 0.592 ms - Total 0.592 ms / 1 intvls (Avg 0.592 ms)
[0x972b228] main stream debug: Using AStream*Stream
[0x972b228] main stream debug: pre buffering
[0x972b228] main stream debug: received first data after 0 ms
[0x972b228] main stream debug: pre-buffering done 296 bytes in 0s - 9033 kbytes/s
[0x972b9c8] main stream debug: looking for stream_filter module: 4 candidates
[0x972b9c8] main stream debug: TIMER module_need() : 0.729 ms - Total 0.729 ms / 1 intvls (Avg 0.729 ms)
[0x972dc68] main stream debug: looking for stream_filter module: 1 candidate
[0x972dc68] main stream debug: using stream_filter module "stream_filter_record"
[0x972dc68] main stream debug: TIMER module_need() : 0.200 ms - Total 0.200 ms / 1 intvls (Avg 0.200 ms)
[0x9722820] main input debug: creating demux: access='file' demux='xspf-open' path='/home/eric/.local/share/vlc/ml.xspf'
[0x972cf10] main demux debug: looking for demux module: 1 candidate
[0x972cf10] playlist demux debug: using XSPF playlist reader
[0x972cf10] main demux debug: using demux module "playlist"
[0x972cf10] main demux debug: TIMER module_need() : 0.330 ms - Total 0.330 ms / 1 intvls (Avg 0.330 ms)
[0x9722820] main input debug: `file/xspf-open:///home/eric/.local/share/vlc/ml.xspf' successfully opened
[0x972dfc8] main xml debug: looking for xml module: 2 candidates
[0x972dfc8] main xml debug: using xml module "xtag"
[0x972dfc8] main xml debug: TIMER module_need() : 0.595 ms - Total 0.595 ms / 1 intvls (Avg 0.595 ms)
[0x972cf10] playlist demux debug: parsed 0 tracks successfully
[0x972dfc8] main xml debug: removing module "xtag"
[0x9722820] main input debug: EOF reached
[0x972cf10] main demux debug: removing module "playlist"
[0x972dc68] main stream debug: removing module "stream_filter_record"
[0x972b140] main access debug: removing module "access_file"
[0x9722820] main input debug: TIMER input launching for 'Media Library' : 20.871 ms - Total 20.871 ms / 1 intvls (Avg 20.871 ms)
[0x9723ca0] main playlist debug: rebuilding array of current - root Playlist
[0x9723ca0] main playlist debug: rebuild done - 0 items, index -1
[0x9723ca0] main playlist debug: Activated
[0x972dc38] main interface debug: looking for interface module: 1 candidate
[0x972dc38] main interface debug: using interface module "hotkeys"
[0x972dc38] main interface debug: TIMER module_need() : 0.381 ms - Total 0.381 ms / 1 intvls (Avg 0.381 ms)
[0x972dc38] main interface debug: thread started
[0x972dc38] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x9723498] main interface debug: looking for interface module: 1 candidate
[0x9723498] main interface debug: using interface module "inhibit"
[0x9723498] main interface debug: TIMER module_need() : 2.709 ms - Total 2.709 ms / 1 intvls (Avg 2.709 ms)
[0x9723498] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x9723498] main interface debug: thread started
[0x972b368] main interface debug: looking for interface module: 1 candidate
[0x972b368] main interface debug: using interface module "screensaver"
[0x972b368] main interface debug: TIMER module_need() : 0.319 ms - Total 0.319 ms / 1 intvls (Avg 0.319 ms)
[0x972b368] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x972b368] main interface debug: thread started
[0x96962d8] main interface debug: looking for interface module: 1 candidate
[0x96962d8] main interface debug: using interface module "signals"
[0x96962d8] main interface debug: TIMER module_need() : 0.256 ms - Total 0.256 ms / 1 intvls (Avg 0.256 ms)
[0x96962d8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x96962d8] main interface debug: thread started
[0x96962d8] main interface debug: thread ended
[0x9696490] main interface debug: looking for interface module: 0 candidates
[0x9696490] main interface error: no interface module matched "globalhotkeys,none"
[0x9696490] main interface debug: TIMER module_need() : 0.106 ms - Total 0.106 ms / 1 intvls (Avg 0.106 ms)
[0x9696490] main interface error: no suitable interface module
[0x9696140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9696140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9696428] main interface debug: looking for interface module: 4 candidates
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

(<unknown>:25622): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
[0x9696428] qt4 interface debug: Error while initializing qt-specific localization
[0x9696428] main interface debug: using interface module "qt4"
[0x9696428] main interface debug: TIMER module_need() : 380.534 ms - Total 380.534 ms / 1 intvls (Avg 380.534 ms)
[0x9696428] main interface debug: thread started
[0x9696428] main interface debug: thread ended
[0x9696428] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x9723ca0] main playlist debug: adding item `FileName.avi' ( /home/eric/Downloads/FilePath/FileName.avi )
[0x9696428] qt4 interface debug: Adding a new MRL to recent ones: /home/eric/Downloads/FilePath/FileName.avi
[0x9723ca0] main playlist debug: rebuilding array of current - root Playlist
[0x9723ca0] main playlist debug: rebuild done - 1 items, index -1
[0x9723ca0] main playlist debug: processing request item FileName.avi node null skip 0
[0x9723ca0] main playlist debug: resyncing on FileName.avi
[0x9723ca0] main playlist debug: FileName.avi is at 0
[0x9723ca0] main playlist debug: starting new item
[0x9723ca0] main playlist debug: creating new input thread
[0xb7200f80] main input debug: Creating an input for 'FileName.avi'
[0xb7200f80] main input debug: thread (input) created at priority 10 (input/input.c:230)
[0xb7200f80] main input debug: thread started
[0xb7200f80] main input debug: using timeshift granularity of 50 MBytes
[0xb7200f80] main input debug: using timeshift path '/tmp'
[0xb7200f80] main input debug: `/home/eric/Downloads/FilePath/FileName.avi' gives access `' demux `' path `/home/eric/Downloads/FilePath/FileName.avi'
[0xb7200f80] main input debug: creating demux: access='' demux='' path='/home/eric/Downloads/FilePath/FileName.avi'
[0x996ceb0] main demux debug: looking for access_demux module: 7 candidates
[0x996ceb0] main demux debug: TIMER module_need() : 1.794 ms - Total 1.794 ms / 1 intvls (Avg 1.794 ms)
[0xb7200f80] main input debug: creating access '' path='/home/eric/Downloads/FilePath/FileName.avi'
[0x9b1aa50] main access debug: looking for access module: 7 candidates
[0x9b1aa50] vcd access debug: trying .cue file: /home/eric/Downloads/FilePath/FileName.cue
[0x9b1aa50] vcd access debug: could not find .cue file
[0x9b1aa50] access_file access debug: opening file `/home/eric/Downloads/FilePath/FileName.avi'
[0x9b1aa50] main access debug: using access module "access_file"
[0x9b1aa50] main access debug: TIMER module_need() : 2.028 ms - Total 2.028 ms / 1 intvls (Avg 2.028 ms)
[0x9b3cac8] main stream debug: Using AStream*Stream
[0x9b3cac8] main stream debug: pre buffering
[0x9b3cac8] main stream debug: received first data after 0 ms
[0x9b3cac8] main stream debug: pre-buffering done 1024 bytes in 0s - 40000 kbytes/s
[0x9a93128] main stream debug: looking for stream_filter module: 4 candidates
[0x9a93128] main stream debug: TIMER module_need() : 0.119 ms - Total 0.119 ms / 1 intvls (Avg 0.119 ms)
[0x996a7f0] main stream debug: looking for stream_filter module: 1 candidate
[0x996a7f0] main stream debug: using stream_filter module "stream_filter_record"
[0x996a7f0] main stream debug: TIMER module_need() : 0.110 ms - Total 0.110 ms / 1 intvls (Avg 0.110 ms)
[0xb7200f80] main input debug: creating demux: access='' demux='' path='/home/eric/Downloads/FilePath/FileName.avi'
[0x996ceb0] main demux debug: looking for demux module: 50 candidates
[0x996a7f0] avi stream debug: found Chunk fourcc:46464952 (RIFF) size:3520022 pos:0
[0x996a7f0] avi stream debug: found LIST chunk: 'AVI '
[0x996a7f0] avi stream debug: <list 'AVI '>
[0x996a7f0] avi stream debug: found Chunk fourcc:5453494c (LIST) size:8822 pos:12
[0x996a7f0] avi stream debug: found LIST chunk: 'hdrl'
[0x996a7f0] avi stream debug: <list 'hdrl'>
[0x996a7f0] avi stream debug: found Chunk fourcc:68697661 (avih) size:56 pos:24
[0x996a7f0] avi stream debug: avih: streams:2 flags: HAS_INDEX IS_INTERLEAVED TRUST_CKTYPE 480x270
[0x996a7f0] avi stream debug: found Chunk fourcc:5453494c (LIST) size:4240 pos:88
[0x996a7f0] avi stream debug: found LIST chunk: 'strl'
[0x996a7f0] avi stream debug: <list 'strl'>
[0x996a7f0] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:100
[0x996a7f0] avi stream debug: strh: type:vids handler:0x3234504d samplesize:0 47.92fps
[0x996a7f0] avi stream debug: found Chunk fourcc:66727473 (strf) size:40 pos:164
[0x996a7f0] avi stream debug: strf: video:MP42 480x270 planes:1 24bpp
[0x996a7f0] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:4116 pos:212
[0x996a7f0] avi stream debug: </list 'strl'>
[0x996a7f0] avi stream debug: found Chunk fourcc:5453494c (LIST) size:4230 pos:4336
[0x996a7f0] avi stream debug: found LIST chunk: 'strl'
[0x996a7f0] avi stream debug: <list 'strl'>
[0x996a7f0] avi stream debug: found Chunk fourcc:68727473 (strh) size:56 pos:4348
[0x996a7f0] avi stream debug: strh: type:auds handler:0x00000001 samplesize:0 38.28fps
[0x996a7f0] avi stream debug: found Chunk fourcc:66727473 (strf) size:30 pos:4412
[0x996a7f0] avi stream debug: strf: audio:0x0055 channels:2 44100Hz 0bits/sample 62kb/s
[0x996a7f0] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:4116 pos:4450
[0x996a7f0] avi stream debug: </list 'strl'>
[0x996a7f0] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:260 pos:8574
[0x996a7f0] avi stream debug: </list 'hdrl'>
[0x996a7f0] avi stream debug: found Chunk fourcc:5453494c (LIST) size:24 pos:8842
[0x996a7f0] avi stream debug: found LIST chunk: 'INFO'
[0x996a7f0] avi stream debug: <list 'INFO'>
[0x996a7f0] avi stream debug: found Chunk fourcc:54465349 (ISFT) size:12 pos:8854
[0x996a7f0] avi stream debug: ISFT: software : Lavf51.12.1
[0x996a7f0] avi stream debug: </list 'INFO'>
[0x996a7f0] avi stream debug: found Chunk fourcc:4b4e554a (JUNK) size:1016 pos:8874
[0x996a7f0] avi stream debug: found Chunk fourcc:5453494c (LIST) size:3386388 pos:9898
[0x996a7f0] avi stream debug: skipping movi chunk
[0x996a7f0] avi stream debug: found Chunk fourcc:31786469 (idx1) size:123728 pos:3396294
[0x996a7f0] avi stream debug: idx1: index entry:7733
[0x996a7f0] avi stream debug: </list 'AVI '>
[0x996a7f0] avi stream debug: * LIST-root size:3520030 pos:0
[0x996a7f0] avi stream debug:      + RIFF-AVI  size:3520022 pos:0
[0x996a7f0] avi stream debug:      |    + LIST-hdrl size:8822 pos:12
[0x996a7f0] avi stream debug:      |    |    + avih size:56 pos:24
[0x996a7f0] avi stream debug:      |    |    + LIST-strl size:4240 pos:88
[0x996a7f0] avi stream debug:      |    |    |    + strh size:56 pos:100
[0x996a7f0] avi stream debug:      |    |    |    + strf size:40 pos:164
[0x996a7f0] avi stream debug:      |    |    |    + JUNK size:4116 pos:212
[0x996a7f0] avi stream debug:      |    |    + LIST-strl size:4230 pos:4336
[0x996a7f0] avi stream debug:      |    |    |    + strh size:56 pos:4348
[0x996a7f0] avi stream debug:      |    |    |    + strf size:30 pos:4412
[0x996a7f0] avi stream debug:      |    |    |    + JUNK size:4116 pos:4450
[0x996a7f0] avi stream debug:      |    |    + JUNK size:260 pos:8574
[0x996a7f0] avi stream debug:      |    + LIST-INFO size:24 pos:8842
[0x996a7f0] avi stream debug:      |    |    + ISFT size:12 pos:8854
[0x996a7f0] avi stream debug:      |    + JUNK size:1016 pos:8874
[0x996a7f0] avi stream debug:      |    + LIST-movi size:3386388 pos:9898
[0x996a7f0] avi stream debug:      |    + idx1 size:123728 pos:3396294
[0x996ceb0] avi demux debug: AVIH: 2 stream, flags  HAS_INDEX IS_INTERLEAVED TRUST_CKTYPE 
[0x996ceb0] avi demux debug: stream[0] rate:575 scale:12 samplesize:0
[0x996ceb0] avi demux debug: stream[0] video(MP42) 480x270 24bpp 47.916667fps
[0xb7200f80] main input debug: selecting program id=0
[0x996ceb0] avi demux debug: stream[1] rate:1225 scale:32 samplesize:0
[0x996ceb0] avi demux debug: stream[1] audio(0x55) 2 channels 44100Hz 0bits
[0x996ceb0] avi demux debug: stream[0] created 4287 index entries
[0x996ceb0] avi demux debug: stream[1] created 3446 index entries
[0x996ceb0] avi demux debug: stream[0] length:89 (based on index)
[0x996ceb0] avi demux debug: stream[1] length:90 (based on index)
[0x996ceb0] main demux debug: using demux module "avi"
[0x996ceb0] main demux debug: TIMER module_need() : 5.731 ms - Total 5.731 ms / 1 intvls (Avg 5.731 ms)
[0xb7200f80] main input debug: looking for a subtitle file in /home/eric/Downloads/FilePath/
[0xb7203868] main decoder debug: looking for decoder module: 30 candidates
[0xb7203868] main decoder debug: TIMER module_need() : 7.566 ms - Total 7.566 ms / 1 intvls (Avg 7.566 ms)
[0xb7203868] main decoder error: no suitable decoder module for fourcc `MP42'.
VLC probably does not support this sound or video format.
[0xb7203868] main decoder debug: killing decoder fourcc `MP42', 0 PES in FIFO
[0x9b1d080] main decoder debug: looking for decoder module: 30 candidates
[0x9b1d080] main decoder debug: using decoder module "mpeg_audio"
[0x9b1d080] main decoder debug: TIMER module_need() : 0.455 ms - Total 0.455 ms / 1 intvls (Avg 0.455 ms)
[0x9b1d080] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:315)
[0x9b1d080] main decoder debug: thread started
[0x9696428] qt4 interface debug: IM: Setting an input
[0x9696428] qt4 interface debug: Updating the geometry
[0xb7200f80] main input debug: `/home/eric/Downloads/FilePath/FileName.avi' successfully opened
[0xb7200f80] main input debug: Buffering 0%
[0xb7200f80] main input debug: Buffering 8%
[0xb7200f80] main input debug: Buffering 16%
[0xb7200f80] main input debug: Buffering 25%
[0xb7200f80] main input debug: Buffering 33%
[0xb7200f80] main input debug: Buffering 41%
[0xb7200f80] main input debug: Buffering 50%
[0xb7200f80] main input debug: Buffering 58%
[0xb7200f80] main input debug: Buffering 66%
[0xb7200f80] main input debug: Buffering 75%
[0xb7200f80] main input debug: Buffering 83%
[0xb7200f80] main input debug: Buffering 91%
[0xb7200f80] main input debug: Buffering 100%
[0xb7200f80] main input debug: Stream buffering done (325 ms in 0 ms)
[0x9b1d080] mpeg_audio decoder debug: MPGA channels:2 samplerate:44100 bitrate:64
[0xb7200f80] main input debug: creating aout
[0x99851c0] main audio output debug: looking for audio output module: 4 candidates
[0x99851c0] pulse audio output: No. of Audio Channels: 2
[0x99851c0] pulse audio output debug: Pulse mainloop started
[0x9696428] qt4 interface debug: Updating the geometry
[0x99851c0] pulse audio output debug: Pulse stream connected
[0x99851c0] pulse audio output debug: Pulse initialized successfully
[0x99851c0] pulse audio output debug: Buffer metrics: maxlength=141120, tlength=42336, prebuf=35280, minreq=7056
[0x99851c0] pulse audio output debug: Using sample spec 'float32le 2ch 44100Hz', channel map 'front-left,front-right'.
[0x99851c0] pulse audio output debug: Connected to device alsa_output.pci-0000_00_1b.0.analog-stereo (0, not suspended).
[0x99851c0] main audio output debug: using audio output module "pulse"
[0x99851c0] main audio output debug: TIMER module_need() : 87.879 ms - Total 87.879 ms / 1 intvls (Avg 87.879 ms)
[0x99851c0] main audio output debug: output 'fl32' 44100 Hz Stereo frame=1 samples/8 bytes
[0x99851c0] main audio output debug: mixer 'fl32' 44100 Hz Stereo frame=1 samples/8 bytes
[0x99851c0] main audio output debug: no need for any filter
[0x99851c0] main audio output debug: looking for audio mixer module: 3 candidates
[0x99851c0] main audio output debug: using audio mixer module "float32_mixer"
[0x99851c0] main audio output debug: TIMER module_need() : 0.446 ms - Total 0.446 ms / 1 intvls (Avg 0.446 ms)
[0x99851c0] main audio output debug: input 'mpga' 44100 Hz Stereo frame=1152 samples/1053 bytes
[0x9b5c900] main audio filter debug: looking for audio filter module: 1 candidate
[0x9b5c900] scaletempo audio filter warning: bad input or output format
[0x9b5c900] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
[0x9b5c900] main audio filter debug: TIMER module_need() : 0.427 ms - Total 0.427 ms / 1 intvls (Avg 0.427 ms)
[0x9b5c900] main audio filter debug: looking for audio filter module: 1 candidate
[0x9b5c900] scaletempo audio filter debug: format: 44100 rate, 2 nch, 4 bps, fl32
[0x9b5c900] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search
[0x9b5c900] scaletempo audio filter debug: 1.000 scale, 1323.000 stride_in, 1323 stride_out, 1059 standing, 264 overlap, 617 search, 2204 queue, fl32 mode
[0x9b5c900] main audio filter debug: using audio filter module "scaletempo"
[0x9b5c900] main audio filter debug: TIMER module_need() : 0.388 ms - Total 0.388 ms / 1 intvls (Avg 0.388 ms)
[0x99851c0] main audio output debug: filter(s) 'mpga'->'fl32' 44100 Hz->44100 Hz Stereo->Stereo
[0x9b4f800] main audio output debug: looking for audio filter module: 24 candidates
[0x9b4f800] main audio output debug: using audio filter module "mpgatofixed32"
[0x9b4f800] main audio output debug: TIMER module_need() : 0.459 ms - Total 0.459 ms / 1 intvls (Avg 0.459 ms)
[0x99851c0] main audio output debug: found a filter for the whole conversion
[0x99851c0] main audio output debug: filter(s) 'fl32'->'fl32' 48510 Hz->44100 Hz Stereo->Stereo
[0x9b4f978] main audio output debug: looking for audio filter module: 24 candidates
[0x9b4f978] main audio output debug: using audio filter module "bandlimited_resampler"
[0x9b4f978] main audio output debug: TIMER module_need() : 0.984 ms - Total 0.984 ms / 1 intvls (Avg 0.984 ms)
[0x99851c0] main audio output debug: found a filter for the whole conversion
[0x9b1d080] main decoder debug: End of audio preroll
[0xb7200f80] main input debug: Decoder buffering done in 92 ms
[0x99851c0] main audio output warning: PTS is out of range (-9813), dropping buffer
[0x99851c0] main audio output warning: PTS is out of range (-35904), dropping buffer
[0x99851c0] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[0x99851c0] pulse audio output debug: Pulse stream started
[0x99851c0] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[0x99851c0] mpgatofixed32 audio output debug: libmad error: bad main_data_begin pointer
[0x99851c0] main audio output warning: output date isn't PTS date, requesting resampling (113934)
[0x99851c0] main audio output warning: buffer is 113933 late, triggering upsampling

```

Thanks a lot for all of the input so far everyone. I appreciate it!
(sorry for such a long post lol)

---

### Post by 11010110 on 2009-11-01
I just tried doing a complete purge of vlc data and then I hunted down every config file and other data associated with vlc (I think I got it all) and then did a reinstall. Still nothing will play.

---

### Post by jmszr on 2009-11-01
11010110,

You can download a VLC 9.9a 386i .deb from here:[http://packages.ubuntu.com/jaunty/i386/vlc/download](http://packages.ubuntu.com/jaunty/i386/vlc/download)

Don't know if that will help you, but......

---

### Post by super kim on 2009-11-01
sorry i can't help you with your problem but i'd just like to report that i have upgraded to karmic, i only use totem to watch video files.
i installed the restricted extras and i can play every video file on my hard drive.

when i used windows i swore that vlc was the bees knees but after switching to ubuntu i don't see the point in using it for watching files on my hdd.

as always though your computer your choice but best of luck configuring vlc though

---

### Post by 11010110 on 2009-11-01
I have used vlc on windows and linux for as long as I can remember. The thing is that no movie player will play any type of video... It has to be a bigger problem in Karmic itself I guess...

I hope that someone figures it out because I have still found nothing in all of my searches lol.

---

### Post by jmszr on 2009-11-02
11010110,

Perhaps this thread will be useful:[http://ubuntuforums.org/showthread.php?p=8212552](http://ubuntuforums.org/showthread.php?p=8212552)

The gist of it is to try this:

```
sudo apt-get install libavcodec52
```

Hope that helps.

---

### Post by kansasnoob on 2009-11-02
Neither Totem or VLC work as well in Karmic as they do in Jaunty!

---

### Post by 11010110 on 2009-11-02
Hey jmszr,

Thanks for the reply. Sadly this did not work for me. It seems like this is helping some people though so maybe someone else with this problem will come across this thread and it could help them out. 

Thanks again for the input I appreciate it.

---

### Post by 11010110 on 2009-11-02
I'm not sure what this could mean but the error message I receive when opening a video has changed after inputing: 
```
sudo apt-get install libavcodec52
```

Now it reads:
```
Your input can't be opened:
VLC is unable to open the MRL '/home/eric/Downloads/D6DE1457d01'. Check the log for details.

```

Maybe we are making headway after all lol. Anyone know what could be going on now?

---

### Post by frodon on 2009-11-02
The packages "ubuntu-restricted-extras" should install all the packages you might miss to read video/music.

Install it ans see if it helps.

---

### Post by 11010110 on 2009-11-02
hey frodon,

Thanks for the reply. I have had the restricted extras installed since the start. Still hasn't helped. Usually this gives you everything you need but there must be something broken somewhere else in Karmic. Strange eh? I have been searching all over and all of the fixes that have helped everyone else haven't gotten me anywhere.

---

### Post by DustofDust on 2009-11-02
vlc plays here but is stuttering since upgrade to karmic.

[http://www.videolan.org/](http://www.videolan.org/)
> VLC 1.0.3 Release

2009-10-31

so it is time for ubuntu to make some updates to vlc in the repo and to fix the problems. it is very clear that the problems are on the ubuntu side and not on the vlc side, as, according to informations from vlc developer directly, in debian sid it runs fine.

i would select vlc over ubuntu if these problems arent fixed!

---

### Post by frodon on 2009-11-02
> **11010110 said:**
> Thanks for the reply. I have had the restricted extras installed since the start. Still hasn't helped. Usually this gives you everything you need but there must be something broken somewhere else in Karmic. Strange eh? I have been searching all over and all of the fixes that have helped everyone else haven't gotten me anywhere.Ok then as a temporary workaround you could install mplayer, i've seen users not having this issue with mplayer only so hopefully you can have the functionality while waiting for a VLC solution.

---

### Post by alphacrucis2 on 2009-11-02
> **11010110 said:**
> hey frodon,

Thanks for the reply. I have had the restricted extras installed since the start. Still hasn't helped. Usually this gives you everything you need but there must be something broken somewhere else in Karmic. Strange eh? I have been searching all over and all of the fixes that have helped everyone else haven't gotten me anywhere.

Same problem here. Since upgrading from Jaunty to Karmic, flv files wont play in vlc. Avidemux can read them and display them ok which shows the codecs must be installed ok.

---

### Post by mikechant on 2009-11-02
Not helpful for getting vlc to work, but:
I used to swear by vlc but over the past few years I've had more and more assorted problems with it, and recently switched to totem (the default Ubuntu player) which I'd previously found inadaquete (in terms of which video types it could play) but I now find it plays everything I throw at it (as long as all the codec packages and libdvdcss2 are installed).

Haven't tried totem on 9.10 yet, but I assume as the default player it would be reasonably well tested by the Canonical team, whereas vlc might not be.

---

### Post by DustofDust on 2009-11-02
> **mikechant said:**
> Not helpful for getting vlc to work, but:
I used to swear by vlc but over the past few years I've had more and more assorted problems with it, and recently switched to totem (the default Ubuntu player) which I'd previously found inadaquete (in terms of which video types it could play) but I now find it plays everything I throw at it (as long as all the codec packages and libdvdcss2 are installed).

Haven't tried totem on 9.10 yet, but I assume as the default player it would be reasonably well tested by the Canonical team, whereas vlc might not be.

and there is the problem, they dont test it with vlc. and compared to vlc, totem lacks a lot of features, it is just a simple player. no shoutcast, shoutcast tv, takes much longer to start playing videos, no save file, convert and so on...

---

### Post by 11010110 on 2009-11-02
Hey all,

I installed avidemux (as someone mentioned above) and I can play some video through that (although it is a video editor and has no fullscreen etc which are useful for viewing lol). movie player and vlc still do not work at all. It is good to see that I can get some kind of video besides streaming flash to work(ish) though. Now to get a PLAYER working lol. 

Heres an interesting sidenote... mplayer will not work for me for some reason now. 
Whenever i try to open it the terminal spits this out at me:

```
mplayer: error while loading shared libraries: libx264.so.67: cannot open shared object file: No such file or directory
```

I tried to uninstall and reinstall it and even purged it and no luck now.

Thanks for all the input everyone. Maybe the new version of VLC will make it into the repos soon!

---

### Post by mc4man on 2009-11-02
try a couple of things

search vlc in synaptic and if there is a libvlccore0 package installed then remove it
(or mark and remove all vlc packages starting with libvlc2 and below, apply, then re-install

search ffmpeg in synaptic and mark the extra versions of the ffmpeg libs for install, apply (don't remove the current ones, libavcodec52 libavformat52 ect. (7 in all

(ubuntu-restricted-extras installs the stripped versions, not the extra versions

If you wanted to clean out all the vlc configs they are here in home folder (hidden

.cache/vlc
.config/vlc
.local/share/vlc

---

### Post by 11010110 on 2009-11-02
Hey everyone good news!

I got it to work (for the most part) for me. If you go into vlc prefs and under video chose Output: OpenGL video output, then it works! At least for me. I also tried reinstalling a whole mess of packages, namely libx264-67 which takes pretty much everything video related with it. I reinstalled everything by hand! I am not sure which one did the trick but I'm running ok-ish now. There are no on screen controls and there are some minor graphical issues (blank spots in vlc surrounding the video frame) but I'll take it over no video lol. Id suggest the vlc settings first because it's easier. 

Good luck to all! If anyone has any questions I'll keep trying to help as best I can!

---

### Post by lennypasta on 2009-11-02
> **jmszr said:**
> 11010110,

Perhaps this thread will be useful:[http://ubuntuforums.org/showthread.php?p=8212552](http://ubuntuforums.org/showthread.php?p=8212552)

The gist of it is to try this:

```
sudo apt-get install libavcodec52
```

Hope that helps.

I was having the problems described in this topic and it was driving me nuts!

The above solved it...so thank you very much jmszr

---

### Post by chenxiaolong on 2009-11-02
Please take a look at my post. I figured out how to make it work.

[http://ubuntuforums.org/showthread.php?p=8225785#post8225785](http://ubuntuforums.org/showthread.php?p=8225785#post8225785)

Remember, you HAVE TO remove the Medibuntu repository. That's what's causing the problems.

---

### Post by iamnotthemessiah on 2009-11-02
> **11010110 said:**
> Hey everyone good news!

I got it to work (for the most part) for me. If you go into vlc prefs and under video chose Output: OpenGL video output, then it works! At least for me. I also tried reinstalling a whole mess of packages, namely libx264-67 which takes pretty much everything video related with it. I reinstalled everything by hand! I am not sure which one did the trick but I'm running ok-ish now. There are no on screen controls and there are some minor graphical issues (blank spots in vlc surrounding the video frame) but I'll take it over no video lol. Id suggest the vlc settings first because it's easier. 

Good luck to all! If anyone has any questions I'll keep trying to help as best I can!

it does for me too, thanks
mp3 playback didnt work for me either but setting that to 'default' under the audio button sorted it. i dont recall what it was set to before

---

### Post by alphacrucis2 on 2009-11-02
What I did to fix this was:

1. Disable medibuntu karmic repo.

2. apt-get --purge remove libx264-67

I seemed to have a version of this from a PPA which was newer that the karmic version but was causing trouble with mplayer/mencoder. Anyway this removes all the dependent video players/authoring, transcoders etc. I copied all the package names it wanted to remove into a text file and let it remove them.

3. ReInstall the package names saved in the text file using the standard Karmic repos. No medibuntu or PPA's. 

4. Problem solved.

---

### Post by jfeole on 2009-11-02
I upgraded from 9.04 to 9.10 and ran into this too.  I resolved it by doing in terminal:

--

$ sudo apt-get remove smplayer
$ sudo apt-get remove mplayer
$ sudo apt-get remove libx264-67 --purge
$ sudo apt-get install libx264-67
$ sudo apt-get install smplayer
$ sudo apt-get install mplayer
$ sudo apt-get install vlc

--


Regards,
JFeole

---

### Post by DustofDust on 2009-11-03
[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)
 vlc  	1.0.3-1~ppa1

there was also a pulseaudio update today, but that did not fix the stuttering audio while playing videos.

btw. you can also ad ubuntustudio meta in the repo to get a lot of audio and video stuff.

---

### Post by zba78 on 2009-11-03
> **jmszr said:**
> 11010110,

Perhaps this thread will be useful:[http://ubuntuforums.org/showthread.php?p=8212552](http://ubuntuforums.org/showthread.php?p=8212552)

The gist of it is to try this:

```
sudo apt-get install libavcodec52
```Hope that helps.
Thanks for this jmszr, I had the same problem as other after upgrading and this solved them. I can now watch videos in both VLC and totem

---

### Post by JayKay3000 on 2009-11-03
I can only scratch my head and say whats up with the Totem Movie/music player. Download all the codecs and it runs pretty much everything.

---

### Post by DustofDust on 2009-11-03
[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

has always up to date packages of vlc.

now my vlc runs perfect after i had a reboot! pulseaudio needed it...

---

### Post by ACLBandit on 2009-11-16
> **alphacrucis2 said:**
> What I did to fix this was:

1. Disable medibuntu karmic repo.

2. apt-get --purge remove libx264-67


THIS. 

Not only did you save my MPlayer, you rescued OGMRip too. THANK YOU.

---

