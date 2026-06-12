---
title: "vlc crashes in jaunty with segmentation fault when changing songs on playlists."
date: 2009-04-23
forum: New to Ubuntu
---

### Post by thebestofall007 on 2009-04-23
i just upgraded to jaunty from intrepid and i am having a problem with vlc 0.9.9a crashing with segmentation fault when i am listening to a multi song playlist (like from a .xspf file) when i change to another song. the terminal output is here:

lou@lou-laptop:~$ vlc
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
Segmentation fault
lou@lou-laptop:~$

this problem also surfaces when i play dvds with vlc. the menu plays, but when the movie starts playing after i hit play, vlc crashes.

---

### Post by Bakon Jarser on 2009-04-23
Hmmmm....somebody has a PPA with vlc 1.0 pre-release.  You could try that.

[http://ubuntuforums.org/showthread.php?t=1111272](http://ubuntuforums.org/showthread.php?t=1111272)

---

### Post by thebestofall007 on 2009-04-23
doesnt work for me. it made vlc not even start. had to revert back to o.9.9a.

---

### Post by jyaan on 2009-07-29
This is a slightly old thread, but I thought I should point out that this issue can probably be resolved by deleting your config files for vlc. They are located in ~/.config/vlc. Just delete that vlc folder. I guess the new version is not compatible with the old config files. This worked for me, at least.

---

### Post by WSmart on 2010-07-25
@jyaan Thanks!  Deleting that config folder worked for me. 

How frustrating though.  Glad I know to look at the log file viewer which made it easy to search on this.  But I wrestled with it for some time before I got there.  Must have crashed vlc a dozen times while trying to watch an hour long MP4 video.  I also had an increase in the CPU usage which was maxing me out and causing the video to skip frames.  I rebooted several times and it wouldn't go away.  

Just got a new vlc version, last week I believe, with my updates.  Might have been a proposed update as I have those turned on.  So as you said, the new didn't like the old.  I'm pretty happy it's fixed!

Thanks again!

Edited typo.

---

