---
title: "Can't Play MP4"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-06-18
All of a sudden, I can no longer play any mp4, or avi files with either vlc or totem. I get an error saying that it doesn't have the right decoders and there is no way to fix it. 

[IMG]http://i93.photobucket.com/albums/l41/buck3tph0t0/VLCandTotemDecoders.png[/IMG]

I can still play ogv though. Can it be related to this?

[IMG]http://i93.photobucket.com/albums/l41/buck3tph0t0/ProprietaryFormats.png[/IMG]

[http://www.ubuntu.com/products/whatisubuntu/904features/music/](http://www.ubuntu.com/products/whatisubuntu/904features/music/)

Does this mean I actually I have to buy codecs, even though I'm using it for "educational purposes?"

---

### Post by ~sHyLoCk~ on 2009-06-18
Search for faad and libfaad0 in Synaptic

---

### Post by Sup3r3g0 on 2009-06-18
> **~sHyLoCk~ said:**
> Search for faad and libfaad0 in Synaptic

I tried it. Still no luck

---

### Post by Sup3r3g0 on 2009-06-19
BUMP

I reinstalled VLC, totem, ffmpeg, medibuntu, and the ubuntu restricted extras and I'm still getting an error message.

---

### Post by t0p on 2009-06-19
This is most curious.  Has anyone else experienced this?  I haven't, and I watch a lot of videos on my Jaunty NBR machine.  That stuff about purchasing codecs is strange.

---

### Post by mc4man on 2009-06-19
try searching ffmpeg in synaptic and make sure libavcodec52 is the unstripped one, if not mark for install and apply.

---

### Post by Sup3r3g0 on 2009-06-19
I found it and reinstalled it. Unfortunatly, I'm still unable to play any mp4's.

---

### Post by LowSky on 2009-06-19
install medibutnu awith this command

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```


now the next requires you to know if your using 32 or 64 Bit OS
this will install all codecs you may ever need

32 bit
```
sudo apt-get install w32codecs
```

64bit
```
sudo apt-get install w64codecs
```

more info see this
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Sup3r3g0 on 2009-06-19
I reinstalled medibuntu and the 32 bit codecs with the commands you gave. I'm still having problems. 

Heres's a what he properties of mp4 files look like now. (they weren't always like this)
[IMG]http://i93.photobucket.com/albums/l41/buck3tph0t0/Screenshot-lebronjamesmp4Properties.png[/IMG]

Should I just reinstall? I have my home directory on another partition, so I don't have to worry about losing any data.

---

### Post by mc4man on 2009-06-19
The suddenly part seems to be relevant, you appear to have everything you need in regards to m4a (aac) and vc1.

w64 codecs are pretty much worthless and while w32codecs is of value 2 things.
Vlc doesn't use w32codecs unless configured in the build, which the ubuntu repos and any ppa I've seen don't do

m4a (aac) and vc1 aren't part of w32codecs

I'd first try resetting vlc
```

vlc --reset-config --reset-plugins-cache
```
The modules involved are 
faad, mp4, vc1, avcodec

Rather than get the complete list, ck. on them one at a time, should return a module(s) name

```
vlc -vvv --no-plugins-cache --list |grep -i faad
```

```
 vlc -vvv --no-plugins-cache --list |grep -i vc1
```

ect.

While the output will be large you could start vlc like this and try one of your files.

```
vlc -vv
```

Note: just saw your post, maybe try to get some better info on your files,
if you have ffmpeg installed go ffmpeg -i /path/to/[COLOR="Blue"]filename.ext[/COLOR]
otherwise try vlc with the -vv (after resetting


small note on the fluendo codecs pac(s)
While they will enable playback of most formats, including all wma,wmv, they are** only for gstreamer players**, will have no effect or added support otherwise.

---

### Post by Sup3r3g0 on 2009-06-20
> **mc4man said:**
> The suddenly part seems to be relevant, you appear to have everything you need in regards to m4a (aac) and vc1.

w64 codecs are pretty much worthless and while w32codecs is of value 2 things.
Vlc doesn't use w32codecs unless configured in the build, which the ubuntu repos and any ppa I've seen don't do

m4a (aac) and vc1 aren't part of w32codecs

I'd first try resetting vlc
```

vlc --reset-config --reset-plugins-cache
```

Okay, I did that. I still can't open any mp4's.

> The modules involved are 
faad, mp4, vc1, avcodec

Rather than get the complete list, ck. on them one at a time, should return a module(s) name

```
vlc -vvv --no-plugins-cache --list |grep -i faad
```

```
 vlc -vvv --no-plugins-cache --list |grep -i vc1
```

ect.

I'm not quite sure what you're asking me to do. What am I supposed to do after I use the commands?

> While the output will be large you could start vlc like this and try one of your files.

```
vlc -vv
```

Note: just saw your post, maybe try to get some better info on your files,
if you have ffmpeg installed go ffmpeg -i /path/to/[COLOR="Blue"]filename.ext[/COLOR]


Here's what I get:
> 
username@computername:~$ ffmpeg -i /home/username/Videos/Youtube/AwkwardRap.mp4
FFmpeg version UNKNOWN-svnUNKNOWN+3:0.svn20090607-0.5~ppa1~jaunty1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --extra-version=svnUNKNOWN+3:0.svn20090607-0.5~ppa1~jaunty1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --enable-libxvid --enable-libmp3lame --enable-nonfree --enable-libfaac --enable-libx264 --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.30. 2 / 52.30. 2
  libavformat   52.34. 0 / 52.34. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jun  7 2009 16:24:01, gcc: 4.3.3

Seems stream 1 codec frame rate differs from container frame rate: 47.94 (47942/1000) -> 23.98 (24000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/username/Videos/Youtube/AwkwardRap.mp4':
  Duration: 00:03:12.40, start: 0.000000, bitrate: 626 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x270 [PAR 1:1 DAR 16:9], 23.98 tbr, 23.97 tbn, 47.94 tbc
At least one output file must be specified

> 
timothycbautista@slackware:~$ vlc -vv /home/timothycbautista/Videos/Youtube/AwkwardRap.mp4
VLC media player 1.0.0-rc3 Goldeneye
[0x9c7e140] main libvlc debug: VLC media player - version 1.0.0-rc3 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x9c7e140] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1~ppa1~jaunty2' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x9c7e140] main libvlc debug: translation test: code is "C"
[0x9c7e140] main libvlc debug: checking plugin modules
[0x9c7e140] main libvlc debug: loading plugins cache file /home/timothycbautista/.cache/vlc/plugins-04041e.dat
[0x9c7e140] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x9c7e140] main libvlc warning: cannot load module `/usr/lib/vlc/demux/libavformat_plugin.so' (libavutil.so.49: cannot open shared object file: No such file or directory)
[0x9c7e140] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libavcodec_plugin.so' (libavutil.so.49: cannot open shared object file: No such file or directory)
[0x9c7e140] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libfaad_plugin.so' (libfaad.so.0: cannot open shared object file: No such file or directory)
[0x9c7e140] main libvlc debug: module bank initialized (369 modules)
[0x9c7e140] main libvlc debug: opening config file (/home/timothycbautista/.config/vlc/vlcrc)
[0x9c7e140] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT FPU 
[0x9c7e140] main libvlc debug: looking for memcpy module: 3 candidates
[0x9c7e140] main libvlc debug: using memcpy module "memcpymmxext"
[0x9d196b0] main input debug: Creating an input for 'Media Library'
[0x9d196b0] main input debug: Input is a meta file: disabling unneeded options
[0x9d196b0] main input debug: using timeshift granularity of 50 MBytes
[0x9d196b0] main input debug: using timeshift  path '/tmp'
[0x9d196b0] main input debug: `file/xspf-open:///home/timothycbautista/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/timothycbautista/.local/share/vlc/ml.xspf'
[0x9d196b0] main input debug: creating demux: access='file' demux='xspf-open' path='/home/timothycbautista/.local/share/vlc/ml.xspf'
[0x9d1df80] main demux debug: looking for access_demux module: 1 candidate
[0x9d1df80] main demux warning: no access_demux module matching "file" could be loaded
[0x9d1df80] main demux debug: TIMER module_need() : 1.067 ms - Total 1.067 ms / 1 intvls (Avg 1.067 ms)
[0x9d196b0] main input debug: creating access 'file' path='/home/timothycbautista/.local/share/vlc/ml.xspf'
[0x9d1ff38] main access debug: looking for access module: 3 candidates
[0x9d1ff38] access_file access debug: opening file `/home/timothycbautista/.local/share/vlc/ml.xspf'
[0x9d1ff38] main access debug: using access module "access_file"
[0x9d1ff38] main access debug: TIMER module_need() : 0.819 ms - Total 0.819 ms / 1 intvls (Avg 0.819 ms)
[0x9d1f408] main stream debug: Using AStream*Stream
[0x9d1f408] main stream debug: pre buffering
[0x9d1f408] main stream debug: received first data after 0 ms
[0x9d1f408] main stream debug: pre-buffering done 296 bytes in 0s - 11117 kbytes/s
[0x9d20770] main stream debug: looking for stream_filter module: 4 candidates
[0x9d20770] main stream debug: TIMER module_need() : 0.697 ms - Total 0.697 ms / 1 intvls (Avg 0.697 ms)
[0x9d229f0] main stream debug: looking for stream_filter module: 1 candidate
[0x9d229f0] main stream debug: using stream_filter module "stream_filter_record"
[0x9d229f0] main stream debug: TIMER module_need() : 0.273 ms - Total 0.273 ms / 1 intvls (Avg 0.273 ms)
[0x9d196b0] main input debug: creating demux: access='file' demux='xspf-open' path='/home/timothycbautista/.local/share/vlc/ml.xspf'
[0x9d214c8] main demux debug: looking for demux module: 1 candidate
[0x9d214c8] playlist demux debug: using XSPF playlist reader
[0x9d214c8] main demux debug: using demux module "playlist"
[0x9d214c8] main demux debug: TIMER module_need() : 0.409 ms - Total 0.409 ms / 1 intvls (Avg 0.409 ms)
[0x9d196b0] main input debug: `file/xspf-open:///home/timothycbautista/.local/share/vlc/ml.xspf' successfully opened
[0x9d22f70] main xml debug: looking for xml module: 2 candidates
[0x9d22f70] main xml debug: using xml module "xml"
[0x9d22f70] main xml debug: TIMER module_need() : 0.710 ms - Total 0.710 ms / 1 intvls (Avg 0.710 ms)
[0x9d214c8] playlist demux debug: parsed 0 tracks successfully
[0x9d22f70] main xml debug: removing module "xml"
[0x9d196b0] main input debug: EOF reached
[0x9d214c8] main demux debug: removing module "playlist"
[0x9d229f0] main stream debug: removing module "stream_filter_record"
[0x9d1ff38] main access debug: removing module "access_file"
[0x9d196b0] main input debug: TIMER input launching for 'Media Library' : 8.264 ms - Total 8.264 ms / 1 intvls (Avg 8.264 ms)
[0x9d11b18] main playlist debug: rebuilding array of current - root Playlist
[0x9d11b18] main playlist debug: rebuild done - 0 items, index -1
[0x9d11b18] main playlist debug: Activated
[0x9d1d8b8] main interface debug: looking for interface module: 1 candidate
[0x9d1d8b8] main interface debug: using interface module "hotkeys"
[0x9d1d8b8] main interface debug: TIMER module_need() : 0.637 ms - Total 0.637 ms / 1 intvls (Avg 0.637 ms)
[0x9d1d8b8] main interface debug: thread started
[0x9d1d8b8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:156)
[0x9d229b0] main interface debug: looking for interface module: 1 candidate
[0x9d229b0] main interface debug: using interface module "inhibit"
[0x9d229b0] main interface debug: TIMER module_need() : 6.801 ms - Total 6.801 ms / 1 intvls (Avg 6.801 ms)
[0x9d229b0] main interface debug: thread started
[0x9d229b0] main interface debug: thread (interface) created at priority 0 (interface/interface.c:156)
[0x9d1e488] main interface debug: looking for interface module: 1 candidate
[0x9d1e488] main interface debug: using interface module "screensaver"
[0x9d1e488] main interface debug: TIMER module_need() : 1.006 ms - Total 1.006 ms / 1 intvls (Avg 1.006 ms)
[0x9d1e488] main interface debug: thread started
[0x9d1e488] main interface debug: thread (interface) created at priority 0 (interface/interface.c:156)
[0x9d11b18] main playlist debug: adding item `AwkwardRap.mp4' ( /home/timothycbautista/Videos/Youtube/AwkwardRap.mp4 )
[0x9d1bf08] main interface debug: looking for interface module: 1 candidate
[0x9d1bf08] main interface debug: using interface module "signals"
[0x9d1bf08] main interface debug: TIMER module_need() : 0.480 ms - Total 0.480 ms / 1 intvls (Avg 0.480 ms)
[0x9d1bf08] main interface debug: thread started
[0x9d1bf08] main interface debug: thread ended
[0x9d1bf08] main interface debug: thread (interface) created at priority 0 (interface/interface.c:156)
[0x9d24ca0] main interface debug: looking for interface module: 0 candidates
[0x9d24ca0] main interface error: no interface module matched "globalhotkeys,none"
[0x9d24ca0] main interface debug: TIMER module_need() : 0.149 ms - Total 0.149 ms / 1 intvls (Avg 0.149 ms)
[0x9d24ca0] main interface error: no suitable interface module
[0x9c7e140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9c7e140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9d24ca8] main interface debug: looking for interface module: 4 candidates
[0x9d24ca8] qt4 interface debug: Error while initializing qt-specific localization
[0x9d24ca8] main interface debug: using interface module "qt4"
[0x9d24ca8] main interface debug: TIMER module_need() : 866.419 ms - Total 866.419 ms / 1 intvls (Avg 866.419 ms)
[0x9d24ca8] main interface debug: thread started
[0x9d24ca8] main interface debug: thread ended
[0x9d24ca8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:156)
[0x9d11b18] main playlist debug: rebuilding array of current - root Playlist
[0x9d11b18] main playlist debug: rebuild done - 1 items, index -1
[0x9d11b18] main playlist debug: processing request item null node Playlist skip 0
[0x9d11b18] main playlist debug: starting new item
[0x9d11b18] main playlist debug: creating new input thread
[0xa009168] main input debug: Creating an input for 'AwkwardRap.mp4'
[0xa009168] main input debug: thread started
[0xa009168] main input debug: using timeshift granularity of 50 MBytes
[0xa009168] main input debug: using timeshift  path '/tmp'
[0xa009168] main input debug: thread (input) created at priority 10 (input/input.c:230)
[0xa009168] main input debug: `/home/timothycbautista/Videos/Youtube/AwkwardRap.mp4' gives access `' demux `' path `/home/timothycbautista/Videos/Youtube/AwkwardRap.mp4'
[0xa009168] main input debug: creating demux: access='' demux='' path='/home/timothycbautista/Videos/Youtube/AwkwardRap.mp4'
[0x9ee18a8] main demux debug: looking for access_demux module: 7 candidates
[0x9ee18a8] main demux debug: TIMER module_need() : 7.776 ms - Total 7.776 ms / 1 intvls (Avg 7.776 ms)
[0xa009168] main input debug: creating access '' path='/home/timothycbautista/Videos/Youtube/AwkwardRap.mp4'
[0xa00ade0] main access debug: looking for access module: 7 candidates
[0xa00ade0] vcd access debug: trying .cue file: /home/timothycbautista/Videos/Youtube/AwkwardRap.cue
[0xa00ade0] vcd access debug: could not find .cue file
[0xa00ade0] access_file access debug: opening file `/home/timothycbautista/Videos/Youtube/AwkwardRap.mp4'
[0xa00ade0] main access debug: using access module "access_file"
[0xa00ade0] main access debug: TIMER module_need() : 2.686 ms - Total 2.686 ms / 1 intvls (Avg 2.686 ms)
[0xa00fd70] main stream debug: Using AStream*Stream
[0xa00fd70] main stream debug: pre buffering
[0xa00fd70] main stream debug: received first data after 0 ms
[0xa00fd70] main stream debug: pre-buffering done 1024 bytes in 0s - 37037 kbytes/s
[0xa010588] main stream debug: looking for stream_filter module: 4 candidates
[0xa010588] main stream debug: TIMER module_need() : 0.954 ms - Total 0.954 ms / 1 intvls (Avg 0.954 ms)
[0xa010520] main stream debug: looking for stream_filter module: 1 candidate
[0xa010520] main stream debug: using stream_filter module "stream_filter_record"
[0xa010520] main stream debug: TIMER module_need() : 0.178 ms - Total 0.178 ms / 1 intvls (Avg 0.178 ms)
[0xa009168] main input debug: creating demux: access='' demux='' path='/home/timothycbautista/Videos/Youtube/AwkwardRap.mp4'
[0xa0105e8] main demux debug: looking for demux module: 50 candidates
[0xa010520] mp4 stream debug: found Box: ftyp size 28
[0xa010520] mp4 stream debug: found Box: moov size 112397
[0xa010520] mp4 stream debug: found Box: mvhd size 108
[0xa010520] mp4 stream debug: read box: "mvhd" creation 733192d-03h:28m:12s modification 733192d-03h:28m:12s time scale 600 duration 694977d-48h:00m:01s rate 1.000000 volume 1.000000 next track id 3
[0xa010520] mp4 stream debug: found Box: iods size 21
[0xa010520] mp4 stream warning: unknown box type iods (incompletely loaded)
[0xa010520] mp4 stream debug: found Box: trak size 74465
[0xa010520] mp4 stream debug: found Box: tkhd size 92
[0xa010520] mp4 stream debug: read box: "tkhd" creation 733192d-03h:28m:12s modification 733192d-03h:28m:12s duration 1444281207d-13h:04m:00s track ID 1 layer 0 volume 1.000000 width 0.000000 height 0.000000
[0xa010520] mp4 stream debug: found Box: mdia size 74365
[0xa010520] mp4 stream debug: found Box: mdhd size 32
[0xa010520] mp4 stream debug: read box: "mdhd" creation 733192d-03h:28m:12s modification 733192d-03h:28m:12s time scale 44100 duration 695075d-04h:54m:24s language und
[0xa010520] mp4 stream debug: found Box: hdlr size 66
[0xa010520] mp4 stream debug: read box: "hdlr" handler type soun name (C) 2007 Google Inc. v06.24.2007.
[0xa010520] mp4 stream debug: found Box: minf size 74259
[0xa010520] mp4 stream debug: found Box: smhd size 16
[0xa010520] mp4 stream debug: read box: "smhd" balance 0.000000
[0xa010520] mp4 stream debug: found Box: dinf size 36
[0xa010520] mp4 stream debug: found Box: dref size 28
[0xa010520] mp4 stream debug: found Box: url  size 12
[0xa010520] mp4 stream debug: read box: "url" url: (null)
[0xa010520] mp4 stream debug: read box: "dref" entry-count 1
[0xa010520] mp4 stream debug: found Box: stbl size 74199
[0xa010520] mp4 stream debug: found Box: stsd size 91
[0xa010520] mp4 stream debug: found Box: mp4a size 75
[0xa010520] mp4 stream debug: read box: "soun" mp4 or qt1/2 (rest=39)
[0xa010520] mp4 stream debug: found Box: esds size 39
[0xa010520] mp4 stream debug: found esds MPEG4ESDescr (25Bytes)
[0xa010520] mp4 stream debug: found esds MP4DecConfigDescr (17Bytes)
[0xa010520] mp4 stream debug: found esds MP4DecSpecificDescr (2Bytes)
[0xa010520] mp4 stream debug: read box: "soun" in stsd channel 2 sample size 16 sample rate 44100.000000
[0xa010520] mp4 stream debug: read box: "stsd" entry-count 1
[0xa010520] mp4 stream debug: found Box: stts size 24
[0xa010520] mp4 stream debug: read box: "stts" entry-count 1
[0xa010520] mp4 stream debug: found Box: stsc size 22492
[0xa010520] mp4 stream debug: read box: "stsc" entry-count 1873
[0xa010520] mp4 stream debug: found Box: stsz size 33164
[0xa010520] mp4 stream debug: read box: "stsz" sample-size 0 sample-count 8286
[0xa010520] mp4 stream debug: found Box: stco size 18420
[0xa010520] mp4 stream debug: read box: "co64" entry-count 4601
[0xa010520] mp4 stream debug: found Box: trak size 37795
[0xa010520] mp4 stream debug: found Box: tkhd size 92
[0xa010520] mp4 stream debug: read box: "tkhd" creation 733192d-03h:28m:12s modification 733192d-03h:28m:12s duration 1429318415d-45h:15m:44s track ID 2 layer 0 volume 0.000000 width 480.000000 height 270.000000
[0xa010520] mp4 stream debug: found Box: mdia size 37695
[0xa010520] mp4 stream debug: found Box: mdhd size 32
[0xa010520] mp4 stream debug: read box: "mdhd" creation 733192d-03h:28m:12s modification 733192d-03h:28m:12s time scale 23971 duration 695030d-05h:46m:40s language und
[0xa010520] mp4 stream debug: found Box: hdlr size 66
[0xa010520] mp4 stream debug: read box: "hdlr" handler type vide name (C) 2007 Google Inc. v06.24.2007.
[0xa010520] mp4 stream debug: found Box: minf size 37589
[0xa010520] mp4 stream debug: found Box: vmhd size 20
[0xa010520] mp4 stream debug: read box: "vmhd" graphics-mode 0 opcolor (0, 0, 0)
[0xa010520] mp4 stream debug: found Box: dinf size 36
[0xa010520] mp4 stream debug: found Box: dref size 28
[0xa010520] mp4 stream debug: found Box: url  size 12
[0xa010520] mp4 stream debug: read box: "url" url: (null)
[0xa010520] mp4 stream debug: read box: "dref" entry-count 1
[0xa010520] mp4 stream debug: found Box: stbl size 37525
[0xa010520] mp4 stream debug: found Box: stsd size 161
[0xa010520] mp4 stream debug: found Box: avc1 size 145
[0xa010520] mp4 stream debug: found Box: avcC size 39
[0xa010520] mp4 stream debug: read box: "avcC" version=1 profile=0x42 level=0x15 length size=2 sps=1 pps=1
[0xa010520] mp4 stream debug:          - sps[0] length=15
[0xa010520] mp4 stream debug:          - pps[0] length=5
[0xa010520] mp4 stream debug: found Box: btrt size 20
[0xa010520] mp4 stream warning: unknown box type btrt (incompletely loaded)
[0xa010520] mp4 stream debug: read box: "vide" in stsd 480x270 depth 24
[0xa010520] mp4 stream debug: read box: "stsd" entry-count 1
[0xa010520] mp4 stream debug: found Box: stts size 24
[0xa010520] mp4 stream debug: read box: "stts" entry-count 1
[0xa010520] mp4 stream debug: found Box: stss size 456
[0xa010520] mp4 stream debug: read box: "stss" entry-count 110
[0xa010520] mp4 stream debug: found Box: stsc size 40
[0xa010520] mp4 stream debug: read box: "stsc" entry-count 2
[0xa010520] mp4 stream debug: found Box: stsz size 18420
[0xa010520] mp4 stream debug: read box: "stsz" sample-size 0 sample-count 4600
[0xa010520] mp4 stream debug: found Box: stco size 18416
[0xa010520] mp4 stream debug: read box: "co64" entry-count 4600
[0xa010520] mp4 stream debug: found Box: mdat size 14965064
[0xa010520] mp4 stream debug: skip box: "mdat"
[0xa010520] mp4 stream debug: dumping root Box "root"
[0xa010520] mp4 stream debug: |    + ftyp size 28
[0xa010520] mp4 stream debug: |    + moov size 112397
[0xa010520] mp4 stream debug: |    |    + mvhd size 108
[0xa010520] mp4 stream debug: |    |    + iods size 21
[0xa010520] mp4 stream debug: |    |    + trak size 74465
[0xa010520] mp4 stream debug: |    |    |    + tkhd size 92
[0xa010520] mp4 stream debug: |    |    |    + mdia size 74365
[0xa010520] mp4 stream debug: |    |    |    |    + mdhd size 32
[0xa010520] mp4 stream debug: |    |    |    |    + hdlr size 66
[0xa010520] mp4 stream debug: |    |    |    |    + minf size 74259
[0xa010520] mp4 stream debug: |    |    |    |    |    + smhd size 16
[0xa010520] mp4 stream debug: |    |    |    |    |    + dinf size 36
[0xa010520] mp4 stream debug: |    |    |    |    |    |    + dref size 28
[0xa010520] mp4 stream debug: |    |    |    |    |    |    |    + url  size 12
[0xa010520] mp4 stream debug: |    |    |    |    |    + stbl size 74199
[0xa010520] mp4 stream debug: |    |    |    |    |    |    + stsd size 91
[0xa010520] mp4 stream debug: |    |    |    |    |    |    |    + mp4a size 75
[0xa010520] mp4 stream debug: |    |    |    |    |    |    |    |    + esds size 39
[0xa010520] mp4 stream debug: |    |    |    |    |    |    + stts size 24
[0xa010520] mp4 stream debug: |    |    |    |    |    |    + stsc size 22492
[0xa010520] mp4 stream debug: |    |    |    |    |    |    + stsz size 33164
[0xa010520] mp4 stream debug: |    |    |    |    |    |    + stco size 18420
[0xa010520] mp4 stream debug: |    |    + trak size 37795
[0xa010520] mp4 stream debug: |    |    |    + tkhd size 92
[0xa010520] mp4 stream debug: |    |    |    + mdia size 37695
[0xa010520] mp4 stream debug: |    |    |    |    + mdhd size 32
[0xa010520] mp4 stream debug: |    |    |    |    + hdlr size 66
[0xa010520] mp4 stream debug: |    |    |    |    + minf size 37589
[0xa010520] mp4 stream debug: |    |    |    |    |    + vmhd size 20
[0xa010520] mp4 stream debug: |    |    |    |    |    + dinf size 36
[0xa010520] mp4 stream debug: |    |    |    |    |    |    + dref size 28
[0xa010520] mp4 stream debug: |    |    |    |    |    |    |    + url  size 12
[0xa010520] mp4 stream debug: |    |    |    |    |    + stbl size 37525
[0xa010520] mp4 stream debug: |    |    |    |    |    |    + stsd size 161
[0xa010520] mp4 stream debug: |    |    |    |    |    |    |    + avc1 size 145
[0xa010520] mp4 stream debug: |    |    |    |    |    |    |    |    + avcC size 39
[0xa010520] mp4 stream debug: |    |    |    |    |    |    |    |    + btrt size 20
[0xa010520] mp4 stream debug: |    |    |    |    |    |    + stts size 24
[0xa010520] mp4 stream debug: |    |    |    |    |    |    + stss size 456
[0xa010520] mp4 stream debug: |    |    |    |    |    |    + stsc size 40
[0xa010520] mp4 stream debug: |    |    |    |    |    |    + stsz size 18420
[0xa010520] mp4 stream debug: |    |    |    |    |    |    + stco size 18416
[0xa010520] mp4 stream debug: |    + mdat size 14965064
[0xa0105e8] mp4 demux debug: unrecognized major file specification (mp42).
[0xa0105e8] mp4 demux debug: found 2 tracks
[0xa0105e8] mp4 demux debug: track[Id 0x1] read 4601 chunk
[0xa0105e8] mp4 demux debug: track[Id 0x1] read 8286 samples length:192s
[0xa009168] main input debug: selecting program id=0
[0xa0105e8] mp4 demux debug: adding track[Id 0x1] audio (enable) language undef
[0xa0105e8] mp4 demux debug: track[Id 0x2] read 4600 chunk
[0xa0105e8] mp4 demux debug: track[Id 0x2] read 4600 samples length:191s
[0xa0105e8] mp4 demux debug: adding track[Id 0x2] video (enable) language undef
[0xa0105e8] main demux debug: using demux module "mp4"
[0xa0105e8] main demux debug: TIMER module_need() : 2905.047 ms - Total 2905.047 ms / 1 intvls (Avg 2905.047 ms)
[0xa0105e8] mp4 demux warning: control query 14 unimplemented
[0xa0105e8] mp4 demux warning: DEMUX_GET_FPS unimplemented !!
[0xa009168] main input debug: looking for a subtitle file in /home/timothycbautista/Videos/Youtube/
[0xa011d20] main decoder debug: looking for decoder module: 29 candidates
[0x9d24ca8] qt4 interface debug: IM: Setting an input
[0xa011d20] main decoder debug: TIMER module_need() : 17.370 ms - Total 17.370 ms / 1 intvls (Avg 17.370 ms)
[0xa011d20] main decoder error: no suitable decoder module for fourcc `mp4a'.
VLC probably does not support this sound or video format.
[0xa011d20] main decoder debug: killing decoder fourcc `mp4a', 0 PES in FIFO
[0xa00ba20] main decoder debug: looking for decoder module: 29 candidates
[0xa00ba20] main decoder debug: TIMER module_need() : 0.682 ms - Total 0.682 ms / 1 intvls (Avg 0.682 ms)
[0xa00ba20] main decoder error: no suitable decoder module for fourcc `avc1'.
VLC probably does not support this sound or video format.
[0xa00ba20] main decoder debug: killing decoder fourcc `avc1', 0 PES in FIFO
[0xa009168] main input debug: `/home/timothycbautista/Videos/Youtube/AwkwardRap.mp4' successfully opened
[0xa009168] main input debug: EOF reached
[0xa0105e8] mp4 demux debug: freeing all memory
[0x9d11b18] main playlist debug: finished input
[0xa0105e8] main demux debug: removing module "mp4"
[0xa010520] main stream debug: removing module "stream_filter_record"
[0xa00ade0] main access debug: removing module "access_file"
[0xa009168] main input debug: Program doesn't contain anymore ES
[0x9d11b18] main playlist debug: dead input
[0xa009168] main input debug: thread ended
[0x9d11b18] main playlist debug: changing item without a request (current 0/1)
[0x9d11b18] main playlist debug: nothing to play
[0x9d24ca8] qt4 interface debug: IM: Deleting the input
[0xa009168] main input debug: TIMER input launching for 'AwkwardRap.mp4' : 5329.215 ms - Total 5329.215 ms / 1 intvls (Avg 5329.215 ms)
[0x9c7e140] main libvlc debug: deactivating the playlist
[0x9d11b18] main playlist debug: Deactivate
[0x9d11b18] main playlist debug: saving Media Library to file /home/timothycbautista/.local/share/vlc/ml.xspf
[0x9d11b18] main playlist debug: looking for playlist export module: 1 candidate
[0x9d11b18] main playlist debug: using playlist export module "export"
[0x9d11b18] main playlist debug: TIMER module_need() : 0.609 ms - Total 0.609 ms / 1 intvls (Avg 0.609 ms)
[0x9d11b18] main playlist debug: removing module "export"
[0x9d11b18] main playlist debug: Deactivated
[0x9c7e140] main libvlc debug: removing all services discovery tasks
[0x9c7e140] main libvlc debug: removing all interfaces
[0x9d24ca8] qt4 interface debug: Quitting the Qt4 Interface
[0x9d24ca8] qt4 interface debug: destroying the main Qt4 interface
[0x9d24ca8] qt4 interface debug: Destroying the main interface
[0x9d24ca8] main interface debug: removing module "qt4"
[0x9d1bf08] main interface debug: removing module "signals"
[0x9d1e488] main interface debug: removing module "screensaver"
[0x9d229b0] main interface debug: removing module "inhibit"
[0x9d1d8b8] main interface debug: removing module "hotkeys"
[0x9c7e140] main libvlc debug: removing playlist
[0x9d11b18] main playlist debug: Destroyed
[0x9c7e140] main libvlc debug: TIMER ML Load : Total 120.327 ms / 1 intvls (Avg 120.327 ms)
[0x9c7e140] main libvlc debug: TIMER Items array build : Total 0.139 ms / 2 intvls (Avg 0.070 ms)
[0x9c7e140] main libvlc debug: TIMER ML Dump : Total 0.901 ms / 1 intvls (Avg 0.901 ms)
[0x9c7e140] main libvlc debug: removing stats
[0x9c7e140] main libvlc debug: removing module "memcpymmxext"
[0x9c7e140] main libvlc debug: writing plugins cache /home/timothycbautista/.cache/vlc/plugins-04041e.dat
Interface initialization failed

> 
otherwise try vlc with the -vv (after resetting

I did that, I get the same results. 

Thanks for helping me so far.:D

---

### Post by andrew.46 on 2009-06-20
Hi Sup3r3g0,

> **Sup3r3g0 said:**
> 
```
username@computername:~$ ffmpeg -i /home/username/Videos/Youtube/AwkwardRap.mp4
```


On a sidenote I see that FFmpeg identifies your file as aac sound and h264 video without error. Just to give you a glimmer of hope this probably means that the world's most primitive media player *should* also be able to play the file for you:

```
ffplay /home/username/Videos/Youtube/AwkwardRap.mp4
```

using the path that you provided.

Andrew

---

### Post by Sup3r3g0 on 2009-06-20
Thanks! I was able to play it!

---

### Post by andrew.46 on 2009-06-20
Hi Sup3r3g0,

> **Sup3r3g0 said:**
> Thanks! I was able to play it!

Great news :-). I see you have added Medibuntu to your sources.list which means that MPlayer from the commandline should also play the file with similar syntax:

```
mplayer /home/username/Videos/Youtube/AwkwardRap.mp4
```

as the MPlayer from Medibuntu should support aac and h264. (Mind you in yet another side-note I see that Medibuntu has dropped MPlayer from its Karmic Koala repository presumably because Karmic has a half decent copy of MPlayer now).

However vlc should also play this file. You are using the most recent version:

```
timothycbautista@slackware:~$ vlc -vv /home/timothycbautista/Videos/Youtube/AwkwardRap.mp4
**[COLOR="Purple"]VLC media player 1.0.0-rc3 Goldeneye[/COLOR]**
```

so can I ask where you picked up this version? I ask only as it is definitely not a part of Ubuntu yet and perhaps you have a problem installation of vlc.

All the best,

Andrew

---

### Post by mc4man on 2009-06-20
You should probably play with mplayer though if there's a thread concerning whomever's ppa your using you may wish to post there, vlc should play that file.
(though it appears to be a youtube.flv converted to mp4, if so, the unknown is what or how it was converted

Out of all that debug junk this is the issue
> [0xa0105e8] main demux debug: using demux module [COLOR="Blue"]"mp4"[/COLOR]
0xa011d20] main decoder error: no suitable decoder module for [COLOR="Blue"]fourcc `mp4a'[/COLOR].
main decoder error: no suitable decoder module for[COLOR="Blue"] fourcc `avc1'[/COLOR].



Why vlc is seeing mp4a and avc1 and not opening the proper modules I'm not sure, I have my own rc3 and with same format file it plays fine whether left as a .flv or converted to mp4

as mp4
> [0x81bd508] main demux debug: using demux module [COLOR="Blue"]"mp4"[/COLOR]
[0x81c3020] avcodec decoder debug: libavcodec initialized (interface 0x341e02)
[0x81c3020] avcodec decoder debug: [COLOR="Blue"]ffmpeg codec (H264 - MPEG-4 AVC (part 10)) started[/COLOR]
[0x81c3020] main decoder debug: using decoder module [COLOR="Blue"]"avcodec"[/COLOR]
[0x826a7d8] main decoder debug: using decoder module [COLOR="Blue"]"faad"[/COLOR]


As a .flv
> [0x81bc2c0] avformat demux debug: adding es: video codec = h264
[0x81bc2c0] a[COLOR="Blue"]vformat demux debug: adding es: audio codec = mp4a[/COLOR]
[0x81bc2c0] avformat demux debug: AVFormat supported stream
[0x81bc2c0] avformat demux debug:     - format = flv (FLV format)

[0x81c0d38] avcodec decoder debug: libavcodec initialized (interface 0x341e02)
[0x81c0d38] avcodec decoder debug: ffmpeg codec (H264 - MPEG-4 AVC (part 10)) started
[0x81c0d38] main decoder debug: using decoder module [COLOR="Blue"]"avcodec"[/COLOR]
[0x81fd600] main decoder debug: using decoder module [COLOR="Blue"]"faad"[/COLOR]


So it's either something concerning the file format or conversion to mp4 or a deficiency in the vlc build or your libav*'s
(do you have the unstripped libavformat also?

Edit 
Went ahead and tried your video (Awkward Rap from youtube

ffmpeg shows this (as a .flv) and vlc Rc3 has no issues with the .flv or when 'converted' by ffmpeg to mp4

> doug@doug-laptop:~$ ffmpeg -i awk.flv
FFmpeg version SVN-r19087, Copyright (c) 2000-2009 Fabrice Bellard, et al.
configuration: --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --libdir=${prefix}/lib --shlibdir=${prefix}/lib --bindir=${prefix}/bin --incdir=${prefix}/include/ffmpeg --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir=${prefix}/share/man --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-libamr-nb --enable-libamr-wb --enable-libgsm --enable-libx264 --enable-libtheora --enable-libdc1394 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-avfilter-lavf --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
libavutil 50. 3. 0 / 50. 3. 0
libavcodec 52.30. 2 / 52.30. 2
libavformat 52.34. 0 / 52.34. 0
libavdevice 52. 2. 0 / 52. 2. 0
libavfilter 0. 5. 0 / 0. 5. 0
libswscale 0. 7. 1 / 0. 7. 1
libpostproc 51. 2. 0 / 51. 2. 0
built on Jun 7 2009 05:25:00, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
[h264 @ 0x8072e80]number of reference frames exceeds max (probably corrupt input), discarding one

Seems stream 1 codec frame rate differs from container frame rate: 47.94 (47942/1000) -> 23.98 (24000/1001)
Last message repeated 38 times
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'awk.flv':
Duration: 00:03:09.33, start: 0.000000, bitrate: 632 kb/s
Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
Stream #0.1(und): Video: h264, yuv420p, 480x270 [PAR 1:1 DAR 16:9], 23.98 tbr, 23.97 tbn, 47.94 tbc 

---

