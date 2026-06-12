---
title: "AVI videos shut down"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by AE000 on 2009-06-26
Hi, I can't open AVI videos, the player shuts down inmediately. I'm using Jaunty and I've already added the Medibuntu repositories, I even installed MPlayer but the same happens with it.

Thanks!
Alex.

---

### Post by Villiam on 2009-06-26
Does it happen with all videos? or only with AVIs? Or only specific to a specific AVI file? That will give you clue where is the problem.
Have you tried VLC player. Its a good one.
sudo aptitude update
sudo aptitude install vlc

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by AE000 on 2009-06-26
Hi Villiam, so far I've only noticed it with AVI videos (I've tried with several), I installed VLC as you recommended but it also shuts down right after opening the file.

---

### Post by zeroseven0183 on 2009-06-26
Are there any error message after the player shuts down? How large are the files you're trying to play?

And how about you give us the specs of your machine.

---

### Post by nandemonai on 2009-06-26
Run one of the video players from the terminal and note any error messages that pop up when it crashes.

---

### Post by allenbradley on 2009-06-26
Try playing the file from terminal using vlc (ie) 
```
 vlc <filename> 
```
and see if you get any error messages.

EDIT : Talk about your late replies!

---

### Post by A4- on 2009-06-26
I just upgraded to 9.04 and had the same problem. [This]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") fixed it for me.

---

### Post by allenbradley on 2009-06-26
I did the same thing Tartler recommended and glxgears started running at 200 fps instead of 600. I think the latest update to X.Org adds support for GM965 cards.

---

### Post by AE000 on 2009-06-26
I have 2.5Gb of RAM, I'm using an Intel Pentium 4 CPU at 3GHz with 260Gb free in my hd.
Here's the output of VLC, the avi file is 700Mb:

[INDENT]alejandro@Desktop:~/Escritorio$ vlc 24-Redemption.avi
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "es"
[00000001] main libvlc: Ejecutar vlc con el interfaz por defecto. Usa 'cvlc' para usar vlc sin interfaz.
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82
Fallo de segmentación
alejandro@Desktop:~/Escritorio$ 
[/INDENT]I tried to burn the file to a CD with Brasero but it also shuts down right when I add the video. As with the other players there are no error messages.

---

### Post by zeroseven0183 on 2009-06-26
Are there any special characters on the filename? How long are the filenames of the videos? Seems that the videos are the problems not the players.

---

### Post by Steelmourne on 2009-06-26
The output lists insufficient resources. If you have any effects enabled, disable them. What video card do you have and how much video memory?

Type lspci -vv -nn > hardware.txt into terminal. Then open up the text file and search for vga controller.

---

### Post by AE000 on 2009-06-26
> **zeroseven0183 said:**
> Are there any special characters on the filename? How long are the filenames of the videos? Seems that the videos are the problems not the players.

No special characters and no more than 15 characters on each filename, I've renamed it to "Redemption.avi" and it still closes itself.

---

### Post by AE000 on 2009-06-26
> **Steelmourne said:**
> The output lists insufficient resources. If you have any effects enabled, disable them. What video card do you have and how much video memory?

Type lspci -vv -nn > hardware.txt into terminal. Then open up the text file and search for vga controller.

The visual effects are disabled (and I can't enable them by the way). I have no video card, the motherboard handles the video, it is an Intel D865GBF motherboard, Intel's site says that it uses Dynamic Video Memory Technology to allow the operating system to allocate the video memory ([www.intel.com/support/graphics/intel865g/](www.intel.com/support/graphics/intel865g/)), can this be configured in Ubuntu?

Here's the output of hardware.txt at vga controller:
[INDENT]00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
    Subsystem: Intel Corporation Device [8086:4246]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
    Region 2: I/O ports at ec00 [size=8]
    Capabilities: <access denied>
    Kernel modules: intelfb
[/INDENT]Does that means that it allocated 128M? is that enough?

Thanks!

---

### Post by AE000 on 2009-07-12
I haven't been able to fix this issue, any suggestions will be appreciated.

---

### Post by dandav101 on 2009-07-15
Here's how I fixed it :

- You go into VLC's Tools --> Preferences --> Video Tab and then select x11 video output on the video output field and save. 

I didn't find this out myself, but from this thread : [HERE]("http://ubuntuforums.org/showthread.php?t=1132119")

---

