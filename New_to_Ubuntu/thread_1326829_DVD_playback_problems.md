---
title: "DVD playback problems"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by river226 on 2009-11-14
Hi, I have set up a new ubuntu 9.10 computer, and I have tried to set up DVD playback. I installed the codecs, practically everyone I can find, and I tried to play a DVD video. I found after this, that every program I tried crashed before it got to playing the Video, I tried Kaffeine, totem, VLC, Dragon Player, and any others I could find, all with the same issue. 
Any suggestions?

---

### Post by Steffen.phx on 2009-11-14
You said you have already installed all required codecs, but when you want to playback commercial movies, you have to keep in mind that these are normally encrypted. 

So you have to install these packet libdvdcss2 to run them, so please make sure you have installed this.

I think this could be the only reason, when every player doesn't start your movie. Please inform us if it helped.

Have a nice weekend :popcorn:

---

### Post by ghostborg on 2009-11-14
All I install are the Mediabuntu and ubuntu-restricted-extras.

Mediabuntu
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Use the code to add the repository
then Playing Encrypted DVDs then the codecs for the type of system you have 32 or 64 bit.

I then use Synaptic to install ubuntu-restricted-extras.

You could try ripping the dvd to your HD to see if that eliminates any problems to help you trouble -shoot.

---

### Post by sandyd on 2009-11-14
offering shortcut...
```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update[FONT=Verdana]
sudo apt-get install w32codecs libdvdcss2 libdvdread3 libdvdread4 lame0 gstreamer0.10-ffmpeg gstreamer-0.10-fluendo-mp3 gstreamer-plugins-ugly libfaac0 libfaad0 ubuntu-restricted-extras
[/FONT]
```p.s. hint: if your installing ubuntu-restricted-extras, use the tab key to accept the EULA. A lot of newbies get stuck at this point.
[FONT=Verdana] replace w32codecs with w64codecs if using x64 bit.

p.s. if your ripping using handbrake, handbrake currently does not work on ubuntu 9.10 due to a GTK update.
[/FONT]

---

### Post by JohnAStebbins on 2009-11-15
> p.s. if your ripping using handbrake, handbrake currently does not work on ubuntu 9.10 due to a GTK update.
Not entirely true.  The latest snapshot is built specifically for karmic.
[http://forum.handbrake.fr/viewtopic.php?f=6&t=12842](http://forum.handbrake.fr/viewtopic.php?f=6&t=12842)

---

### Post by river226 on 2009-11-15
Neither suggestion worked, and ripping isn't really practical for my purposes. Any other ideas?

---

### Post by SPazzo on 2009-11-15
This isn't really a suggestion but do you think it could be the DVD drive itself?  Have you tried playing a CD or booting from a Live CD or something?

---

### Post by river226 on 2009-11-15
no it's not the drive, turns out since i haven't updated it for a while, not spending any real time on it, and focusing my attention elsewhere, that was the problem. got playback now, thanks for the help

---

### Post by fabiodasoghe on 2009-12-07
I have Ubuntu 9.10 on x64 and I had to modify the last command issued in the shell.

What worked for me is:

```

sudo apt-get install w64codecs libdvdcss2 libdvdread3 libdvdread4 gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-ugly libfaac0 libfaad0 ubuntu-restricted-extras

```

There are two mispelled packages (fluendo and ugly) and one package not valid anymore (lame0).

Repeat: this worked for me, maybe some Ubuntu-guru (not me!) could explain why...

Hope this help.

Cheers, and thank you for you suggestions, now I can playback dvds on my Karmic Koala! ;-)

---

### Post by PetteriP on 2009-12-08
Happy for you guys who got it working.
I however did not. I'm running Xubuntu 9.10, istalled Medibuntu, w32codecs, all the things actually mentioned in this thread. Also checked the region (which was wrong) and corrected that.
VLC and Movie Player both fail to open DVD. The opening screen pops up for just an instant and then disappears and the programs shut down.

Output of "vlc -vv" - when I try to open a disk - is:
```
pee@Chisum:~/Desktop$ vlc -vv
VLC media player 1.0.2 Goldeneye
[0x9898140] main libvlc debug: VLC media player - version 1.0.2 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x9898140] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--disable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1ubuntu2' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=xulrunner-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-x264' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--disable-fluidsynth' '--disable-kate' '--disable-mtp' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x9898140] main libvlc debug: translation test: code is "C"
[0x9898140] main libvlc debug: checking plugin modules
[0x9898140] main libvlc debug: loading plugins cache file /home/pee/.cache/vlc/plugins-04041e.dat
[0x9898140] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x9898140] main libvlc debug: module bank initialized (375 modules)
[0x9898140] main libvlc debug: opening config file (/home/pee/.config/vlc/vlcrc)
[0x9898140] main libvlc debug: No Media Player is running. Continuing normally.
[0x9898140] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT FPU 
[0x9898140] main libvlc debug: looking for memcpy module: 3 candidates
[0x9898140] main libvlc debug: using memcpy module "memcpymmxext"
[0x992f198] main input debug: Creating an input for 'Media Library'
[0x992f198] main input debug: Input is a meta file: disabling unneeded options
[0x992f198] main input debug: using timeshift granularity of 50 MBytes
[0x992f198] main input debug: using timeshift path '/tmp'
[0x992f198] main input debug: `file/xspf-open:///home/pee/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/pee/.local/share/vlc/ml.xspf'
[0x992f198] main input debug: creating demux: access='file' demux='xspf-open' path='/home/pee/.local/share/vlc/ml.xspf'
[0x9930a90] main demux debug: looking for access_demux module: 1 candidate
[0x9930a90] main demux warning: no access_demux module matching "file" could be loaded
[0x9930a90] main demux debug: TIMER module_need() : 55.286 ms - Total 55.286 ms / 1 intvls (Avg 55.286 ms)
[0x992f198] main input debug: creating access 'file' path='/home/pee/.local/share/vlc/ml.xspf'
[0x993ea80] main access debug: looking for access module: 3 candidates
[0x993ea80] access_file access debug: opening file `/home/pee/.local/share/vlc/ml.xspf'
[0x993ea80] main access debug: using access module "access_file"
[0x993ea80] main access debug: TIMER module_need() : 72.151 ms - Total 72.151 ms / 1 intvls (Avg 72.151 ms)
[0x993eb68] main stream debug: Using AStream*Stream
[0x993eb68] main stream debug: pre buffering
[0x993eb68] main stream debug: received first data after 0 ms
[0x993eb68] main stream debug: pre-buffering done 296 bytes in 0s - 2535 kbytes/s
[0x993f2a0] main stream debug: looking for stream_filter module: 4 candidates
[0x993f2a0] main stream debug: TIMER module_need() : 78.018 ms - Total 78.018 ms / 1 intvls (Avg 78.018 ms)
[0x9941428] main stream debug: looking for stream_filter module: 1 candidate
[0x9941428] main stream debug: using stream_filter module "stream_filter_record"
[0x9941428] main stream debug: TIMER module_need() : 1.483 ms - Total 1.483 ms / 1 intvls (Avg 1.483 ms)
[0x992f198] main input debug: creating demux: access='file' demux='xspf-open' path='/home/pee/.local/share/vlc/ml.xspf'
[0x99419f8] main demux debug: looking for demux module: 1 candidate
[0x99419f8] playlist demux debug: using XSPF playlist reader
[0x99419f8] main demux debug: using demux module "playlist"
[0x99419f8] main demux debug: TIMER module_need() : 2.046 ms - Total 2.046 ms / 1 intvls (Avg 2.046 ms)
[0x992f198] main input debug: `file/xspf-open:///home/pee/.local/share/vlc/ml.xspf' successfully opened
[0x9941b68] main xml debug: looking for xml module: 2 candidates
[0x9941b68] main xml debug: using xml module "xtag"
[0x9941b68] main xml debug: TIMER module_need() : 35.191 ms - Total 35.191 ms / 1 intvls (Avg 35.191 ms)
[0x99419f8] playlist demux debug: parsed 0 tracks successfully
[0x9941b68] main xml debug: removing module "xtag"
[0x992f198] main input debug: EOF reached
[0x99419f8] main demux debug: removing module "playlist"
[0x9941428] main stream debug: removing module "stream_filter_record"
[0x993ea80] main access debug: removing module "access_file"
[0x992f198] main input debug: TIMER input launching for 'Media Library' : 367.173 ms - Total 367.173 ms / 1 intvls (Avg 367.173 ms)
[0x992e208] main playlist debug: Activated
[0x992f198] main interface debug: looking for interface module: 1 candidate
[0x992f198] main interface debug: using interface module "hotkeys"
[0x992f198] main interface debug: TIMER module_need() : 19.838 ms - Total 19.838 ms / 1 intvls (Avg 19.838 ms)
[0x992f198] main interface debug: thread started
[0x992f198] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x992f820] main interface debug: looking for interface module: 1 candidate
[0x992e208] main playlist debug: rebuilding array of current - root Playlist
[0x992e208] main playlist debug: rebuild done - 0 items, index -1
[0x992f820] main interface debug: using interface module "dbus"
[0x992f820] main interface debug: TIMER module_need() : 29.585 ms - Total 29.585 ms / 1 intvls (Avg 29.585 ms)
[0x992f820] main interface debug: thread started
[0x992f820] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x993c758] main interface debug: looking for interface module: 1 candidate
[0x993c758] main interface debug: using interface module "inhibit"
[0x993c758] main interface debug: TIMER module_need() : 24.187 ms - Total 24.187 ms / 1 intvls (Avg 24.187 ms)
[0x993c758] main interface debug: thread started
[0x993c758] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x99300d0] main interface debug: looking for interface module: 1 candidate
[0x99300d0] main interface debug: using interface module "screensaver"
[0x99300d0] main interface debug: TIMER module_need() : 1.448 ms - Total 1.448 ms / 1 intvls (Avg 1.448 ms)
[0x99300d0] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x99300d0] main interface debug: thread started
[0x993f4e8] main interface debug: looking for interface module: 1 candidate
[0x993f4e8] main interface debug: using interface module "signals"
[0x993f4e8] main interface debug: TIMER module_need() : 1.717 ms - Total 1.717 ms / 1 intvls (Avg 1.717 ms)
[0x993f4e8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x993f4e8] main interface debug: thread started
[0x993f4e8] main interface debug: thread ended
[0x993f038] main interface debug: looking for interface module: 0 candidates
[0x993f038] main interface error: no interface module matched "globalhotkeys,none"
[0x993f038] main interface debug: TIMER module_need() : 33.957 ms - Total 33.957 ms / 1 intvls (Avg 33.957 ms)
[0x993f038] main interface error: no suitable interface module
[0x9898140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9898140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x993f0a0] main interface debug: looking for interface module: 4 candidates
[0x993f0a0] qt4 interface debug: Error while initializing qt-specific localization
[0x993f0a0] main interface debug: using interface module "qt4"
[0x993f0a0] main interface debug: TIMER module_need() : 2748.909 ms - Total 2748.909 ms / 1 intvls (Avg 2748.909 ms)
[0x993f0a0] main interface debug: thread started
[0x993f0a0] main interface debug: thread ended
[0x993f0a0] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x992e208] main playlist debug: adding item `dvd:///dev/sr0' ( dvd:///dev/sr0 )
[0x993f0a0] qt4 interface debug: Adding a new MRL to recent ones: dvd:///dev/sr0
[0x992e208] main playlist debug: rebuilding array of current - root Playlist
[0x992e208] main playlist debug: rebuild done - 1 items, index -1
[0x992e208] main playlist debug: processing request item dvd:///dev/sr0 node null skip 0
[0x992e208] main playlist debug: resyncing on dvd:///dev/sr0
[0x992e208] main playlist debug: dvd:///dev/sr0 is at 0
[0x992e208] main playlist debug: starting new item
[0x992e208] main playlist debug: creating new input thread
[0x9aec9e8] main input debug: Creating an input for 'dvd:///dev/sr0'
[0x9aec9e8] main input debug: thread (input) created at priority 10 (input/input.c:230)
[0x9aec9e8] main input debug: thread started
[0x9aec9e8] main input debug: using timeshift granularity of 50 MBytes
[0x9aec9e8] main input debug: using timeshift path '/tmp'
[0x9aec9e8] main input debug: `dvd:///dev/sr0' gives access `dvd' demux `' path `/dev/sr0'
[0x9aec9e8] main input debug: creating demux: access='dvd' demux='' path='/dev/sr0'
[0x9af3e28] main demux debug: looking for access_demux module: 2 candidates
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
[0x993f0a0] qt4 interface debug: IM: Setting an input
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x993f0a0] qt4 interface debug: Updating the geometry
libdvdnav: DVD Title: BLACK_LABEL_SOCIETY
libdvdnav: DVD Serial Number: 34e76848
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/pee/.dvdnav/BLACK_LABEL_SOCIETY.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000135
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0001946a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0003d14e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003de051
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003de10c
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
[0x9af3e28] dvdnav demux debug: trying to go to dvd menu
[0x9af3e28] main demux debug: using access_demux module "dvdnav"
[0x9af3e28] main demux debug: TIMER module_need() : 3805.457 ms - Total 3805.457 ms / 1 intvls (Avg 3805.457 ms)
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x993f0a0] qt4 interface debug: Title 6
[0x993f0a0] qt4 interface debug: Chapter: 7
[0x9aec9e8] main input debug: `dvd:///dev/sr0' successfully opened
[0x9af3e28] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[0x9aec9e8] main input error: ES_OUT_RESET_PCR called
[0x9af3e28] dvdnav demux debug: DVDNAV_VTS_CHANGE
[0x9af3e28] dvdnav demux debug:      - vtsN=1
[0x9af3e28] dvdnav demux debug:      - domain=8
[0x9aec9e8] main input error: ES_OUT_RESET_PCR called
[0x9af3e28] dvdnav demux debug: DVDNAV_CELL_CHANGE
[0x9af3e28] dvdnav demux debug:      - cellN=1
[0x9af3e28] dvdnav demux debug:      - pgN=1
[0x9af3e28] dvdnav demux debug:      - cell_length=189000
[0x9af3e28] dvdnav demux debug:      - pg_length=189000
[0x9af3e28] dvdnav demux debug:      - pgc_length=9294000
[0x9af3e28] dvdnav demux debug:      - cell_start=0
[0x9af3e28] dvdnav demux debug:      - pg_start=0
[0x9af3e28] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[0x9af3e28] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[0x9af3e28] dvdnav demux debug:      - physical_wide=0
[0x9af3e28] dvdnav demux debug:      - physical_letterbox=1
[0x9af3e28] dvdnav demux debug:      - physical_pan_scan=0
[0x9af3e28] dvdnav demux debug: buttonUpdate not done b=1 t=0
[0x9aec9e8] main input debug: selecting program id=0
[0x9aefde0] main decoder debug: looking for decoder module: 31 candidates
[0x993f0a0] qt4 interface debug: New caching: 0
[0x993f0a0] qt4 interface debug: New caching: 0
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x9aefde0] avcodec decoder debug: libavcodec initialized (interface 0x341400)
[0x9aefde0] main decoder debug: using decoder module "spudec"
[0x9aefde0] main decoder debug: TIMER module_need() : 1480.543 ms - Total 1480.543 ms / 1 intvls (Avg 1480.543 ms)
[0x9b14198] main packetizer debug: looking for packetizer module: 21 candidates
[0x9b14198] main packetizer debug: using packetizer module "spudec"
[0x9b14198] main packetizer debug: TIMER module_need() : 188.405 ms - Total 188.405 ms / 1 intvls (Avg 188.405 ms)
[0x9aefde0] main decoder debug: thread started
[0x9aefde0] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:315)
[0x9aefde0] spudec decoder debug: invalid starting packet (size < 4 or pts <=0)
[0x9aefde0] spudec decoder debug: spu size: 0, i_pts: 0 i_buffer: 128
[0x9af3e28] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[0x9af3e28] dvdnav demux debug:      - physical=0
[0x9aec9e8] main input debug: Buffering 0%
[0x9af3e28] dvdnav demux debug: buttonUpdate not done b=1 t=0
[0x9aec9e8] main input debug: Buffering 0%
[0x9b1c788] main decoder debug: looking for decoder module: 31 candidates
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x993f0a0] qt4 interface debug: New caching: 0
[0x993f0a0] qt4 interface debug: New caching: 0
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x9b1c788] main decoder debug: using decoder module "libmpeg2"
[0x9b1c788] main decoder debug: TIMER module_need() : 32.990 ms - Total 32.990 ms / 1 intvls (Avg 32.990 ms)
[0x9b1c788] main decoder debug: thread started
[0x9b1c788] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:315)
[0x9af3e28] dvdnav demux debug: buttonUpdate not done b=1 t=0
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x9b1c788] libmpeg2 decoder debug: 720x480 (display 720,480), aspect 768000, sar 0:0, 29.971 fps
[0x9aec9e8] main input debug: no usable vout present, spawning one
[0x9b164e8] main spu text debug: looking for text renderer module: 2 candidates
[0x9aec9e8] main input debug: Buffering 1%
[0x9aec9e8] main input debug: Buffering 1%
[0x9aec9e8] main input debug: idx1=-1(??) idx2=-1(??)
[0x9aec9e8] main input debug: Buffering 2%
[0x9aec9e8] main input debug: Buffering 2%
[0x9aec9e8] main input debug: Buffering 3%
[0x993f0a0] qt4 interface debug: New caching: 3
[0x993f0a0] qt4 interface debug: New caching: 3
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x9aec9e8] main input debug: Buffering 3%
[0x9aec9e8] main input debug: Buffering 4%
[0x9aec9e8] main input debug: Buffering 4%
[0x9aec9e8] main input debug: Buffering 5%
[0x9aec9e8] main input debug: Buffering 5%
[0x9aec9e8] main input debug: Buffering 6%
[0x9aec9e8] main input debug: Buffering 7%
[0x9aec9e8] main input debug: Buffering 7%
[0x9aec9e8] main input debug: Buffering 8%
[0x9aec9e8] main input debug: Buffering 8%
[0x9aec9e8] main input debug: Buffering 9%
[0x9aec9e8] main input debug: Buffering 9%
[0x9aec9e8] main input debug: Buffering 10%
[0x9aec9e8] main input debug: Buffering 10%
[0x9aec9e8] main input debug: Buffering 11%
[0x9aec9e8] main input debug: Buffering 11%
[0x9aec9e8] main input debug: Buffering 12%
[0x9aec9e8] main input debug: Buffering 13%
[0x9aec9e8] main input debug: Buffering 13%
[0x9aec9e8] main input debug: Buffering 14%
[0x9aec9e8] main input debug: Buffering 14%
[0x9aec9e8] main input debug: Buffering 15%
[0x9aec9e8] main input debug: Buffering 15%
[0x9aec9e8] main input debug: Buffering 16%
[0x9aec9e8] main input debug: Buffering 16%
[0x9aec9e8] main input debug: Buffering 17%
[0x9aec9e8] main input debug: Buffering 17%
[0x9aec9e8] main input debug: Buffering 18%
[0x9aec9e8] main input debug: Buffering 18%
[0x9aec9e8] main input debug: Buffering 19%
[0x9aec9e8] main input debug: Buffering 20%
[0x9aec9e8] main input debug: Buffering 20%
[0x9aec9e8] main input debug: Buffering 21%
[0x9aec9e8] main input debug: Buffering 21%
[0x9aec9e8] main input debug: Buffering 22%
[0x9aec9e8] main input debug: Buffering 22%
[0x9aec9e8] main input debug: Buffering 23%
[0x9aec9e8] main input debug: Buffering 23%
[0x9aec9e8] main input debug: Buffering 24%
[0x993f0a0] qt4 interface debug: New caching: 24
[0x993f0a0] qt4 interface debug: New caching: 24
[0x9aec9e8] main input debug: Buffering 24%
[0x9aec9e8] main input debug: Buffering 25%
[0x9aec9e8] main input debug: Buffering 26%
[0x9aec9e8] main input debug: Buffering 26%
[0x9aec9e8] main input debug: Buffering 27%
[0x9aec9e8] main input debug: Buffering 27%
[0x9aec9e8] main input debug: Buffering 28%
[0x9aec9e8] main input debug: Buffering 28%
[0x9aec9e8] main input debug: Buffering 29%
[0x9aec9e8] main input debug: Buffering 29%
[0x9aec9e8] main input debug: Buffering 30%
[0x9aec9e8] main input debug: Buffering 30%
[0x9aec9e8] main input debug: Buffering 31%
[0x9aec9e8] main input debug: Buffering 31%
[0x9aec9e8] main input debug: Buffering 32%
[0x9aec9e8] main input debug: Buffering 33%
[0x9aec9e8] main input debug: Buffering 33%
[0x9aec9e8] main input debug: Buffering 34%
[0x9aec9e8] main input debug: Buffering 34%
[0x9aec9e8] main input debug: Buffering 72%
[0x9b6d3a8] main decoder debug: looking for decoder module: 31 candidates
[0x9b6d3a8] main decoder debug: using decoder module "a52"
[0x9b6d3a8] main decoder debug: TIMER module_need() : 1.290 ms - Total 1.290 ms / 1 intvls (Avg 1.290 ms)
[0x9b6d3a8] main decoder debug: thread started
[0x9b6d3a8] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:315)
[0x9aec9e8] main input debug: Buffering 80%
[0x9aec9e8] main input debug: Stream buffering done (344 ms in 196 ms)
[0x9b6d3a8] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0x9b5e958] main generic debug: thread started
[0x993f0a0] qt4 interface debug: New caching: 100
[0x993f0a0] qt4 interface debug: New caching: 100
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x9b5e958] main generic debug: thread (fontlist builder) created at priority 0 (freetype.c:475)
[0x9b164e8] freetype spu text debug: using fontsize: 2
[0x9b164e8] main spu text debug: using text renderer module "freetype"
[0x9b164e8] main spu text debug: TIMER module_need() : 194.631 ms - Total 194.631 ms / 1 intvls (Avg 194.631 ms)
[0x9b85ab0] main scale debug: looking for video filter2 module: 17 candidates
[0x9b5e958] freetype generic debug: Building font database...
[0x9b85ab0] swscale scale debug: 32x32 chroma: YUVA -> 16x16 chroma: YUVA with scaling using Bicubic (good quality)
[0x9b85ab0] main scale debug: using video filter2 module "swscale"
[0x9b85ab0] main scale debug: TIMER module_need() : 171.860 ms - Total 171.860 ms / 1 intvls (Avg 171.860 ms)
[0x9b84620] main scale debug: looking for video filter2 module: 17 candidates
[0x9b5e958] freetype generic debug: Finished building font database.
[0x9b5e958] freetype generic debug: Took 87358 microseconds
[0x9b5e958] main generic debug: thread ended
[0x9b84620] yuvp scale debug: YUVP to YUVA converter
[0x9b84620] main scale debug: using video filter2 module "yuvp"
[0x9b84620] main scale debug: TIMER module_need() : 437.385 ms - Total 437.385 ms / 1 intvls (Avg 437.385 ms)
[0x9b17ca8] main video output debug: window size: 853x480
[0x9b17ca8] main video output debug: looking for video output module: 6 candidates
[0x9b17ca8] xvideo video output debug: adaptor 0, port 68, format 0x32315659 (YV12) planar
[0x9c263a8] main window debug: looking for xwindow module: 3 candidates
[0x9c263a8] qt4 window debug: requesting video...
[0x993f0a0] qt4 interface debug: Video was requested -1, -1
[0x993f0a0] qt4 interface debug: Video is resizing to: 853 480
[0x993f0a0] qt4 interface debug: Updating the geometry
[0x9c263a8] main window debug: using xwindow module "qt4"
[0x9c263a8] main window debug: TIMER module_need() : 549.414 ms - Total 549.414 ms / 1 intvls (Avg 549.414 ms)
QPainter::begin: Paint device returned engine == 0, type: 1
[0x9b17ca8] xvideo video output debug: XShm video extension v1.1 (with pixmaps, opcode: 139)
QPainter::begin: Paint device returned engine == 0, type: 1
[0x9b17ca8] xvideo video output debug: Window manager supports NetWM
[0x9b17ca8] xvideo video output debug: Window manager supports _NET_WM_STATE_ABOVE
[0x9b17ca8] xvideo video output debug: Window manager supports _NET_WM_STATE_BELOW
[0x9b17ca8] xvideo video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[0x9b17ca8] main video output debug: using video output module "xvideo"
[0x9b17ca8] main video output debug: TIMER module_need() : 1406.619 ms - Total 1406.619 ms / 1 intvls (Avg 1406.619 ms)
[0x9b17ca8] main video output debug: Deinterlacing available
[0x9b17ca8] main video output debug: got 16 direct buffer(s)
[0x9b17ca8] main video output debug: pic render sz 720x480, of (0,0), vsz 720x480, 4cc I420, ar 16:9, sar 32:27, msk r0x0 g0x0 b0x0
[0x9b17ca8] main video output debug: pic in sz 720x480, of (0,0), vsz 720x480, 4cc I420, ar 16:9, sar 32:27, msk r0x0 g0x0 b0x0
[0x9b17ca8] main video output debug: pic out sz 720x480, of (0,0), vsz 720x480, 4cc I420, ar 16:9, sar 32:27, msk r0x0 g0x0 b0x0
[0x9b17ca8] main video output debug: direct render, mapping render pictures 0-14 to system pictures 1-15
[0x9b1c788] main decoder warning: dts != current_pts (-247265)
[0x9aec9e8] main input debug: creating aout
[0x9aa70e8] main audio output debug: looking for audio output module: 4 candidates
[0x9b17ca8] qt4 video output debug: Qt: Entering Fullscreen
[0x9b1c788] main decoder warning: backward_pts != current_pts (-33367)
[0x9b1c788] main decoder debug: End of video preroll
[0x9b1c788] main decoder debug: Received first picture
[0x9b164e8] freetype spu text debug: using fontsize: 30
[0x9aa70e8] pulse audio output: No. of Audio Channels: 2
[0x9b47fb8] main blend debug: looking for video blending module: 1 candidate
[0x9b47fb8] blend blend debug: chroma: YUVA -> I420
[0x9b47fb8] main blend debug: using video blending module "blend"
[0x9b47fb8] main blend debug: TIMER module_need() : 26.399 ms - Total 26.399 ms / 1 intvls (Avg 26.399 ms)
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  103
  Current serial number in output stream:  104
```
...and here VLC shuts down.
There is something about insufficient resources in the end... Wonder what that is all about!

Sorry to mess up this nice and solved thread ;)

---

