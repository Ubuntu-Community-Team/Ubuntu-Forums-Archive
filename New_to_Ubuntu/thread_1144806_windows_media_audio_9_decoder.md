---
title: "windows media audio 9 decoder"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by rmf8066 on 2009-05-01
I have downloaded some small clips to my computer, but some of them will not play with any sound. Before the video starts, it asks me if i want to 

"search for a suitable plug in. The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported."

so i click on search, and it tells me that "there are no packages with the requested packages found. Windows Media Audio 9 decoder."

so, i was wondering what i needed to do to fix this problem, i typed in windows media audio 9 decoder in google, and the sites gave me it for a windows operating system, not ubuntu. 

any ideas?

---

### Post by SunnyRabbiera on 2009-05-01
you may want to try the win32 codecs, just remember some formats work better then others especially if they are microsoft formats...

---

### Post by andrew.46 on 2009-05-01
Hi,

MPlayer with the Medibuntu codecs should be able to play these files:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -ac help | grep 'Windows Media Audio 9'[/COLOR]**
wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll]
wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax]

```

But as SunnyRabbiera pointed out Microsoft codecs can be a little difficult :-).

Andrew

---

### Post by chitowner2 on 2009-09-19
[QUOTE=andrew.46;7194628]Hi,

MPlayer with the Medibuntu codecs should be able to play these files:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -ac help | grep 'Windows Media Audio 9'[/COLOR]**
wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll]
wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax]

```

But as SunnyRabbiera pointed out Microsoft codecs can be a little difficult :-).




Tried this, but resulting mplayer install still can not play wmv or wma files. 
OS is jaunty/kde4.2

anybody know a "foolproof" codec installation? I've got medibuntu and non-free installed. Still have some files that won't play at all, some play video but no audio- even with VLC!

:confused:

---

### Post by andrew.46 on 2009-09-19
Hi chitowner,

> **chitowner2 said:**
> Tried this, but resulting mplayer install still can not play wmv or wma files. 

Could you run one of these files from the commandline as follows:

```
mplayer ***[COLOR="Red"]myfile.wmv[/COLOR]***
```

and post the command and full terminal output here?

Andrew

---

### Post by mc4man on 2009-09-19
@ chitowner2
if you're running an amd_64 install it's probably a good time to mention.

 If so, maybe follow Andrew's guide for a newer mplayer version or ck. out the smplayer repo for a mplayer build. ( any mplayer build with a ffmpeg => r19754

That would resolve wma3 and wmv3 w/wma3 audio (wma pro 9 and 10

wmal is not currently possible in any 64 bit player (though it isn't that difficult to build and install a 32bit mplayer in 64 bit install

No repo or ppa vlc is good for any wma other than wma2 (though like in mplayer all wma is possible in 32 bit vlc and all wma3 in a modified 64 bit vlc

---

### Post by chitowner2 on 2009-09-19
> **andrew.46 said:**
> Hi chitowner,



Could you run one of these files from the commandline as follows:

```
mplayer ***[COLOR="Red"]myfile.wmv[/COLOR]***
```

and post the command and full terminal output here?

Andrew


MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 7750 Dual-Core Processor (Family: 16, Model: 2, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing myfile.mv.
File not found: 'myfile.mv'
Failed to open myfile.mv.


Exiting... (End of file)


And?  What will this tell us?

---

### Post by MrWES on 2009-09-19
Pretty sure Andrew meant for you to subsitute your particular wmv file name. He was just showing you an example.

~Bill

---

### Post by chitowner2 on 2009-09-19
> **mc4man said:**
> @ chitowner2
if you're running an amd_64 install it's probably a good time to mention.

 If so, maybe follow Andrew's guide for a newer mplayer version or ck. out the smplayer repo for a mplayer build. ( any mplayer build with a ffmpeg => r19754

That would resolve wma3 and wmv3 w/wma3 audio (wma pro 9 and 10

wmal is not currently possible in any 64 bit player (though it isn't that difficult to build and install a 32bit mplayer in 64 bit install

No repo or ppa vlc is good for any wma other than wma2 (though like in mplayer all wma is possible in 32 bit vlc and all wma3 in a modified 64 bit vlc

Pardon my ignorance, but i don't understand your reference to Andrew's build? Yes I am running amd_64 ver of jaunty.

---

### Post by chitowner2 on 2009-09-19
> **andrew.46 said:**
> Hi chitowner,



Could you run one of these files from the commandline as follows:

```
mplayer ***[COLOR="Red"]myfile.wmv[/COLOR]***
```

and post the command and full terminal output here?

Andrew



LOL! I am *such* a noob!

:~/Documents$ mplayer /home/ltm/Movies/ExcedrineRT-1.wmvMPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 7750 Dual-Core Processor (Family: 16, Model: 2, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/ltm/Movies/ExcedrineRT-1.wmv.
File not found: '/home/ltm/Movies/ExcedrineRT-1.wmv'
Failed to open /home/ltm/Movies/ExcedrineRT-1.wmv.


Exiting... (End of file)

---

### Post by andrew.46 on 2009-09-19
Hi chitowner,

> **chitowner2 said:**
> LOL! I am *such* a noob!

No it is my fault for as usual being less that clear, my apologies.

```
CPU: AMD Athlon(tm) 7750 Dual-Core Processor (Family: 16, Model: 2, Stepping: 3)
```

It looks a little as if you migght be running a 64bit system?

```

File not found: '/home/ltm/Movies/ExcedrineRT-1.wmv'
Failed to open /home/ltm/Movies/ExcedrineRT-1.wmv.
```

Oops another misfire :). It might be easiest if you drag the file onto your Desktop and then the syntax should be:

```
mplayer $HOME/Desktop/ExcedrineRT-1.wmv
```

If you type the first couple of letters of the actual filename (ExcedrineRT-1.wmv) and press the Tab key the full name will be filled in for you. The terminal output will show exactly what build of MPlayer you are using, what sort of file you are attempting to play and what sort of codecs MPlayer attempts to use to play it.

All the best,

Andrew

---

### Post by mc4man on 2009-09-19
> Pardon my ignorance, but i don't understand your reference to Andrew's build? Yes I am running amd_64 ver of jaunty.

[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

Or for a ppa build that should work well

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

and the companion smplayer ppa
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)


( if deciding to use a ppa and unclear on how to just ask first

---

### Post by chitowner2 on 2009-09-19
OK Andrew;

I paid more attention this time. Here is what I get from mplayer:

home$ mplayer /home/video/MOVIES/ExcedrineRT-1.wmv
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 7750 Dual-Core Processor (Family: 16, Model: 2, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/video/MOVIES/ExcedrineRT-1.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps  250.0 kbps (30.5 kbyte/s)
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
xscreensaver_disable: Could not find XScreenSaver window.
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Requested audio codec family [wma9dmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wmadmo] (afm=dmo) not available.
Enable it at compilation.
Cannot find codec for audio format 0x162.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video


Exiting... (End of file)

and
:/home$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present

So hopefully that tells you something you can interpret for me. I think 'asf" is another one of those "container"formats. in this instance I get video but no audio from mplayer, vlc and movie player. kaffeine can't open it at al.

CT

---

### Post by chitowner2 on 2009-09-19
> **mc4man said:**
> [http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

Or for a ppa build that should work well

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

and the companion smplayer ppa
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)


( if deciding to use a ppa and unclear on how to just ask first

&&&###&&&###
Thanks mc4man; I followed the links to the 'easier' version and used the method there. Now to reboot...

:-/

---

### Post by andrew.46 on 2009-09-20
Hi chitowner,

Two separate problems by the look of it. The first is video: 

```

[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.
```

There is a problem with running the xv video output on your system The bandaid solution for this is to do as MPlayer suggests and run:

```
mplayer -vo x11 /home/video/MOVIES/ExcedrineRT-1.wmv
```

and the second is audio:

```
Requested audio codec family [wma9dmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wmadmo] (afm=dmo) not available.
Enable it at compilation.
Cannot find codec for audio format 0x162.
```

Looks like the audio is [wmapro]("http://wiki.multimedia.cx/index.php?title=Windows_Media_Audio_Pro") and on a 32bit MPlayer of the vintage seen in the Ubuntu repository the external codec wma9dmo would be used but this cannot be used with the 64bit MPlayer.

However if you follow the links that mc4man has provided you will end up with a copy of MPlayer that features native playback of wmapro and in all likelihood also enable the xv video output.

All the best with this,

Andrew

---

### Post by chitowner2 on 2009-09-20
Andrew, thanks for the help, but this particular file does not seem to 'like' mplayer. 

trying 

Code:
mplayer -vo x11 /home/video/MOVIES/ExcedrineRT-1.wmv

as you suggest gives no help:

$ sudo mplayer -vo x11 /home/video/MOVIES/ExcedrineRT-1.wmv
[sudo] password for ltm: 
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 7750 Dual-Core Processor (Family: 16, Model: 2, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/video/MOVIES/ExcedrineRT-1.wmv.
File not found: '/home/video/MOVIES/ExcedrineRT-1.wmv'
Failed to open /home/video/MOVIES/ExcedrineRT-1.wmv.

Exiting... (End of file)

This looks like the same output I got when the path was wrong but the path is correct; it's the same as I used to get the output that you responded to. I also ran vxinfo:
/home$ xvinfo
X-Video Extension version 2.2
screen #0
no adaptors present

"No adapters present" seems to be telling me that despite following the instructions posted here [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

there were no codecs installed which mplayer can use. This output from vxinfo is identical to what I got before running he instructions from ubuntu-freak's how-to.

Any other ideas?
I know the file is not corrupt; it plays fine on my other jaunty PC (with kde3.5) using VLC, although mplayer gves no audio there either.. I am tempted to just search for codecs on that box and copy them over to the new one, but that would not be "installing" them so it probably won't work.

I am not focused on mplayer in particular, getting any multimedia player to handle this file properly is what I'm after. (The reason I chose this file to work on is b/c is seems to be so difficult to get to play properly.)

CT

---

### Post by andrew.46 on 2009-09-20
Hi chitowner,

> **chitowner2 said:**
> I am not focused on mplayer in particular, getting any multimedia player to handle this file properly is what I'm after. (The reason I chose this file to work on is b/c is seems to be so difficult to get to play properly.)

I will admit to being a little intrigued by the name of this clip so I have tracked it down believe it or not and had a good laugh at the tablets aimed at 'racial tension headaches' :). This file as I suspected has wmapro:

```
Input #0, asf, from 'ExcedrineRT-1.wmv':
Duration: 00:01:02.29, start: 20.000000, bitrate: 561 kb/s
**[COLOR="Red"]Stream #0.0: Audio: wmapro, 48000 Hz, 2 channels, s16, 281 kb/s[/COLOR]**
Stream #0.1: Video: wmv3, yuv420p, 320x240, 250 kb/s
```

and I attach a screenshot of this playing with the 32bit svn MPlayer and the newly released ffwmapro. To play this on a 64bit system you will need to run a *current* version of MPlayer which is to say a recent compilation of the subversion MPlayer. Have you had any luck with the links mc4man has given you?

BTW thanks for the great laugh at the medication for 'racial tension headaches' :).

Andrew

---

### Post by MrWES on 2009-09-20
Andrew,

did you transcode that via ffmpeg? and then feed it to mplayer?

---

### Post by andrew.46 on 2009-09-20
Hi MrWES,

> **MrWES said:**
> did you transcode that via ffmpeg? and then feed it to mplayer?

No, MPlayer played the file directly, I simply used FFmpeg to identify the file as the output from FFmpeg is a little easier to understand :). The file I downloaded is here if you want to have a look at it:

```
wget http://www.andrews-corner.org/samples/ExcedrineRT-1.wmv
```

You can force libavcodec playback from the commandline with:

```
mplayer -afm ffmpeg -vfm ffmpeg ExcedrineRT-1.wmv
```

although there must be a single command to force both audio and video...

Andrew

---

### Post by mc4man on 2009-09-20
@ chitowner2

Sorry, I should have been more verbose, have been distracted by setting up karmic on my once great, now old p4 desktop. (karmic blows away any previous ubuntu release multimedia wise

You need to get a better mplayer, this doesn't look like a rvm ppa version
> 
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team


not sure what you meant here, am guessing that at best you installed smplayer ...?

> I followed the links to the 'easier' version and used the method there. Now to reboot...


If so, to clarify, smplayer is just a front-end to the installed mplayer on your machine, so nothing is gained if you don't install a more current **mplayer**. ( i believe all the mplayers on rvm's "mplayer" ppa are now r29643

So to word a bit differently

Add this ppa to your sources and then either from synaptic or the update manager update your current mplayer install

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Again, if you're unclear at all on how to add a ppa, just ask, help would certainly be forthcoming

---

### Post by gigaferz on 2009-09-20
i might look stupid but have you tried VLC (videolan) ?

---

### Post by humphreybc on 2009-09-20
Just my 2c.

Recently I found that Rhythmbox was crashing upon trying to play .wma files, even though I had w64codecs installed through the Medibuntu repository, and all the available gstreamer plugins.

I changed to Banshee yesterday after a recommendation and it's great... it's a very similar layout to Rhythmbox, but with a lot more features, greater stability and is a lot faster when searching through a large media library. Only thing that it's not very good at at the moment is playing videos, but that's not worrying me as I use VLC to play movies/TV shows. They appear to be working hard on better video support.

It's available in the repos.

---

### Post by chitowner2 on 2009-09-21
Andrew-
Glad you enjoyed the clip; now you have an idea why I feel so frustrated trying to get it to play on my own system.

I tried that ffmpg thing here- didn't work. Must be due to the ver of mplayer I have installed?  I have never "compiled" anything and no clue as to how to do so. I was hoping the png you posted would provide a helpful clue, but alas, I am too much a noob to grok what help it might be.


mc4man-
I do not know what a ppa is or how to use it. Yes, additional direction would be gratefully received. I did look at the launchpad page and saw there is something there about mplayer for jaunty, but was stymied by not knowing what to do with it.

I know I need a public-key to use launchpad, but I didn't get that right either.  :-(

FYI, here is a paste of my sources.list:

# 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty universe
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty-updates universe
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty-updates universe
## Major bug fix updates produced after the final release of the distribution.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty main restricted
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe multiverse

## Medibuntu.
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty-security main restricted
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty-security main restricted
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty-security universe
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty-security universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty-security multiverse
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) jaunty-security multiverse


CT

---

### Post by andrew.46 on 2009-09-21
Hi chitowner2,

Don't worry about compiling at this time, it should be a relatively simple matter to add RVM's PPAs and this will give you a version of MPlayer that will play this and other 'difficult' files quite easily. To add the required PPAs simply hold down Alt and press F2, and in this dialogue box type:

```
gksudo gedit /etc/apt/sources.list
```

or substitute gedit for whatever editor you prefer and then add the following lines which enable RVM's PPAs:

```
deb http://ppa.launchpad.net/rvm/mplayer/ubuntu jaunty main 
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main 
```

Now save the file and close it. To install the OpenPGP keys for these PPAs run the following 2 commands:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 03E02400
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com E4A4F4F4
```

Now run the following:

```
sudo apt-get update && sudo apt-get upgrade
```

If you don't have SMPlayer installed yet, or if you have rid yourself of MPlayer in frustration you will need to run:

```
sudo apt-get install mplayer smplayer
```

Then you will be able to play this troublesome file with SMPlayer as I demonstrate with yet another gratuitous screenshot :).

Andrew

---

### Post by MrWES on 2009-09-21
Very nice -- thanks Andrew. BTW, I finally found a good script to convert mkv to mp4. I also got mkv2vob to run in Wine. Both make very good quality files from the mkv container for playing on my PS3.

Bill

---

### Post by andrew.46 on 2009-09-21
Hi Bill,

> **MrWES said:**
> Very nice -- thanks Andrew. BTW, I finally found a good script to convert mkv to mp4. I also got mkv2vob to run in Wine. Both make very good quality files from the mkv container for playing on my PS3.

Great news :)

Andrew

---

### Post by chitowner2 on 2009-09-21
Andrew-

problem w/ keyserver:

gpg: requesting key 03E02400 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

now what? is there an alternate server?
BTW, I did install smplayer previously. Hope that won't be an issue

CT
:confused:

P.S.: guess server was just busy. worked after several tries.

---

### Post by chitowner2 on 2009-09-22
> **andrew.46 said:**
> Hi chitowner2,

Don't worry about compiling at this time, it should be a relatively simple matter to add RVM's PPAs and this will give you a version of MPlayer that will play this and other 'difficult' files quite easily. To add the required PPAs simply hold down Alt and press F2, and in this dialogue box type:

```
gksudo gedit /etc/apt/sources.list
```

or substitute gedit for whatever editor you prefer and then add the following lines which enable RVM's PPAs:

```
deb http://ppa.launchpad.net/rvm/mplayer/ubuntu jaunty main 
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main 
```

Now save the file and close it. To install the OpenPGP keys for these PPAs run the following 2 commands:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 03E02400
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com E4A4F4F4
```

Now run the following:

```
sudo apt-get update && sudo apt-get upgrade
```

If you don't have SMPlayer installed yet, or if you have rid yourself of MPlayer in frustration you will need to run:

```
sudo apt-get install mplayer smplayer
```

Then you will be able to play this troublesome file with SMPlayer as I demonstrate with yet another gratuitous screenshot :).

Andrew


Andrew-

I appreciate all the help, but I am wondering if something is boned on my system. I followed your instructions; it took several tries with the server to get the keys downloaded, but eventually everything got don. I got no err messages until I tried to play that wma file again. 

Here is a synopsis:

kaffeine		fails to run
enque in smplayer	video stalls, no audio
smplayer		video stalls, no audio
mplayer		        video stalls, no audio
dragon player		video only; no audio
movie player		video only; no audio
vlc		        video only; no audio

As you can see, I've pretty much tried everything. Color me frustrated!

CT

---

### Post by MrWES on 2009-09-22
wow! over 4,200 views on this thread. Must be a hot topic aye?

~Bill

---

### Post by andrew.46 on 2009-09-22
Hi chitowner,

> **chitowner2 said:**
> I appreciate all the help, but I am wondering if something is boned on my system. I followed your instructions; it took several tries with the server to get the keys downloaded, but eventually everything got don. I got no err messages until I tried to play that wma file again. 

Hmmm.... sounds a little odd, I appreciate your frustration but I can assure you that an appropriately configured MPlayer *will* play this file. Can I suggest you download the version of this file that I have parked on my site, just in case your own version is corrupt? To save flicking back through this thread I give the details again:

```
cd Desktop
wget http://www.andrews-corner.org/samples/ExcedrineRT-1.wmv
mplayer ExcedrineRT-1.wmv
```

and post the terminal output in full here. Hopefully this will provide an answer :).

Andrew

---

### Post by andrew.46 on 2009-09-22
Hi Bill,

> **MrWES said:**
> wow! over 4,200 views on this thread. Must be a hot topic aye?

There must be a *huge* number of lurkers :).

Andrew

---

### Post by MrWES on 2009-09-22
> **andrew.46 said:**
> Hi chitowner,



Hmmm.... sounds a little odd, I appreciate your frustration but I can assure you that an appropriately configured MPlayer *will* play this file. Can I suggest you download the version of this file that I have parked on my site, just in case your own version is corrupt? To save flicking back through this thread I give the details again:

```
cd Desktop
wget http://www.andrews-corner.org/samples/ExcedrineRT-1.wmv
mplayer ExcedrineRT-1.wmv
```

and post the terminal output in full here. Hopefully this will provide an answer :).

Andrew

Here's what I got with that Andrew:
```
bill@bill-laptop:~/Desktop$ mplayer ExcedrineRT-1.wmv
MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing ExcedrineRT-1.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps  250.0 kbps (30.5 kbyte/s)
Clip info:
 title: 
 author: 
 copyright: 
 comments: 
==========================================================================
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmv9dmod.dll, /usr/lib/win32/wmv9dmod.dll, /usr/local/lib/win32/wmv9dmod.dll
IMediaObject ERROR: 0x89c24cd  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmv9dmod.dll.
You need to upgrade/install the binary codecs package.
Go to http://www.mplayerhq.hu/dload.html
VDecoder init failed :(
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmvdmod.dll, /usr/lib/win32/wmvdmod.dll, /usr/local/lib/win32/wmvdmod.dll
IMediaObject ERROR: 0x89c24cd  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmvdmod.dll.
You need to upgrade/install the binary codecs package.
Go to http://www.mplayerhq.hu/dload.html
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 281.8 kbit/9.17% (ratio: 35219->384000)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x240 => 320x240 Planar YV12 

```

Bill

---

### Post by andrew.46 on 2009-09-22
Hi Bill,

> **MrWES said:**
> Here's what I got with that Andrew:

```

bill@bill-laptop:~/Desktop$ mplayer ExcedrineRT-1.wmv
MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
[...]
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))

```


Indeed that is what *should* be happening :-). As long as the video plays as well... Actually I did not realise that RVM tagged his builds like that, an excellent idea!

Andrew

---

### Post by MrWES on 2009-09-22
Yep, video definitely played.

P.S. The more I read on ffmpeg, the more I realize the true power of this command line app -- especially the unrestricted, compiled version:)

---

### Post by chitowner2 on 2009-09-22
OK Andrew-

I did that; here]'s the output from Konsole:

:/home$ mplayer /home/Desktop/ExcedrineRT-1.wmv
MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/ltm/Desktop/ExcedrineRT-1.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps  250.0 kbps (30.5 kbyte/s)
Clip info:
 title: 
 author: 
 copyright: 
 comments: 
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
[vdpau] Could not open dynamic library libvdpau.so.1
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 281.8 kbit/9.17% (ratio: 35219->384000)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
[AO_ALSA] alsa-lib: pcm_pulse.c:626:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

[AO_ALSA] Unable to set hw-parameters: Input/output error
[AO ESD] latency: [server: 0.19s, net: 0.00s] (adjust 0.19s)
AO: [esd] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...


MPlayer interrupted by signal 13 in module: play_audio
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and won't help unless you provide this information when reporting a possible bug.

***&&&***
"Player crashed. This shouldn't happen." LOL! I know that!

ok Andrew, now what? I hope something in that output is useful! 

CT

---

### Post by mc4man on 2009-09-22
See what happens if you go 

```
mplayer -ao pulse -vo x11 /home/Desktop/ExcedrineRT-1.wmv
```

by default your mplayer build will use oss, so this seems to be an issue that may or may not need to be addressed
> [AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy

The wildcard here is you appear to be using kubuntu , my limited experiences with kubuntu proved to be perplexing at times

---

### Post by chitowner2 on 2009-09-22
> **mc4man said:**
> See what happens if you go 

```
mplayer -ao pulse -vo x11 /home/Desktop/ExcedrineRT-1.wmv
```

by default your mplayer build will use oss, so this seems to be an issue that may or may not need to be addressed


The wildcard here is you appear to be using kubuntu , my limited experiences with kubuntu proved to be perplexing at times


Andrew- 
I am using a jaunty/gnome install with kde 4.2 added, since I prefer the kde desktop. If it makes any difference, I could open a session with gnome.

Once again following your instructon, now I get video, but no audio. Here is the 'paste':

:~/Documents$ mplayer -ao pulse -vo x11 /home/Desktop/ExcedrineRT-1.wmv
MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/Desktop/ExcedrineRT-1.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps  250.0 kbps (30.5 kbyte/s)
Clip info:
 title: 
 author: 
 copyright: 
 comments: 
==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 281.8 kbit/9.17% (ratio: 35219->384000)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] Init failed: Invalid argument
Failed to initialize audio driver 'pulse'
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [x11] 320x240 => 320x240 Planar YV12 
[swscaler @ 0xe75d20]using unscaled yuv420p -> rgb32 special converter
V:  59.8 1195/1195  2%  3%  0.0% 0 0 
Exiting... (Quit)

FYI:
Reading state information... Done
pulseaudio is already the newest version.


SO- looks like something is wrong with pulseaudio?

CT

Are either of these links relevant?
[https://lists.ubuntu.com/archives/kubuntu-bugs/2009-May/075766.html](https://lists.ubuntu.com/archives/kubuntu-bugs/2009-May/075766.html)
[http://www.linuxquestions.org/questions/linux-software-2/cant-open-audio-device.-device-or-resource-busy.-649589/](http://www.linuxquestions.org/questions/linux-software-2/cant-open-audio-device.-device-or-resource-busy.-649589/)

CT

---

### Post by chitowner2 on 2009-09-23
IT WAS AMAROK!

I had amarok running all this time (paused) but it still blocked ALL other audio output.

Once I saw that link about a bug in amarok and turned it off, I got sound from other apps. Since it is a known bug, nothing we can do about it, I guess.

SYNOPSIS
That ExcedrineRT file only gives me audio when I use the command suggested by Andrew, so there may still be a glitch somewhere with pulseaudio. I did not find any way to configure mplayer to use alsa as default audio. That would be useful.

So at this point I am able to get vid and audio from avi, asf, flv, mpg and wmv files; that pretty much covers it. 

Here s terminal output from the succesful play of ExecdrineRT.wmv;

:/home$ mplayer -ao pulse -vo x11 /home/lDesktop/ExcedrineRT-1.wmv
MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/Desktop/ExcedrineRT-1.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps  250.0 kbps (30.5 kbyte/s)
Clip info:
 title: 
 author: 
 copyright: 
 comments: 
==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 281.8 kbit/9.17% (ratio: 35219->384000)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [x11] 320x240 => 320x240 Planar YV12 
[swscaler @ 0xe75d20]using unscaled yuv420p -> rgb32 special converter
[wmapro @ 0xd8fae0]not enough space for the output samples  0.6% 0 0 
A:  82.3 V:  82.2 A-V:  0.056 ct:  0.167 1866/1866  2%  4%  0.6% 0 0 

Exiting... (End of file)

Special thanks to Andrew for his diligent assistance and thanks to the others who shared ideas.

CT
:guitar:

---

### Post by andrew.46 on 2009-09-23
Hi chitowner2,

Great news :). Sound preferences can be adjusted in SMplayer from Options ---> Peferences, I have attached a screenshot that demonstrates the exact location. For the commandline MPLayer you should have the file $HOME/.mplayer/config although I do not run RVM's build and perhaps he has changed this. In this file simply place:

```
ao = alsa
```

and this will give you alsa each time. If the file already exists just make sure that the ao setting does not already exist.

All the very best,

Andrew

---

### Post by chitowner2 on 2009-09-23
Andrew-
Thanks for the tip about editing the audio config. I checked those settings and added"ao = alsa" to the mplayer file. Now I hope I'm DONE with this detour!

CT
:)

---

### Post by swarsron on 2009-12-18
I added the lines to my sources.list and smplayer updated fine. mplayer and mencoder won't install anymore because of a missing dependency:

# sudo apt-get install mencoder mplayer                    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mencoder: Depends: libx264-65 (>= 1:0.svn20081230) but it is not installable
  mplayer: Depends: libx264-65 (>= 1:0.svn20081230) but it is not installable
E: Broken packages

Any idea?

Thanks

---

### Post by rvm4000 on 2009-12-18
> **swarsron said:**
> I added the lines to my sources.list and smplayer updated fine. 

What lines did you add?

> **swarsron said:**
> 
mplayer and mencoder won't install anymore because of a missing dependency:

# sudo apt-get install mencoder mplayer                    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mencoder: Depends: libx264-65 (>= 1:0.svn20081230) but it is not installable
  mplayer: Depends: libx264-65 (>= 1:0.svn20081230) but it is not installable
E: Broken packages

Any idea?

Thanks

libx264-65 is available [here](https://launchpad.net/~rvm/+archive/mplayer) but only for intrepid and hardy, because that package was already supposedly in karmic. Now it seems only libx264-67 is available in karmic... I'll try to upload libx264-65 to my PPA tomorrow.

---

### Post by swarsron on 2009-12-19
> **rvm4000 said:**
> What lines did you add?


deb [http://ppa.launchpad.net/rvm/mplayer/ubuntu](http://ppa.launchpad.net/rvm/mplayer/ubuntu) jaunty main 
deb [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) jaunty main

> **rvm4000 said:**
> 
libx264-65 is available [here](https://launchpad.net/~rvm/+archive/mplayer) but only for intrepid and hardy, because that package was already supposedly in karmic. Now it seems only libx264-67 is available in karmic... I'll try to upload libx264-65 to my PPA tomorrow.

Thank you for your work. I'm annoyed by not being able to play
certain files, but not enough to build a 32 bit mplayer myself.
So your work is very appreciated.

---

### Post by rvm4000 on 2009-12-19
libx264-65 for karmic has been uploaded (although I didn't have time to test it)

---

### Post by swarsron on 2009-12-20
now i can install it, but i still get no sound.

```

MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 1
<snip>
stream type: guid_audio_stream
stream concealment: guid_audio_conceal_interleave
type: 64 bytes,  stream: 8 bytes  ID: 1
unk1: 0  unk2: 12868C
FILEPOS=0x13D1
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
Unknown extra header dump: [10] [0] [4] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [10] [0] [0] [0] [5] [f2] [9a] [f] [5] [c9] [2d] [48] [80] [5a] [7b] [60] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] 
==========================================================================
ASF: audio scrambling: 1 x 1 x 1088
stream type: guid_video_stream
stream concealment: unknown guid 0057fb20-555b-cf11-a8fd00805f5c442b
type: 56 bytes,  stream: 0 bytes  ID: 2
unk1: 0  unk2: 0
FILEPOS=0x1467
==> Found video stream: 2
[asfheader] Video stream found, -vid 2
======= VIDEO Format ======
  biSize 45
  biWidth 1408
  biHeight 508
  biPlanes 1
  biBitCount 24
  biCompression 861293911='WMV3'
  biSizeImage 0
Unknown extra header dump: [47] [f1] [8] [1] [0] 
===========================
ASF: packets: 39629  flags: 2  max_packet_size: 1444  min_packet_size: 1444  max_bitrate: 620854  preroll: 5000
============ ASF Stream group == START ===
 stream count=[0x2][2]
   stream id=[0x1][1]
   max bitrate=[0x5345][21317]
   stream id=[0x2][2]
   max bitrate=[0x925f1][599537]
============ ASF Stream group == END ===
Found movie at 0x14F7 - 0x369414B
ASF: 1 audio and 1 video streams found
Auto-selected ASF video ID = 2
Auto-selected ASF audio ID = 1
ASF: Searching for audio stream (id:1).
VIDEO:  [WMV3]  1408x508  24bpp  1000.000 fps  144.0 kbps (17.6 kbyte/s)
[V] filefmt:6  fourcc:0x33564D57  size:1408x508  fps:1000.000  ftime:=0.0010
<snip>
==========================================================================
==========================================================================
Requested audio codec family [wma9spdmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wma9spdshow] (afm=dshow) not available.
Enable it at compilation.
Cannot find codec for audio format 0xA.
Audio: no sound
Freeing 0 unused audio chunks.
Starting playback...

```

I can't really figure out why since mplayer should be able to play those files

```

#mplayer -ac help G dmo                      
wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wmadmo      dmo       working   Windows Media Audio DMO  [wmadmod.dll]
wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll]

```

the .dll files are on my pc
#locate wma9dmod.dll
/usr/lib/win32/wma9dmod.dll

But when i strace the mplayer process it doesn't try to access those files, which seems strange...

---

### Post by rvm4000 on 2009-12-20
What version of ubuntu are you using?

I've just realized that my mplayer package for karmic does depend on libx264-67, not libx264-65.

Audio using the ffwmapro codec does work for me:

```

mplayer  WMVHDsplash.wmv 

MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing WMVHDsplash.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  1280x720  24bpp  1000.000 fps  6500.0 kbps (793.5 kbyte/s)
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
[vdpau] Could not open dynamic library libvdpau.so.1
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
==========================================================================
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmv9dmod.dll, /usr/lib/win32/wmv9dmod.dll, /usr/local/lib/win32/wmv9dmod.dll
IMediaObject ERROR: 0x89c0f4d  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmv9dmod.dll.
You need to upgrade/install the binary codecs package.
Go to http://www.mplayerhq.hu/dload.html
VDecoder init failed :(
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmvdmod.dll, /usr/lib/win32/wmvdmod.dll, /usr/local/lib/win32/wmvdmod.dll
IMediaObject ERROR: 0x89c0f4d  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmvdmod.dll.
You need to upgrade/install the binary codecs package.
Go to http://www.mplayerhq.hu/dload.html
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, floatle, 384.0 kbit/4.17% (ratio: 48000->1152000)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))
==========================================================================
AO: [oss] 48000Hz 6ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [x11] 1280x720 => 1280x720 Planar YV12 

```

---

### Post by swarsron on 2009-12-20
karmic.

I just realized that i have this problem only with two .wmv files. I can play the other files but can't seek in them. So i'll now try to convert them to a sane format. 

Thank you again

---

### Post by anticipator on 2010-06-28
1. Download the latest 'all-codecs-pack' from mplayer hq
[http://www.mplayerhq.hu/MPlayer/releases/codecs/](http://www.mplayerhq.hu/MPlayer/releases/codecs/)

2. Extract the files to a directory[COLOR=red][/COLOR]
tar -xvf all-********.tar.bz2 (replace '*' accordingly from filename :P )
This will extract the files into a directory 'all-********/' in the current location

3. Copy all the extracted files to /usr/local/lib/codecs/ (If there is no such directory, create it)
cp all-********/* /usr/local/lib/codecs/

4. Make sure the files have the required permissions
chmod 755 /usr/local/lib/codecs/*

5. Some players look in a the directory /usr/lib/win32/ for codecs. So if you don't have that directory create it and copy the files there as well.
cp /usr/local/lib/codecs/* /usr/lib/win32/

6. Now your media file should work fine in mplayer or smplayer...  

Good Luck!

---

### Post by lhaeh on 2010-08-16
I'll just go through a rundown of some of the stuff I did when not being able to get audio working:

-Added the mediubuntu and ppa.launchpad.net to sources.list
-Did a chmod 755 /usr/local/lib/codecs/* and for /usr/lib/win32/ after extracting the 'all-codecs-pack'
-Had to do sudo apt-get install mplayer smplayer non-free-codecs w64codecs libdvdcss2 after updating sources.list, might have been a few more then that.

I hope that helps as somewhat of a checklist of things to do if your not sure if you forgot something along the way. There are some things I probably forgot though.

---

### Post by bluetonic on 2010-09-17
@lhaeh & anticipator

It works like a charm. Thx guys

---

### Post by guelo18 on 2012-02-11
Hi. I don´t know if you still having problem with the wma thing but I enter to the ubuntu software center and look for banshee player, so when I opened it it show me some "aditional stuff to add" so one of them says banshee-community-extensions and then it plays wma files. If don't then download an audio converter from the ubuntu software center.

---

