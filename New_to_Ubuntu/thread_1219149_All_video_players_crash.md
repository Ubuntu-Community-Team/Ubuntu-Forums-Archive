---
title: "All video players crash"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by hman469 on 2009-07-21
I just installed Jaunty replacing Hardy that I have been using for a year now and all the video players suddenly disappear when I try to play any format of video.  I can start the players fine but as soon as I point it to a video it just disappears with no error notice or anything.  I have the Medibuntu repositories and codecs installed exactly as I did with hardy (except I used the ones required for Jaunty).  I have installed VLC, Mplayer, and movie player installed by default. All three do the same identical thing.

Any ideas where to begin would be deeply appreciated, thanks!

---

### Post by hyperdude111 on 2009-07-21
This may help.

It is no longer to use the mediabuntu repos and install each library individually.
 
The command 
```
sudo apt-get install ubuntu-restricted-extras
```
can install can install every codec at once working for your system. This is flash, mp4, mp3, divx, java etc. If you need DVD support then also use mediabuntu.

---

### Post by binbash on 2009-07-21
change your video output to X11

---

### Post by hman469 on 2009-07-21
> **hyperdude111 said:**
> This may help.

It is no longer to use the mediabuntu repos and install each library individually.
 
The command 
```
sudo apt-get install ubuntu-restricted-extras
```
can install can install every codec at once working for your system. This is flash, mp4, mp3, divx, java etc. If you need DVD support then also use mediabuntu.

Thanks, but still the same problem though.

---

### Post by hman469 on 2009-07-21
> **binbash said:**
> change your video output to X11

How do I go about doing that?

---

### Post by ~sHyLoCk~ on 2009-07-21
> **hman469 said:**
> How do I go about doing that?
In the video option in the preference section of the player you are using.

---

### Post by hman469 on 2009-07-21
> **~sHyLoCk~ said:**
> In the video option in the preference section of the player you are using.

I cannot find an option or preference to change that on any of the three media players I am using?

---

### Post by issih on 2009-07-21
open a terminal, then start one of the players you are talking about from there (e.g. use the command "vlc" to start that or "totem" to start the Movie Player)

Then do what ever causes the crash, and post the output that appears in the terminal here.

If its something about badalloc, then I've been struggling with it too, and have a few workarounds, but until we know what is actually happening we can't really say any more

Hope that helps

---

### Post by hman469 on 2009-07-21
> **issih said:**
> open a terminal, then start one of the players you are talking about from there (e.g. use the command "vlc" to start that or "totem" to start the Movie Player)

Then do what ever causes the crash, and post the output that appears in the terminal here.

If its something about badalloc, then I've been struggling with it too, and have a few workarounds, but until we know what is actually happening we can't really say any more

Hope that helps



Here you go: 
hman@hman-desktop:~$ vlc
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
hman@hman-desktop:~$

---

### Post by issih on 2009-07-22
Yup, this line here:

X Error of failed request: BadAlloc (insufficient resources for operation)

is a sign that you have the same issues as me, it appears to be related to compiz taking too much of your video ram (I only have a puny 128Mb card).

To check this hit alt+f2 and enter:

```
metacity --replace
```

and see if your video programs work with compiz off (metacity is a gnome's default window manager in case you didn't know)

If that solves it, then try enabling compiz again ("compiz --replace") and then go into the compiz's settings manager and start disabling plugins until you find the culprit..apparently blur is particularly bad (and is liable to be my culprit as I recently turned it on to get blur behind transparent objects - I'm waiting for some video encodes to finish before I mess with it though)

Hope that helps

---

### Post by hman469 on 2009-07-22
> **issih said:**
> Yup, this line here:

X Error of failed request: BadAlloc (insufficient resources for operation)

is a sign that you have the same issues as me, it appears to be related to compiz taking too much of your video ram (I only have a puny 128Mb card).

To check this hit alt+f2 and enter:

```
metacity --replace
```

and see if your video programs work with compiz off (metacity is a gnome's default window manager in case you didn't know)

If that solves it, then try enabling compiz again ("compiz --replace") and then go into the compiz's settings manager and start disabling plugins until you find the culprit..apparently blur is particularly bad (and is liable to be my culprit as I recently turned it on to get blur behind transparent objects - I'm waiting for some video encodes to finish before I mess with it though)

Hope that helps


That didn't change anything for me.  My video is built in but I have at least 1.5 gig of ram in my computer.

---

### Post by issih on 2009-07-22
ram is not the same as video ram...

dedicated video cards tend to have ram built into them, which is specifically for the vram, integrated solutions assign some portion of the main ram to the video chipset, which is usually done in bios.

If your video card is built in, you might benefit from booting into bios (it will tell you how if you watch the boot sequence when you power on your computer - something like "press delete to enter setup" - but it will depend on your motherboard)

In there find the section where you assign ram to the videocard and increase the amount (chances are you will have a limited number of options) I'd go as large as it will let you to begin with to see if it will help at all.

Other than that I'm out of ideas.

Hope that helps

---

### Post by hman469 on 2009-07-22
> **issih said:**
> ram is not the same as video ram...

dedicated video cards tend to have ram built into them, which is specifically for the vram, integrated solutions assign some portion of the main ram to the video chipset, which is usually done in bios.

If your video card is built in, you might benefit from booting into bios (it will tell you how if you watch the boot sequence when you power on your computer - something like "press delete to enter setup" - but it will depend on your motherboard)

In there find the section where you assign ram to the videocard and increase the amount (chances are you will have a limited number of options) I'd go as large as it will let you to begin with to see if it will help at all.

Other than that I'm out of ideas.

Hope that helps


Thanks, but no.  I changed it from 64 to the max which was 256 and still no help.  I guess I will have to go back to hardy if I can't get this fixed.  DARN!

---

### Post by Durden on 2009-07-22
Go into appearance settings and disable desktop effects. Then I would reboot just for kicks to clear out RAM.

---

### Post by hman469 on 2009-07-22
> **Durden said:**
> Go into appearance settings and disable desktop effects. Then I would reboot just for kicks to clear out RAM.

That is already done. Still no change.  Thanks though.

---

### Post by Durden on 2009-07-22
[http://bbs.archlinux.org/viewtopic.php?id=70075](http://bbs.archlinux.org/viewtopic.php?id=70075)

Take a look here. A few posts down someone says they have had success by "removing the 'AccelMethod' entry on my xorg.conf"

There is no real reason why it would work before and not now if compiz is disabled. Other than perhaps a driver issue. I may have missed it before but what video card is this? Intel?

---

### Post by oarion7 on 2009-07-22
> **Durden said:**
> I may have missed it before but what video card is this?

Seconded. Could it be ATI?

---

### Post by hman469 on 2009-07-22
> **Durden said:**
> [http://bbs.archlinux.org/viewtopic.php?id=70075](http://bbs.archlinux.org/viewtopic.php?id=70075)

Take a look here. A few posts down someone says they have had success by "removing the 'AccelMethod' entry on my xorg.conf"

There is no real reason why it would work before and not now if compiz is disabled. Other than perhaps a driver issue. I may have missed it before but what video card is this? Intel?


Intel(R) 82865G Graphics Controller  built in to an Hewlett-Packard HP d530 CMT

It worked fine with Hardy Heron, but since I installed Jaunty I cant get any videos to play.

---

### Post by issih on 2009-07-23
Ah..should have twigged this sooner, jaunty has major issues with intel graphics chipsets...Its a big issue related to new code not playing nicely together.

[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

That site has a fair bit of information about how to get round it, but in many ways, you may be best skipping jaunty and moving onto karmic when its done, by which time things should have improved.

Hope that helps

---

### Post by hman469 on 2009-07-23
> **issih said:**
> Ah..should have twigged this sooner, jaunty has major issues with intel graphics chipsets...Its a big issue related to new code not playing nicely together.

[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

That site has a fair bit of information about how to get round it, but in many ways, you may be best skipping jaunty and moving onto karmic when its done, by which time things should have improved.

Hope that helps

Thanks, but still no go.  Anybody else have any ideas before I re-format and re-install Hardy?

---

### Post by llamabr on 2009-07-23
You've tried turning off compiz?  It's very graphic memory intensive, and causes games and movies to crash.  Don't just turn off the desktop effects, turn the whole thing off.

---

### Post by hman469 on 2009-07-23
> **llamabr said:**
> You've tried turning off compiz?  It's very graphic memory intensive, and causes games and movies to crash.  Don't just turn off the desktop effects, turn the whole thing off.

Isn't that what I did when I turned on Metacity in post #12?

---

### Post by kukibird1 on 2009-07-23
I had the same issue with Jaunty and this video card. 

This worked for me. 

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")


or 

[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

---

