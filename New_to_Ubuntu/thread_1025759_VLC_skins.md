---
title: "VLC skins"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by ozbolt on 2008-12-30
I've changed my VLC skin and played with a couple until I get stucked with this terrible skin, and I cannot switch it off. I've tried removing VLC and then autoremoving everything else, deleting all files in filesystem that had VLC in its name, rebooted and now the same.
When I try to change it this happens:
 ```
ozbolt@ozbolt-desktop:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000404] skins2 interface: skin: Blissta  author: Asim Siddiqui
[00000721] xml xml error: XML parser error (line 1) : failed to load external entity "skin.dtd"

[00000721] xml xml error: XML parser error (line 2) : Validation failed: no DTD found !
[00000404] skins2 interface error: failed to parse /tmp/vlt7h1NF5/default/theme.xml
[00000404] skins2 interface error: error while parsing /tmp/vlt7h1NF5/default/theme.xml
[00000724] xml xml error: XML parser error (line 1) : Document is empty

[00000404] skins2 interface error: failed to parse /usr/share/vlc/skins2/default.vlt



[00000727] xml xml error: XML parser error (line 1) : failed to load external entity "skin.dtd"

[00000727] xml xml error: XML parser error (line 2) : Validation failed: no DTD found !
[00000727] xml xml error: XML parser error (line 2) : attributes construct error

[00000727] xml xml error: XML parser error (line 2) : Couldn't find end of Start Tag ThemeInfo

[00000404] skins2 interface error: failed to parse /tmp/vltBjAc10/theme.xml
[00000404] skins2 interface error: error while parsing /tmp/vltBjAc10/theme.xml
[00000730] xml xml error: XML parser error (line 1) : Document is empty

[00000404] skins2 interface error: failed to parse /home/ozbolt/.vlc-skins/marmor.vlt
```

Same when I try going in default skin.
If anybody knows how to fix this then help.
thanks in advance

---

### Post by fooman on 2008-12-30
try first uninstalling vlc.

after its uninstalled,  open your home directory and in the toolbar, click "view".  put a check next to "show hidden files".  find the .configure folder and open it.  in there should be a folder named "vlc" ...right click on it and choose "move to trash".

reinstall vlc and see if its any better.

hope that helps.

---

### Post by mc4man on 2008-12-30
Easiest way
In a terminal
```

vlc --reset-config
```

---

### Post by PierreDeKat on 2008-12-30
I had a very similar problem with VLC skins awhile back, to the extent that VLC would no longer launch. And deleting the /home/username/.config/vlc folder before reinstalling fixed it for me.

---

### Post by Elfy on 2008-12-30
You can try to run vlc with default config and reset the skins from the settings

```
vlc --reset-config
```

If not the vlc folder on my install is in ~/.config

---

