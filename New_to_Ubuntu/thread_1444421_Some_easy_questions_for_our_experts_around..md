---
title: "Some easy questions for our experts around."
date: 2010-04-01
forum: New to Ubuntu
---

### Post by Rushyang on 2010-04-01
Bonjour guys!

I installed ubuntu 9.10 karmic koala just yesterday. & boy! my days were never been this much better! 

This forum had all the solutions already! I'd no topics to ask for help from some really cool experts around here...  I installed NVIDIA drivers, updated linux kernel, internet usage tools, audio tools, video codecs, learn many keyboard shortcuts too. 

Now, I've some problems which I can't solve.

1) I've Linux Professional Professional Video Tutorial. In which there are videos with .wmv format. 

I can't play them, i just hear sound with mplayer for some. 

P.S.: Please don't suggest to unblock restricted extras, VLC or movie player codecs... None of them are working. 

2) Is there any audio player in which I can assign hot keys for playing my music? (just need a name, I'll search for rest..)

3) Now, I don't want ubuntu to connect PPPOE connection automatically on start up & I also don't want to use pppoeconf into terminal everytime I log in into ubuntu. 

Is there any GUI based Internet PPPOE Dialer like windows, which allow me to dial my PPPOE connection by clicking it? Or script or something? which also should allow me to disconnect internet whenever I want. 

4) Now, I really admire some experts are providing cool stuff around, by suggesting commands and scripts to be input in terminal. I want to know, 
To be an expert, do you need to remember all those commands? Do you remember them all? :-s

---

### Post by Chesamo on 2010-04-01
> **Rushyang said:**
> 1) I've Linux Professional Professional Video Tutorial. In which there are videos with .wmv format. 

I can't play them, i just hear sound with mplayer for some. 

P.S.: Please don't suggest to unblock restricted extras, VLC or movie player codecs... None of them are working.
Well, that's the only solution to your problem. Do the wmv files you are given not use a standard compression or encapsulation method?
> **Rushyang said:**
> 2) Is there any audio player in which I can assign hot keys for playing my music? (just need a name, I'll search for rest..)
Not explicitly, no, but you can assign shortcut keys in System > Preferences > Keyboard Shortcuts. The first category is called "Sound". They shortcuts you are looking for are in there.
> **Rushyang said:**
> 3) Now, I don't want ubuntu to connect PPPOE connection automatically on start up & I also don't want to use pppoeconf into terminal everytime I log in into ubuntu. 

Is there any GUI based Internet PPPOE Dialer like windows, which allow me to dial my PPPOE connection by clicking it? Or script or something? which also should allow me to disconnect internet whenever I want.
You can create Launchers to run programs. Right-click on your top Panel and click "Add to Panel..." Select Launcher. It should be fairly straightforward from there.
> **Rushyang said:**
> 4) Now, I really admire some experts are providing cool stuff around, by suggesting commands and scripts to be input in terminal. I want to know, 
To be an expert, do you need to remember all those commands? Do you remember them all? :-s
Lord no! Google is your friend ;-)

But it is a memorization kind of thing. After looking it up (or writing it down for reference), eventually you'll just remember the commands.

---

### Post by coffeecat on 2010-04-01
> **Rushyang said:**
> 1) I've Linux Professional Professional Video Tutorial. In which there are videos with .wmv format. 

I can't play them, i just hear sound with mplayer for some. 

P.S.: Please don't suggest to unblock restricted extras, VLC or movie player codecs... None of them are working. 

I thought it was the British who were meant to have a sense of irony! Whoever produced a Linux professional video tutorial complete with videos that use a restricted proprietary codec developed by Microsoft no less, and which will not play on a default Ubuntu installation, has out-ironied anything my compatriots can come up with. :-s

Anyway, I think you may need either the w64codecs or w32codecs package (depending on whether you installed the 32- or 64-bit version of Ubuntu). Have a look here:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

You can either activate the medibuntu repository and use Synaptic (or the command line) or download and install the w32/64codecs package directly.

By the way, do you have a link to this tutorial? I am intrigued as to why they are using WMV. And it's "**ubuntu**-restricted-extras" by the way.

---

### Post by Rushyang on 2010-04-01
> **coffeecat said:**
> 
You can either activate the medibuntu repository and use Synaptic (or the command line) or download and install the w32/64codecs package directly.

By the way, do you have a link to this tutorial? I am intrigued as to why they are using WMV. And it's "**ubuntu**-restricted-extras" by the way.

Yes sir! I meant **ubuntu**-restricted-extras. Those are not working.. Now I'll try with those w32 codecs. Thank You.

I hope, I'm not violating any rules by providing you this link to check.. & I hope you'll be able to make it play for me...
> 
[http://rapidshare.com/files/370761367/00_LPI_Series_Intro.wmv](http://rapidshare.com/files/370761367/00_LPI_Series_Intro.wmv) 


---

### Post by coffeecat on 2010-04-01
> **Rushyang said:**
> I hope, I'm not violating any rules by providing you this link to check.. & I hope you'll be able to make it play for me...

I don't think there's any problem with the rules. Anyway I tried this first in 64-bit Jaunty (just because I happened to have Jaunty running). It wouldn't play and mplayer gave a revealing error message: "Cannot find codec for audio format 0xA". If you google that you come up with a list of hits a mile long.

So I tried it in mplayer in 32-bit Jaunty and it played just fine. Well - I think it played just fine, but I was overcome by an overwhelming sense of ennui after only a few seconds and nearly lost the will to live. :wink: But I roused myself to post this reply. I have only a couple of comments.

The fact that the author of a Linux tutorial is using a codec that causes difficulty in Linux suggests to me that you would do better looking elsewhere for tuition. Why it plays in 32-bit Jaunty but not 64-bit, I'm not sure because I go through the same multimedia app installation routine for all my installs. I think it may be something to do with w32codecs and w64codecs. I believe there are some things missing in the 64-bit version.

---

### Post by Rushyang on 2010-04-01
> **coffeecat said:**
> 
So I tried it in mplayer in 32-bit Jaunty and it played just fine. Well - I think it played just fine, but I was overcome by an overwhelming sense of ennui after only a few seconds and nearly lost the will to live. :wink: But I roused myself to post this reply. I have only a couple of comments.


Alright then! I found out that I don't have installed w32codecs installed in my Karmic Koala. and I've added repositories and I'm just waiting for my unlimited internet session to start. So that I can download and install them from following reference link..
> 
[http://www.ubuntugeek.com/install-and-enable-dvd-playback-and-w32codecs-in-ubuntu-system.html](http://www.ubuntugeek.com/install-and-enable-dvd-playback-and-w32codecs-in-ubuntu-system.html)

Thanks a lot for this help so far! I AM REALLY PROUD TO BE PART OF THIS FORUM AND HAVE EXPERTS AROUND LIKE YOU. :D

---

### Post by muteXe on 2010-04-01
Linux tutorials in Windows Media Video format eh?  Interesting...

Google's your best mate probably. And i've always liked [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) as well.

And what do you mean by "None of them are working", when you talk about restricted extras, VLC or movie player codecs?

---

### Post by Rushyang on 2010-04-01
> **muteXe said:**
> Linux tutorials in Windows Media Video format eh?  Interesting...

Google's your best mate probably. And i've always liked [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) as well.

And what do you mean by "None of them are working", when you talk about restricted extras, VLC or movie player codecs?

I talked about those Windows Media Video Tutorials specifically... All other formats are working... VLC is best on ubuntu.


Thanks for that link! :D

---

### Post by sandyd on 2010-04-01
> **Rushyang said:**
> Bonjour guys!

I installed ubuntu 9.10 karmic koala just yesterday. & boy! my days were never been this much better! 

This forum had all the solutions already! I'd no topics to ask for help from some really cool experts around here...  I installed NVIDIA drivers, updated linux kernel, internet usage tools, audio tools, video codecs, learn many keyboard shortcuts too. 

Now, I've some problems which I can't solve.

1) I've Linux Professional Professional Video Tutorial. In which there are videos with .wmv format. 

I can't play them, i just hear sound with mplayer for some. 
[B]```


```[/B]```
[B]sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[/B]
```[B]
Depending on wether your running 64 or 32 bit..

32-bit
```

sudo apt-get install w32codecs

```[/B][B]
64-bit 
```

sudo apt-get install w64codecs
```[/B]
P.S.: Please don't suggest to unblock restricted extras, VLC or movie player codecs... None of them are working. 

2) Is there any audio player in which I can assign hot keys for playing my music? (just need a name, I'll search for rest..)
[code]
[B]Not sure about gnome, but if you right click on the kde icon, and select menueditor, then go to the application in question, you can select a particular key to open the app.
[/B]
3) Now, I don't want ubuntu to connect PPPOE connection automatically on start up & I also don't want to use pppoeconf into terminal everytime I log in into ubuntu. 

Is there any GUI based Internet PPPOE Dialer like windows, which allow me to dial my PPPOE connection by clicking it? Or script or something? which also should allow me to disconnect internet whenever I want. 
**Not sure, I use cable.**

4) Now, I really admire some experts are providing cool stuff around, by suggesting commands and scripts to be input in terminal. I want to know, 
To be an expert, do you need to remember all those commands? Do you remember them all? :-s

**nah. we only know them cause we specialize in helping people.**

eh.
im late to the party today.

---

### Post by andrew.46 on 2010-04-01
Hi Rushyang,

That video is a scary combination of Windows Media Audio 9 Speech and Windows Media Screen Codec 2. It can be played with MPlayer and the so-called w32codecs:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -afm dmo -vfm dmo 00_LPI_Series_Intro.wmv [/COLOR]**
MPlayer SVN-r30980-4.3.3 (C) 2000-2010 MPlayer Team

Playing 00_LPI_Series_Intro.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [MSS2]  640x480  24bpp  1000.000 fps    6.4 kbps ( 0.8 kbyte/s)
Clip info:
 title: CBT Nuggets Training Videos
 author: CBT Nuggets, Inc.
 copyright: 1999-2004, CBT Nuggets, Inc.
 comments: IT Certification Training Videos - www.cbtnuggets.com
==========================================================================
Trying to force video codec driver family dmo...
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: RGB8 RGB555 RGB565 RGB24 RGB32 
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x9003230]BICUBIC scaler, from bgra to yuv420p using MMX2
VO: [xv] 640x480 => 640x480 Planar YV12 
**[COLOR="Red"]Selected video codec: [wmsdmod] vfm: dmo (Windows Media Screen Codec 2)[/COLOR]**
==========================================================================
==========================================================================
Trying to force audio codec driver family dmo...
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 22050 Hz, 1 ch, s16le, 20.0 kbit/5.67% (ratio: 2500->44100)
**[COLOR="Red"]Selected audio codec: [wma9spdmo] afm: dmo (Windows Media Audio 9 Speech DMO)[/COLOR]**
==========================================================================
AO: [oss] 22050Hz 1ch s16le (2 bytes per sample)
Starting playback...
A:  13.4 V:  13.0 A-V:  0.364 ct:  0.100  30/ 30  3%  3%  2.0% 0 0 
Exiting... (Quit)

```

A very odd choice for a linux talk :).

Andrew

---

### Post by chrisinspace on 2010-04-01
> **Rushyang said:**
> 1) I've Linux Professional Professional Video Tutorial. In which there are videos with .wmv format.

Haha...bizarre that your Linux Professional Video Tutorial comes in Windows Media format! :p

Hmmmm...Maybe it was secretly created by a Windows FUD operative to make it look hard to use Linux.

---

### Post by Rushyang on 2010-04-02
Hi All,

I think I messed up with my repository entry (source list) while I was learning around...
```
 sudo gedit /etc/apt/sources.lst 
```Now, when I give ```
 sudo apt-get install w32codecs 
```It gives me error of broken packages.

The same problem comes up in my _Synaptic Package Manager_. Here is my Sources.lst file...


```

#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

```

Please suggest! Find screenshot of Synaptic Packet Manager's Error in the attachment.

---

### Post by 3rdalbum on 2010-04-02
> **Rushyang said:**
> Hi All,

I think I messed up with my repository entry (source list) while I was learning around...
```
 sudo gedit /etc/apt/sources.lst 
```Now, when I give ```
 sudo apt-get install w32codecs 
```It gives me error of broken packages.

The same problem comes up in my _Synaptic Package Manager_. Here is my Sources.lst file...

## Medibuntu - **Ubuntu 7.04 "feisty fawn"**
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) **feisty** free non-free


You've added a repository for Ubuntu 7.04, to your Ubuntu 9.10. That's not going to have a happy ending. Don't follow outdated tutorials!

First, open the sources.list:

```
gksudo gedit /etc/apt/sources.list
```

Remove those lines that I've quoted above (the ones that mention Medibuntu).

Now go to [www.medibuntu.org](www.medibuntu.org) and follow their "Repository Howto". When you've done that, you'll have access to Medibuntu's software, and you can install the "non-free-codecs" package in Synaptic.

---

### Post by anewguy on 2010-04-02
Here's a link to an example of what is really crazy with this thing:

[http://www.computer-training-software.com/ubuntu-certification.htm]("http://www.computer-training-software.com/ubuntu-certification.htm")

Notice the "About this Linux Ubuntu Certification Training CD", yet also notice the "Compatibility:  	Vista, 2000, XP, Windows 7, Mac OS, OSX".

I guess you're supposed to learn all about Ubuntu but never run Ubuntu?  Talk about an oxymoronic approach to things!

Dave ;)

---

### Post by Chronon on 2010-04-02
> **anewguy said:**
> Here's a link to an example of what is really crazy with this thing:

[http://www.computer-training-software.com/ubuntu-certification.htm]("http://www.computer-training-software.com/ubuntu-certification.htm")

Notice the "About this Linux Ubuntu Certification Training CD", yet also notice the "Compatibility:  	Vista, 2000, XP, Windows 7, Mac OS, OSX".

I guess you're supposed to learn all about Ubuntu but never run Ubuntu?  Talk about an oxymoronic approach to things!

Dave ;)
HAHA!  Talk about irony!

---

### Post by Rushyang on 2010-04-02
> **3rdalbum said:**
> You've added a repository for Ubuntu 7.04, to your Ubuntu 9.10. That's not going to have a happy ending. Don't follow outdated tutorials!

Now go to [www.medibuntu.org]("http://www.medibuntu.org") and follow their "Repository Howto". When you've done that, you'll have access to Medibuntu's software, and you can install the "non-free-codecs" package in Synaptic.

Thanks man... that solved my sources.lst problem. But I still can't run that .wmv file.. I just hear voice but don't have video output. 

Right now, I've install Mplayer with w32codecs and Mediubuntu's non-free-codecs too.

> **anewguy said:**
> 
[http://www.computer-training-software.com/ubuntu-certification.htm](http://www.computer-training-software.com/ubuntu-certification.htm)

I guess you're supposed to learn all about Ubuntu but never run Ubuntu?  Talk about an oxymoronic approach to things!

Dave ;)
No, I was talking about different tutorials...But, I also have those tutorial & I just don't know what to do with virtual cd image files yet.. Can you tell me how to open those virtual cd image file with extension **.bin** & **.cue**?? 

Thanks for baring with me guys! \\:D/

---

### Post by anewguy on 2010-04-02
Guess I was thinking of a .bin file, not a .bin image.  So here's a link on doing that:

<link>http://maketecheasier.com/mount-iso-bin-and-cue-files-from-nautilus/2009/05/23</link>

If you need help with that, post back.

Dave :;

---

### Post by andrew.46 on 2010-04-02
Hi Rushyang,

> **Rushyang said:**
> Thanks man... that solved my sources.lst problem. But I still can't run that .wmv file.. I just hear voice but don't have video output. 

Could you run the file in the following manner:
```

mplayer -v 00_LPI_Series_Intro.wmv
```

and post the full terminal output here?

Andrew

---

### Post by Rushyang on 2010-04-02
> **anewguy said:**
> 
<link>http://maketecheasier.com/mount-iso-bin-and-cue-files-from-nautilus/2009/05/23</link>

If you need help with that, post back.

Dave :;

Hey thanks.. I'll try and post the result here soon.. Thanks again!
> **andrew.46 said:**
> Hi Rushyang,

Could you run the file in the following manner:
```

mplayer -v 00_LPI_Series_Intro.wmv
```and post the full terminal output here?

Andrew

Hi Andrew! 
Man, you're like a life savior! I don't know how did you do it.. but that command gave me output in it's player window and video is running successfully! with including video and audio both!

But that player has no controllers! Man, nice going.. I wonder, when I open it from mouse by right clicking on video and open with mplayer.. It didn't work!! But from terminal, it's working!! What's the magic behind this??

---

### Post by andrew.46 on 2010-04-02
Hi Rushyang,

> **Rushyang said:**
> 
Man, you're like a life savior! I don't know how did you do it.. but that command gave me output in it's player window and video is running successfully! with including video and audio both!

But that player has no controllers! Man, nice going.. I wonder, when I open it from mouse by right clicking on video and open with mplayer.. It didn't work!! But from terminal, it's working!! What's the magic behind this??

Well there are quite comprehensive controls but the commandline player runs from the keyboard :). I had a suspicion that you had a problem with the video out device set for the gui MPlayer, and the terminal output would give a few hints about that... I don't suppose you could post that terminal output?

Once you can *see* the successful video out device I would suggest you install a better gui:

```
sudo apt-get install smplayer
```

and then adjust the settings there. Hopefully this will set you on your way :).

Andrew

---

### Post by Rushyang on 2010-04-02
> **anewguy said:**
> Guess I was thinking of a .bin file, not a .bin image.  So here's a link on doing that:

<link>http://maketecheasier.com/mount-iso-bin-and-cue-files-from-nautilus/2009/05/23</link>

If you need help with that, post back.

Dave :;

Hi Dave,
That .bin image is mounted successfully..! Now I can mount every cd image file directly..! Thanks man. :) 

-Rushyang

> **andrew.46 said:**
> Hi Rushyang,
I had a suspicion that you had a problem with the video out device set for the gui MPlayer, and the terminal output would give a few hints about that... I don't suppose you could post that terminal output?

Andrew

Hi Andrew,

Well, here is terminal output ...

```
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 10
CPU: Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz (Family: 6, Model: 23, Stepping: 6)
extended cpuid-level: 8
extended cache-info: 201351232
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/rushyang/.mplayer/codecs.conf'
Reading /home/rushyang/.mplayer/codecs.conf: Can't open '/home/rushyang/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --datadir=/usr/share/mplayer --codecsdir=/usr/lib/codecs --enable-xvmc --enable-vdpau --enable-sdl --enable-ossaudio --enable-lirc --enable-freetype --enable-menu --enable-largefiles --extra-cflags=-I/build/buildd/mplayer-1.0~rc3+svn20090426/debian/include --disable-bitmap-font --disable-ggi --language=all --disable-xmms --disable-arts --disable-aa --disable-mad --disable-musepack --disable-libdv --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --enable-mp3lame --enable-faac-lavc --enable-x264-lavc --enable-mp3lame-lavc --enable-libdirac-lavc --enable-libschroedinger-lavc --target=i586-linux --enable-win32dll --enable-real --enable-xanim --enable-runtime-cpudetection --enable-vdpau --disable-libdvdcss-internal --enable-dvdread --enable-debug --enable-tv-v4l2 --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-fbdev --disable-gui
CommandLine: '-v' '00_LPI Series Intro.wmv'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/rushyang/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/rushyang/.mplayer/input.conf'
Can't open input config file /home/rushyang/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('00_LPI Series Intro.wmv.conf') -> '/home/rushyang/.mplayer/00_LPI Series Intro.wmv.conf'

Playing 00_LPI Series Intro.wmv.
get_path('sub/') -> '/home/rushyang/.mplayer/sub/'
[file] File size is 466518 bytes
STREAM: [file] 00_LPI Series Intro.wmv
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: ASF format
Checking for YUV4MPEG2
ASF file format detected.
stream type: guid_audio_stream
stream concealment: guid_audio_conceal_interleave
type: 64 bytes,  stream: 8 bytes  ID: 1
unk1: 0  unk2: 3E7FAD4
FILEPOS=0x14FD
==> Found audio stream: 1
[asfheader] Audio stream found, -aid 1
======= WAVE Format =======
Format Tag: 10 (0xA)
Channels: 1
Samplerate: 22050
avg byte/sec: 2500
Block align: 1088
bits/sample: 16
cbSize: 46
Unknown extra header dump: [10] [0] [4] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [10] [0] [0] [0] [5] [fa] [9a] [0] [5] [c9] [2d] [48] [80] [5a] [60] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] 
==========================================================================
ASF: audio scrambling: 1 x 1 x 1088
stream type: guid_video_stream
stream concealment: unknown guid 0057fb20-555b-cf11-a8fd00805f5c442b
type: 879 bytes,  stream: 0 bytes  ID: 2
unk1: 0  unk2: 0
FILEPOS=0x1593
==> Found video stream: 2
[asfheader] Video stream found, -vid 2
======= VIDEO Format ======
  biSize 868
  biWidth 640
  biHeight 480
  biPlanes 1
  biBitCount 24
  biCompression 844321613='MSS2'
  biSizeImage 0
Unknown extra header dump: [0] [0] [3] [3c] [0] [0] [0] [2] [0] [0] [0] [1] [0] [0] [2] [80] [0] [0] [1] [e0] [0] [0] [2] [80] [0] [0] [1] [e0] [41] [70] [0] [0] [0] [1] [86] [a0] [0] [0] [0] [0] [40] [a0] [0] [0] [41] [0] [0] [0] [0] [0] [0] [9] [ff] [ff] [ff] [ff] [0] [0] [1] [0] [0] [0] [0] [0] [0] [40] [0] [0] [80] [0] [0] [c0] [0] [0] [ff] [0] [40] [0] [0] [40] [40] [0] [40] [80] [0] [40] [c0] [0] [40] [ff] [0] [80] [0] [0] [80] [40] [0] [80] [80] [0] [80] [c0] [0] [80] [ff] [0] [c0] [0] [0] [c0] [40] [0] [c0] [80] [0] [c0] [c0] [0] [c0] [ff] [0] [ff] [0] [0] [ff] [40] [0] [ff] [80] [0] [ff] [c0] [0] [ff] [ff] [40] [0] [0] [40] [0] [40] [40] [0] [80] [40] [0] [c0] [40] [0] [ff] [40] [40] [0] [40] [40] [40] [40] [40] [80] [40] [40] [c0] [40] [40] [ff] [40] [80] [0] [40] [80] [40] [40] [80] [80] [40] [80] [c0] [40] [80] [ff] [40] [c0] [0] [40] [c0] [40] [40] [c0] [80] [40] [c0] [c0] [40] [c0] [ff] [40] [ff] [0] [40] [ff] [40] [40] [ff] [80] [40] [ff] [c0] [40] [ff] [ff] [80] [0] [0] [80] [0] [40] [80] [0] [80] [80] [0] [c0] [80] [0] [ff] [80] [40] [0] [80] [40] [40] [80] [40] [80] [80] [40] [c0] [80] [40] [ff] [80] [80] [0] [80] [80] [40] [80] [80] [80] [80] [80] [c0] [80] [80] [ff] [80] [c0] [0] [80] [c0] [40] [80] [c0] [80] [80] [c0] [c0] [80] [c0] [ff] [80] [ff] [0] [80] [ff] [40] [80] [ff] [80] [80] [ff] [c0] [80] [ff] [ff] [c0] [0] [0] [c0] [0] [40] [c0] [0] [80] [c0] [0] [c0] [c0] [0] [ff] [c0] [40] [0] [c0] [40] [40] [c0] [40] [80] [c0] [40] [c0] [c0] [40] [ff] [c0] [80] [0] [c0] [80] [40] [c0] [80] [80] [c0] [80] [c0] [c0] [80] [ff] [c0] [c0] [0] [c0] [c0] [40] [c0] [c0] [80] [c0] [c0] [c0] [c0] [c0] [ff] [c0] [ff] [0] [c0] [ff] [40] [c0] [ff] [80] [c0] [ff] [c0] [c0] [ff] [ff] [ff] [0] [0] [ff] [0] [40] [ff] [0] [80] [ff] [0] [c0] [ff] [0] [ff] [ff] [40] [0] [ff] [40] [40] [ff] [40] [80] [ff] [40] [c0] [ff] [40] [ff] [ff] [80] [0] [ff] [80] [40] [ff] [80] [80] [ff] [80] [c0] [ff] [80] [ff] [ff] [c0] [0] [ff] [c0] [40] [ff] [c0] [80] [ff] [c0] [c0] [ff] [c0] [ff] [ff] [ff] [0] [ff] [ff] [40] [ff] [ff] [80] [ff] [ff] [c0] [ff] [ff] [ff] [0] [20] [0] [0] [20] [40] [0] [20] [80] [0] [60] [0] [0] [60] [40] [0] [60] [80] [20] [0] [0] [20] [0] [40] [20] [0] [80] [20] [20] [0] [20] [20] [40] [20] [20] [80] [20] [40] [0] [20] [40] [40] [20] [40] [80] [20] [60] [0] [20] [60] [40] [20] [60] [80] [20] [80] [40] [20] [80] [80] [40] [20] [0] [40] [20] [40] [40] [20] [80] [40] [60] [0] [40] [60] [40] [40] [60] [80] [40] [60] [c0] [40] [a0] [40] [40] [a0] [80] [40] [a0] [c0] [60] [0] [0] [60] [0] [40] [60] [20] [0] [60] [20] [40] [60] [20] [80] [60] [40] [0] [60] [40] [40] [60] [40] [80] [60] [40] [c0] [60] [60] [0] [60] [60] [40] [60] [60] [80] [60] [60] [c0] [60] [80] [0] [60] [80] [40] [60] [80] [80] [60] [80] [c0] [60] [a0] [40] [60] [a0] [80] [60] [a0] [c0] [60] [c0] [80] [60] [c0] [c0] [80] [20] [0] [80] [20] [40] [80] [20] [80] [80] [60] [0] [80] [60] [40] [80] [60] [80] [80] [60] [c0] [80] [a0] [40] [80] [a0] [80] [80] [a0] [c0] [80] [a0] [ff] [80] [e0] [80] [80] [e0] [c0] [80] [e0] [ff] [a0] [40] [40] [a0] [40] [80] [a0] [60] [40] [a0] [60] [80] [a0] [60] [c0] [a0] [80] [40] [a0] [80] [80] [a0] [80] [c0] [a0] [80] [ff] [a0] [a0] [40] [a0] [a0] [80] [a0] [a0] [c0] [a0] [a0] [ff] [a0] [c0] [40] [a0] [c0] [80] [a0] [c0] [c0] [a0] [c0] [ff] [a0] [e0] [80] [a0] [e0] [c0] [a0] [e0] [ff] [a0] [ff] [c0] [a0] [ff] [ff] [c0] [60] [40] [c0] [60] [80] [c0] [60] [c0] [c0] [a0] [40] [c0] [a0] [80] [c0] [a0] [c0] [c0] [a0] [ff] [c0] [e0] [80] [c0] [e0] [c0] [c0] [e0] [ff] [e0] [80] [80] [e0] [80] [c0] [e0] [a0] [80] [e0] [a0] [c0] [e0] [a0] [ff] [e0] [c0] [80] [e0] [c0] [c0] [e0] [c0] [ff] [e0] [e0] [80] [e0] [e0] [c0] [e0] [e0] [ff] [e0] [ff] [80] [e0] [ff] [c0] [e0] [ff] [ff] [ff] [a0] [80] [ff] [a0] [c0] [ff] [a0] [ff] [ff] [e0] [80] [ff] [e0] [c0] [ff] [e0] [ff] [20] [20] [20] [60] [60] [60] [a0] [a0] [a0] [e0] [e0] [e0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] 
===========================
ASF: packets: 318  flags: 2  max_packet_size: 1444  min_packet_size: 1444  max_bitrate: 35074  preroll: 5000

 Title: CBT Nuggets Training Videos
 Author: CBT Nuggets, Inc.
 Copyright: 1999-2004, CBT Nuggets, Inc.
 Comment: IT Certification Training Videos - www.cbtnuggets.com

============ ASF Stream group == START ===
 stream count=[0x2][2]
   stream id=[0x1][1]
   max bitrate=[0x5345][21317]
   stream id=[0x2][2]
   max bitrate=[0x35bd][13757]
============ ASF Stream group == END ===
Found movie at 0x195A - 0x71B12
ASF: 1 audio and 1 video streams found
Auto-selected ASF video ID = 2
ASF: Searching for audio stream (id:-1).
Auto-selected ASF audio ID = 1
VIDEO:  [MSS2]  640x480  24bpp  1000.000 fps    6.4 kbps ( 0.8 kbyte/s)
[V] filefmt:6  fourcc:0x3253534D  size:640x480  fps:1000.000  ftime:=0.0010
Clip info:
 name: CBT Nuggets Training Videos
 author: CBT Nuggets, Inc.
 copyright: 1999-2004, CBT Nuggets, Inc.
 comments: IT Certification Training Videos - www.cbtnuggets.com
get_path('sub/') -> '/home/rushyang/.mplayer/sub/'
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1920x1080 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
[VO_XV] Could not grab port 304.
[VO_XV] Using Xv Adapter #0 (NV17 Video Texture)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2046x2046
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: RGB8 RGB555 RGB565 RGB24 RGB32 
VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
VDec: using BGRA as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO Config (640x480->640x480,flags=0,'MPlayer',0x42475220)
SwScaler: reducing / aligning filtersize 1 -> 4
    Last message repeated 1 times
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0xa183be0]BICUBIC scaler, from rgb32 to yuv420p using MMX2
[swscaler @ 0xa183be0]using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xa183be0]using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xa183be0]using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0xa183be0]640x480 -> 640x480
REQ: flags=0x437  req=0x0  
VO: [xv] 640x480 => 640x480 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 305 for hw scaling
INFO: Win32/DMO video codec init OK.
Selected video codec: [wmsdmod] vfm: dmo (Windows Media Screen Codec 2)
==========================================================================
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
======= WAVE Format =======
Format Tag: 10 (0xA)
Channels: 1
Samplerate: 22050
avg byte/sec: 2500
Block align: 1088
bits/sample: 16
cbSize: 46
Unknown extra header dump: [10] [0] [4] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [10] [0] [0] [0] [5] [fa] [9a] [0] [5] [c9] [2d] [48] [80] [5a] [60] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] 
==========================================================================
======= WAVE Format =======
Format Tag: 1 (0x1)
Channels: 1
Samplerate: 22050
avg byte/sec: 44100
Block align: 2
bits/sample: 16
cbSize: 0
==========================================================================
INFO: Win32/DMO audio codec init OK!
dec_audio: Allocating 8192 bytes for input buffer.
dec_audio: Allocating 65536 + 65536 = 131072 bytes for output buffer.
AUDIO: 22050 Hz, 1 ch, s16le, 20.0 kbit/5.67% (ratio: 2500->44100)
Selected audio codec: [wma9spdmo] afm: dmo (Windows Media Audio 9 Speech DMO)
==========================================================================
Building audio filter chain for 22050Hz/1ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 22050Hz/1ch/s16le
[dummy] Was reinitialized: 22050Hz/1ch/s16le
Trying preferred audio driver 'pulse', options '[none]'
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 22050Hz 1ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 22050Hz/1ch/s16le -> 22050Hz/1ch/s16le...
[dummy] Was reinitialized: 22050Hz/1ch/s16le
[dummy] Was reinitialized: 22050Hz/1ch/s16le
Starting playback...
Increasing filtered audio buffer size from 0 to 12032

avg. framerate: 0 fps             
*** [scale] Allocating mp_image_t, 640x480x32bpp BGR packed, 1228800 bytes
*** [vo] Allocating mp_image_t, 640x480x12bpp YUV planar, 460800 bytes
Unicode font: 5025 glyphs.
Unicode font: 5025 glyphs.
```& I just installed **smplayer** and It's working fine now.. I can use GUI controllers too.. Spectacular! :popcorn: Thanks man.. Thanks BIG time. 

So I also wanted to know that, what if I've opened some path into terminal and I directly want to open that path into GUI based file browser? 

E.g: Like in windows "cmd" that command is **start.**

-Rushyang

---

### Post by anewguy on 2010-04-02
You're welcome!

Dave ;)

---

### Post by andrew.46 on 2010-04-02
Hi Rushyang,

> **Rushyang said:**
> 

So I also wanted to know that, what if I've opened some path into terminal and I directly want to open that path into GUI based file browser? 

E.g: Like in windows "cmd" that command is **start.**



I suspect you may find what you need by pressing Alt+F2.

All the best,

Andrew

---

### Post by Rushyang on 2010-04-03
> **andrew.46 said:**
> Hi Rushyang,

I suspect you may find what you need by pressing Alt+F2.

All the best,

Andrew


Hi Andrew,
Let me rephrase my question..

If I'm working in /home/rushyang/Downloads directory or any other directory which deep inside like..
**/media/Drive/E-Books/Ubuntu\ Tutorials/LPI**

then, is there any command while working in terminal to open that PATH direclty into file browser? 

P.S.: I don't know if there exists one.. but window's operating system has there one command similar.. that's why i'm just wondering. & I also can't find by googling.

Thanks man..

-Rushyang

---

### Post by mc4man on 2010-04-03
I guess you could go
nautilus $pwd
or if spaces in path
nautilus "$pwd"

---

### Post by Rushyang on 2010-04-03
> **mc4man said:**
> I guess you could go
nautilus $pwd
or if spaces in path
nautilus "$pwd"
Hi Mac4man,

Thanks ... that worked..

Is there any log file or something where all my past used commands are being logged... so that I don't have to press up arrow key too many times to find out my yesterday's used command?

-Rushyang

---

### Post by durand on 2010-04-03
About the music shortcut stuff, you may want to look into MPD. It's basically a daemon that's always running and there are loads of frontends to control it. My favourite is Sonata, but I also use mpc, which is a very simple commandline program for it. Anyway, you can use that to automatically add songs, play music, etc with simple commands attached to keyboard shortcuts. To add shortcuts, press Alt+F2, type in gconf-editor, press enter. Then navigate to apps/metacity and change the keys in global_keybindings and keybinding_commands

---

### Post by andrew.46 on 2010-04-03
Hi Rushyang,

> **Rushyang said:**
> Is there any log file or something where all my past used commands are being logged... so that I don't have to press up arrow key too many times to find out my yesterday's used command?

I suspect you are looking for $HOME/.bash_history.

Andrew

---

### Post by JKyleOKC on 2010-04-03
> **Rushyang said:**
> Is there any log file or something where all my past used commands are being logged... so that I don't have to press up arrow key too many times to find out my yesterday's used command?
Look for ".bash_history" in your home directory. You may have to hit control-h to make the hidden files show up, or you can view it in a terminal by using "less .bash_history" so that you see a page at a time.

You can also edit this file, since you're its owner, to delete all the false starts and typos that have gone into it (at least they do for me, so I trim the file back to essentials around once a day)...

---

### Post by mc4man on 2010-04-03
> ...so that I don't have to press up arrow key too many times

Because I never got the deal (or if I did then don't like), with 'tab complete', I take a different tack to retrieve specific commands from bash history.

First you'd probably want to enable  show hidden files in nautilus - 
in terminal go.. (several other ways to open - it's a useful place to ck. out
```
nautilus-file-management-properties
```

Then open your your home folder and create a text document named 
```
.inputrc
```
paste this inside
```
"\e[5~": history-search-backward
"\e[6~": history-search-forward
```

Then just start a command in a terminal and use the page up or page down keys to retrieve commands with what you've started in the terminal, right arrow to move the cursor to the end of the chosen one.

---

### Post by durand on 2010-04-03
In the terminal, if you press Ctrl R, you can search through previous commands based on what you type. Also, an easy way to show hidden files in nautilus would be to just press Ctrl + H.

---

