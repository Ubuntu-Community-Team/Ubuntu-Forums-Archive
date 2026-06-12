---
title: "VLC crashes on playing video"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by adnani on 2009-05-02
vlc player opens for a second and closes when I try playing a video. I am using Ubuntu 9.04
Following message is comes on running in terminal


sanjay@sanjay-desktop:~$ vlc ~/Desktop/TinTin - Shooting Star.divxVLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat /home/sanjay/Desktop/TinTin
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[00000418] access_directory access error: /home/sanjay/Desktop/TinTin: No such file or directory
[00000418] access_file access error: cannot open file /home/sanjay/Desktop/TinTin (No such file or directory)
[00000412] main input error: open of `/home/sanjay/Desktop/TinTin' failed: could not create access: no suitable access module
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat -
No such file or directory
libdvdnav: vm: failed to open/read the DVD

---

### Post by jerrrys on 2009-05-05
could not create access: no suitable access module
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat -

this may help...

[http://www.google.com/search?q=vlc+player+ubuntu+9.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=vlc+player+ubuntu+9.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

