---
title: "DVDs"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by matt2008 on 2009-08-09
i did some searching on here and install everything I need. I think. But when I open a DVD in VLC it plays for a second and closes, the same thing happens in The movie player. Any Ideas?

---

### Post by garikaib on 2009-08-09
Which version of Ubuntu are you running?

---

### Post by frt975 on 2009-08-09
Install Restricted Extras

---

### Post by cariboo on 2009-08-09
It looks like you don't have libdvdcss2 installed. You need  to enable the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories. Follow the instructions for your version of Ubuntu.

---

### Post by matt2008 on 2009-08-09
Im running 9.04 and Installed Restricted extras, It still closes right after it starts to load the dics

---

### Post by wojox on 2009-08-09
Install the libraries like Caribio said.

---

### Post by matt2008 on 2009-08-09
I already installed those with no luck

---

### Post by oldos2er on 2009-08-09
Have you installed libdvdcss2? It's in the Medibuntu repository, [http://medibuntu.org](http://medibuntu.org)

---

### Post by matt2008 on 2009-08-09
yeah I already installed it

---

### Post by oldos2er on 2009-08-09
With the DVD in your DVD drive, type **vlc** in a terminal, and post the output here.

---

### Post by matt2008 on 2009-08-09
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

---

### Post by oldos2er on 2009-08-09
Which version of Ubuntu are you running?

---

