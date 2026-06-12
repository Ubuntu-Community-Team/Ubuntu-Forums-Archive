---
title: "upgraded to 9.04 tote&amp;VLC crash on open video (without error)"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by mishkin on 2009-04-28
Whenever I open a video It just opens for a sec then disappears. I tryed uninstalling and reinstalling vlc, adding repositories and installng codecs etc

it worked just fine before I upgraded to 9.04 (was running 8.10)

wtf, help!!!

(I only use this comp for watching videos :( )

edit: regular mpeg videos crash it too, but the icons for scene avi and regular mpeg are both loading a preview pic of the video so it's working a bit i guess

---

### Post by jbrown96 on 2009-04-28
Try launching it from a terminal and post the output here. ```
vlc FILE
```

---

### Post by tpalmucci on 2009-04-29
I have the same issue on a fresh install of Jaunty (plus additional codecs, such as non-free, etc). similar issues occur with Totem & VLC. It also occurs with both MPG and WMV files.
Here's the cmd line output:
======================
tomp@tomp-laptop:~/Desktop$ totem movie2.wmv 

/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 169 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
=========================
tomp@tomp-laptop:~/Desktop$ vlc movie2.wmv 
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82
======================

It's the same "insufficient resources for operation" error in each case.
Intel Core2 duo, 2GB ram, 256mb v-ram. 

Thanks in advance for your assistance!

---

### Post by keenlearner on 2009-04-29
I wish I had seen this post before I upgraded yesterday :(

Same problem, every player will crash when my video is opened

Now I am using the mplayer with command line

> mplayer -vo x11 your_music_file_1.mp4 your_music_file_2.mp4

Hope anyone can use that for temporary...

---

### Post by 65_volks on 2009-04-29
> **jbrown96 said:**
> Try launching it from a terminal and post the output here. ```
vlc FILE
```



VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

Totem:


greg@TV:~$ totem /home/greg/Desktop/30.Rock.S03E02.HDTV.XviD-LOL.avi
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 91 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Mplayer:
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.66GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/greg/Desktop/30.Rock.S03E02.HDTV.XviD-LOL.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1044.7 kbps (127.5 kbyte/s)
Clip info:
 Software: transcode-0.6.9
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
GNOME screensaver enabled

Exiting... (Quit)

---

### Post by bug67 on 2009-04-29
My video players (Totem/VLC) don't crash but will not, under any circumstances play DVDs.  I tried following this guide:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

to no avail.  I'm at a loss.  Everything worked fine in Intrepid.

> **jbrown96 said:**
> Try launching it from a terminal and post the output here.

VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000355] main interface error: no interface module matched "screensaver,none"
[00000355] main interface error: no suitable interface module
[00000001] main libvlc error: interface "screensaver,none" initialization failed
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Remote control interface initialized. Type `help' for help.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Can't stat FILE
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[00000360] access_directory access error: FILE: No such file or directory
[00000360] access_file access error: cannot open file FILE (No such file or directory)
[00000358] main input error: open of `FILE' failed: could not create access: no suitable access module

Looks like there's definitely some stuff going on (or NOT going on) but, I'm such a n00b it's goofy!:P

---

### Post by 65_volks on 2009-04-30
> **bug67 said:**
> My video players (Totem/VLC) don't crash but will not, under any circumstances play DVDs.  I tried following this guide:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

to no avail.  I'm at a loss.  Everything worked fine in Intrepid.




libdvdread: Encrypted DVD support unavailable.


:P

bug67,
  this thread is having a different problem you need help with Encrypted DVD support try searching that or start your own thread.

---

### Post by acmarfil31 on 2009-05-15
Same goes for me. Every time I watch AVI or MPG videos, totem and VLC just crashes and goes to kernel panic screen.

I hope our gurus around can shed a light on this. Please help.


Thanks!

acm

---

### Post by stephdl on 2009-05-24
if lspci answer that
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) 

you can try this, it works for me

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by jinjanjaa on 2009-06-12
Same problem  here......

but one interesting phenomenon in my pc is tat the videos which crash normally, play rite when i m listening to songs in rhythmbox. that is wen rhythmbox is on playing my songs i  start the video and LO!! it  works... even dvd movies.....

every1 chk  whether the same happens in ur pc....

---

### Post by krlhc8 on 2009-06-17
I am having the exact same issues, getting all the X11 BadAlloc errors and what not.  Jinjanjaa's tip worked for me.  I opened Rhythmbox and played then song, played the vlc video, then paused the song, and it worked.

---

### Post by jinjanjaa on 2009-06-19
hey every1....
i found the fix. [Here]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") are the details...

---

### Post by Seta_Roja on 2009-06-22
Newbie and I solved it changing the video output in system/preferences/multimedia system selector
(...or something like that: selector de sistemas multimedia in spanish version)

go to video tab and try different complements... In my case Videos don't works in auto mode, but it worked with X window system (w/o Xv).

And after that to use VLC, configuring it with the proper output in audio and video, and no-auto mode...


:popcorn: yepa!

---

