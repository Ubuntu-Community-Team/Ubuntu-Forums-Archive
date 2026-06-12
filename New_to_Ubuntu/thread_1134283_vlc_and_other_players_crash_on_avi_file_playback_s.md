---
title: "vlc and other players crash on avi file playback start"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by ivanvajar on 2009-04-23
While trying out SuperUbuntu in LiveCD mode, all movie players crash when I start the movie. This particular SuperUbuntu is Interpid Ibex based distro. Any idea?

---

### Post by SuperSonic4 on 2009-04-23
Did you install the codecs?

---

### Post by ivanvajar on 2009-04-23
All codecs are installed. Complete gStreamer, java and flash are installed.

---

### Post by ivanvajar on 2009-04-25
Bump...

---

### Post by kwacka on 2009-04-25
Open terminal and type in 'vlc'.

Do you get any error codes?

---

### Post by canadastitan on 2009-04-25
> **kwacka said:**
> Open terminal and type in 'vlc'.

Do you get any error codes?

I have the exact same problem..
Ever since I upgraded to 9.04 I can not play any .avi files with any media player..I have tried MPlayer ,Xine ,VLC ,Movie Player,Kaffiene ,Dragon Player ,KMplayer..
All the players will start then crash and close almost immediately..??
I suspect it is some kind of bug in 9.04..!!
I tried typing vic in terminal and got message it was not installed so I installed that also and still get the same results with the media players..
all but 2 of the media players crash and close but both Dragon Player and KMplayer will run with a black screen and play the audio only..??
I have installed all the dependencies for all these media players including the restricted ones that are available..I still can not play any .avi video

---

### Post by kwacka on 2009-04-25
When starting (e.g.) VLC from a terminal do you get any error messages?

---

### Post by canadastitan on 2009-04-25
> **kwacka said:**
> When starting (e.g.) VLC from a terminal do you get any error messages?

this is what i get in terminal
dale@Titan:~$ vlc
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
dale@Titan:~$ 
and the vlc player will start but as soon as it opens the selected .avi file it crashes and closes also

---

### Post by kwacka on 2009-04-25
> **canadastitan said:**
> this is what i get in terminal
dale@Titan:~$ vlc
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team

[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)


Suggests that there are problems with your video or video drivers.

What do you have?

---

### Post by canadastitan on 2009-04-25
My computer is a Dell Optiplex GX270
It did require special video drivers for win xp pro, but it all worked fine with ubuntu 7.10, 8.04, 8.10...this problem only started when I upgraded to 9.04

The driver for windows xp pro was..............

 Video:Intel 845 G/GL Integrated Video, Intel Grantsdale G Integrated Video, Springdale G Integrated Video Driver

Version    : A00

OEM Name   : Intel

OEM Ver    : 6.14.10.3762

Computers  : Dimension - 4500S, 4500C, 2300, 2300C, 2350, 4590T, 2400C, 4600C;

OptiPlex - SX270 / SX270N, GX260, 160L, 170L, GX270 / GX270N, SX260, GX60
.........................................................................
I have the set up.exe file for windows  somewhere that i got from dell long ago,but that is for a windows based computer and I now run Linux exclusivly..!!
Is this video driver or an updated video driver available for ubuntu 9.04..???

---

### Post by ivanvajar on 2009-04-26
Sorry I didn't reply sooner. This has something to do with drivers, I'm almost sure. Under PCLinux everything works fine. With Sabayon there is flickering on video playback and it can't be solved by changing the video output plugin. Super Ubuntu uses Medibuntu repositories and drivers are provided by them. Now, the machine I'm talking about is not mine. It's friend's Toshiba Sattelite with ATI Radeon (I don't remember what) which I don't have with me at this time. It was supprise that everything else worked just fine.

---

### Post by ellgor on 2009-04-26
Hi, 

If you are still having problems try this:

Goto>System>Preferences>Multimedia Systems Selector (it may not be enabled in your menu, enable if not)
Choose Video, under default output change this to X Window System (No Xv), it may need a reboot to take effect, hope this helps.

Regards, Ellgor.

---

### Post by canadastitan on 2009-04-26
Thanks Ellgor
I made that change from auto detect and now I can play video with movie player
The other media players will not work though

---

### Post by canadastitan on 2009-04-26
I do not realy think it is a problem with my video drivers as i have found a program that will play the .avi files..!!
the program is FF video convertor (WinFF)..
If I add the .avi file into WinFF then play it with it's FFplay,then it will play the video correctly with slight audio problems..but yet all the other media players will not work for me at all
..I suspect there is some kind of difference between ubuntu 9.04 and its earlier version's,as all the earlier version's will play .avi video correctly with all of the media player's...
..This problem only started when I upgraded from 8.10 to 9.04

---

### Post by gtarabat on 2009-05-06
Hello.

I have the same problem as [canadastitan]("http://www.uluga.ubuntuforums.org/member.php?u=539405"). After upgrade from 8.10 to 9.04 I cannot play avi and mpeg files.  Vlc crashes immediately at startup and Mplayer plays only sound.
Before the upgrade everything was OK.

If anybody has a solution...
Thanks a lot.

---

### Post by forteller on 2009-05-11
I have the same problem (except that I'm pretty sure that I could open avi's in VLC in 9.04 for a while, but suddenly it started crashing VLC. Not 100% sure, though).

A bad workaround is to open VLC first, and then drag the .avi onto it. This is cumbersome, but works for me.

---

### Post by gtarabat on 2009-05-20
Thanks for the reply. The problem remains. Vlc always crashes. 

I can't find any solution.](*,)

---

### Post by j_dolu on 2009-05-26
I have the same problem. After upgrade from ubuntu 810 to 904, all video player could not play any video file. All suddenly crash on opening any video file. No error found.
I try to do fresh install kubuntu 904 and install all video codecs. Dragon player did not crash on opening video file but it only show blue window. I try install VLC, it still crash on opening video file.

Any suggestion on this?

---

### Post by fxb on 2009-05-26
I'm having the same problem with VLC in Ubuntu 8.10 w/ 2.6.27-14-generic.  VLC has always been my preferred video player, and has always worked flawlessly.  The problem began sometime after May 18th, and extends to other viedo formats (.mkv, .mp4, etc)  All files still play in mplayer, so it doesn't strike me as a problem with video drivers or codecs.

---

### Post by abhilash82 on 2009-06-01
> **canadastitan said:**
> this is what i get in terminal
dale@Titan:~$ vlc
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
dale@Titan:~$ 
and the vlc player will start but as soon as it opens the selected .avi file it crashes and closes also

I also have the same problem;

```
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82
```

Is there any solution to this problem?

---

### Post by glx51mm on 2009-06-03
Same problem here. Installation is 9.04 and i think the problem appeared after installing winFF and having the latest recommended updates (i don't remember seeing anything relevant in the updates though). Tried uninstalling winFF but problem persists. Also tried reinstalling vlc and codecs (gstreamer) but still no luck...
My other laptop that is up to date running 9.04 has no such problems yet.

---

### Post by glx51mm on 2009-06-03
ok, i think i found what is going wrong. First I must mention that the problem has appeared on an Advent 4211 (msi wind u100 clone) running 9.04 remix (didn't mention that earlier).
What I did was to change the xorg.conf file from this:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2384 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


to this:


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection



and everything works fine again.
Why i did that ? Because earlier I tried to hook up an external display and at some point I accepted a message saying to write some new info to the display configuration file which was what probably caused all this. Reverting back to the old xorg.conf solved the problem.
I really hope you will find this helpful. Good luck.

---

### Post by billgoldberg on 2009-06-03
Onboard Intel graphics cards aren't properly supported on Ubuntu 9.04.

It's in the release notes of the OS, you should read those before installing.

---

### Post by daphilp on 2009-06-03
Complete newby with same problem. but Utube and streaming video play fine.
very confused,
dave
Ireland

---

### Post by j_dolu on 2009-07-31
> **j_dolu said:**
> I have the same problem. After upgrade from ubuntu 810 to 904, all video player could not play any video file. All suddenly crash on opening any video file. No error found.
I try to do fresh install kubuntu 904 and install all video codecs. Dragon player did not crash on opening video file but it only show blue window. I try install VLC, it still crash on opening video file.

Any suggestion on this?

Lastly I install Linux Mint 7. VLC still crash upon opening video file. 
I change the video output option to "X11 Video Output", and my problem solved.
I think this would solve VLC problem in Ubuntu too, since Linux Mint 7 comes from Ubuntu

Regards
Dolu
[www.get-updates.com]("http://www.get-updates.com")

---

### Post by PGScooter on 2009-07-31
I bet the VLC guys at the VLC forum can figure out what's going on: [http://forum.videolan.org/viewforum.php?f=13&sid=ea9c0fe2bf96a06703cb3d32a03aba56](http://forum.videolan.org/viewforum.php?f=13&sid=ea9c0fe2bf96a06703cb3d32a03aba56)

---

### Post by rifter on 2010-02-27
Changing the video output to X11 video in vlc 

Tools -> Preferences -> Video -> Output -> X11 video output

will fix the badalloc error for most people.

Ubuntu 9.10 Karmic Koala improved support for onboard Intel video chipsets as well.  Good luck.

---

### Post by rifter on 2010-03-02
> **ellgor said:**
> Hi, 

If you are still having problems try this:

Goto>System>Preferences>Multimedia Systems Selector (it may not be enabled in your menu, enable if not)
Choose Video, under default output change this to X Window System (No Xv), it may need a reboot to take effect, hope this helps.

Regards, Ellgor.

That works for Totem Movie Player.  For vlc you want to go in vlc to 

Tools -> Preferences -> Video -> Output -> X11 video output

to fix the same problem.

---

